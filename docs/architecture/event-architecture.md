# Event Architecture

## Maturity Metadata

**Status:** Approved.

**Intended Use:** Authoritative architectural design and specifications for Lyra's event-driven runtime and asynchronous integrations.

## Purpose

Define the platform's asynchronous messaging architecture, detailing event types, broker selection guidelines, retry policies, and observability streams to maintain system performance under sustained load.

## Event-Driven Architecture Overview

Lyra leverages an asynchronous Event-Driven Architecture (EDA) to decouple latency-sensitive conversation routing from long-running operations (such as audio encoding, transcript redaction, and webhook notifications).

```
   +----------------------+
   | Protocol Adapter     |
   +----------+-----------+
              | WebSocket / REST
              v
   +----------+-----------+
   | Conversation Engine  |
   +----------+-----------+
              |
              | Emits turn event
              v
     ==================== [ Message Broker / Pub-Sub ] ====================
              |                                            |
              +---------------------+                      +---------------+
              |                     |                      |               |
              v                     v                      v               v
   +----------+-----------+  +------+------+        +------+------+  +-----+-----+
   | Workflow Engine      |  | Audio Proc. |        | Observabil. |  | Webhook   |
   | (Playbook Exec)      |  | (S3 Storage)|        | Logs        |  | Dispatcher|
   +----------------------+  +-------------+        +-------------+  +-----------+
```

### 1. Classification of Event Types
All event messages emitted across the platform are serialized as JSON payloads conforming to `schemas/event.schema.json`. Events are classified into four main categories:

* **System Events:** Infrastructure status updates (e.g., `REGISTRY_STARTED`, `DATABASE_CONNECT_FAILED`).
* **Session Events:** Turn-level conversation transitions (e.g., `SESSION_INIT`, `AUDIO_CHUNK_RECEIVED`, `INTENT_DETECTED`, `DIALOGUE_TURN_COMPLETE`).
* **Capability Events:** Integration execution logs (e.g., `CAPABILITY_INVOCATION_REQUESTED`, `CAPABILITY_INVOCATION_SUCCESSFUL`, `CAPABILITY_INVOCATION_FAILED`).
* **Audit & Analytics Events:** Compliance markers (e.g., `TRANSCRIPT_PII_REDACTED`, `SESSION_ARCHIVED`, `CREDENTIAL_ACCESS_RECORDED`).

### 2. Message Broker Selection Guidelines
* **Primary Message Broker:** RabbitMQ (AMQP 0-9-1) is selected as the default message broker for production due to its native support for complex routing, queue persistence, and acknowledgment mechanisms.
* **Low-Latency Messaging (In-Memory Mocks):** For local development and testing, Redis Pub/Sub may be substituted to minimize environment footprints.

### 3. Queue Topology
The message broker is partitioned into designated exchanges and queues:
* `lyra.exchange.sessions` (Topic): Routes all conversation and session lifecycle events.
* `lyra.queue.transcripts` (Durable): Buffers transcripts before writing to persistence.
* `lyra.queue.audio` (Durable): Handles raw audio buffers for background compression and S3 ingestion.
* `lyra.queue.webhooks` (Lazy / Durable): Backlog queue for delivering async notifications to tenant systems.

### 4. Retry and Dead Letter Queue (DLQ) Policies
When a downstream event subscriber fails (e.g., the Webhook Dispatcher cannot reach a tenant callback URL):
1. **Exponential Backoff:** The dispatcher retries delivery up to 5 times using exponential backoff with jitter (initial delay: 2 seconds, backoff factor: 2.0).
2. **Dead Letter Queue:** If the retry threshold is exceeded, the message is routed to `lyra.queue.dlq.webhooks`.
3. **Alerting:** An observability audit event `WEBHOOK_DELIVERY_EXCEEDED` is published, triggering alerts for system operators.
