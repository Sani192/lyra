# Storage Strategy

## Maturity Metadata

**Status:** Approved.

**Intended Use:** Authoritative architectural design and specifications for Lyra persistence and archiving systems.

## Purpose

Define the platform's storage requirements, data classifications, schema migration models, object store configurations, and retention workflows to guarantee data durability and privacy compliance.

## Storage Classification

Lyra divides data storage into four main classes based on latency, transactional safety, and sizing requirements:

| Data Class | Storage Engine | Read/Write Pattern | Durability Requirement | Retention Policy |
| --- | --- | --- | --- | --- |
| **Active Session State** | Redis | Low latency key/value lookup | Ephemeral (replicated) | Evicted after 24 hrs inactivity |
| **System Metadata** | PostgreSQL | Transactional RDBMS (SQL) | Highly durable (ACID) | Permanent |
| **Audio Recordings** | S3 Object Store | Write-once, read-rarely | Durable, low-cost | 30 days (default) |
| **Conversation Logs** | S3 Object Store | Write-once, read-often | Durable (Audit compliant) | Permanent / Tenant custom |

```
              +--------------------------+
              |   Conversation Engine    |
              +----+---------+---------+-+
                   |         |         |
      Metadata/SQL |         | Cache   | Audio / Transcripts
                   v         v         v
             +-----+----+  +-+---+  +--+-------+
             | Postgres |  |Redis|  |S3 Object |
             +----------+  +-----+  +----------+
```

### 1. PostgreSQL Schema Management
* **Database selection:** PostgreSQL 15+ is the primary system of record for system topology (Organizations, Projects, Environments, Capabilities, and active Sessions metadata).
* **Migration Strategy:** Database schemas are version-controlled using **Alembic**. Schema alterations must be submitted alongside backend implementation patches. Direct manual schema manipulation in database consoles is strictly forbidden.
* **Connection Routing:** Applications must communicate with PostgreSQL via PgBouncer proxy layers to preserve connection bounds during pod scale-outs.

### 2. Object Storage Partition Prefix Mapping
Raw audio inputs, synthesized turns, and redacted transcripts are persisted to S3-compatible object storage. To maintain partition performance, files are organized as follows:
```
s3://lyra-data/org_uuid/proj_uuid/env/year/month/day/session_uuid/[file_type]_turn_[turn_id].[extension]
```
Example filenames:
* `audio_in_turn_001.wav` (PCM 16kHz, raw voice input).
* `audio_out_turn_001.mp3` (synthesized voice output returned to the client).
* `transcript_turn_001.json` (unredacted in-memory context metadata).
* `transcript_final.json` (redacted conversation log, stored post-session).

### 3. Data Archival & Deletion Workflows
* **Automated Retention:** Cron workers run daily to scan S3 audio prefixes. Audio recordings older than 30 days are automatically deleted unless the organization has explicitly registered a custom retention lease.
* **Soft Deletions:** In metadata tables, deleting an organization or project marks the records as `deleted_at = timezone.now()`. A background cleaner purges these records after 14 days of quarantine.
