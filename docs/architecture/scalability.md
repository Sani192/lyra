# Performance & Scalability Architecture

## Maturity Metadata

**Status:** Approved.

**Intended Use:** Authoritative architectural design and specifications for scaling Lyra runtimes and persistence layers.

## Purpose

Define the performance guidelines, concurrency targets, connection pooling models, and background task offloading policies necessary to scale Lyra to support 10,000 concurrent streaming voice conversations.

## Scalability Principles

To support real-time audio streams, the platform isolates synchronous routing operations from resource-intensive background processing, ensuring horizontal scaling is cost-efficient and bottleneck-free.

```
                  +--------------------------------+
                  | Ingress Websocket / HTTP Load  |
                  +---------------+----------------+
                                  |
                                  v
                  +---------------+----------------+
                  |  Stateless Runtime Services    |
                  |  (Engine / Adapter / Registry) |
                  +---------------+----------------+
                                  |
                                  | Publishes task event
                                  v
+---------------------------------+---------------------------------+
| Background Scale Out (Asynchronous Workers)                       |
|                                                                   |
|  +--------------------+  +-------------------+  +--------------+  |
|  | Transcript Redact. |  | Audio Compression |  | Log Export   |  |
|  | (PII Redaction)    |  | (wav to mp3/ogg)  |  | & Archiving  |  |
|  +--------------------+  +-------------------+  +--------------+  |
|                                                                   |
+-------------------------------------------------------------------+
```

### 1. Scaling Concurrency Target
The platform cluster is calibrated to support:
* **Concurrent Voice Sessions:** 10,000 active streams.
* **WebSocket Turn Latency Budget:** <1000ms roundtrip.
* **Network & Validation Overhead:** <100ms.

To sustain this, the ingress Protocol Adapters and Conversation Engine runtimes are entirely stateless and do not persist session states in-memory.

### 2. Asynchronous Task Offloading
Synchronous processing of voice turns is completed as soon as the Text-to-Speech (TTS) wave is generated and streamed back. All post-turn and post-session processing is offloaded asynchronously to background workers via task queues (e.g., Celery running on Redis/RabbitMQ):
* **PII Redaction:** Transcript scrubbers scan text blocks for names and identifiers post-turn.
* **Audio Compression:** Raw PCM input files are compressed (e.g., converted to Ogg/Opus or MP3) in the background before S3 upload.
* **Log Exports:** Aggregating session histories and syncing to external tenant webhook endpoints.

### 3. Database Connection Pooling
To prevent PostgreSQL database exhaustion when scaling to hundreds of pod runtimes:
* **PgBouncer Gateway:** PgBouncer is deployed in front of the PostgreSQL instance to manage connection pooling.
* **Pooling Mode:** Configured to `transaction` pooling mode.
* **Target limits:** Max client connections are capped at 20,000; server-side pool is kept active at a maximum of 500 direct database sessions.

### 4. Registry Schema Local Caching
To eliminate database calls when resolving intent-to-capability schemas during conversation turns:
* Capability schemas are cached in local memory inside the Capability Registry container.
* Invalidation is event-driven; no polling of database metadata is allowed.
