# Integration Layer Architecture

## Maturity Metadata

**Status:** Approved.

**Intended Use:** Authoritative architectural design and specifications for Lyra's integration adapters and contract mappings.

## Purpose

Define the integration layer, specifying how external protocols (REST, OpenAPI, MCP) map to Lyra's internal, protocol-agnostic domain models, and establishing secure credential management guidelines for downstream APIs.

## Integration Layer Design

The Integration Layer acts as an adapter boundary between external protocols and the core Conversation Engine. This guarantees that internal models remain decoupled from transport-specific payloads.

```
+--------------------------------------------------------------+
| Ingress Transport Edge                                       |
|                                                              |
|   +-------------------+  +-------------------+  +---------+  |
|   |  WebSocket Audio  |  |  HTTP REST Turns  |  |   MCP   |  |
|   +---------+---------+  +---------+---------+  +----+----+  |
+-------------|----------------------|-----------------|-------+
              v                      v                 v
+-------------+----------------------+-----------------+-------+
| Protocol Adapters                                            |
| (Translates external payload to Lyra standard schema format) |
+----------------------------+---------------------------------+
                             |
                             v
+----------------------------+---------------------------------+
| Core Conversation Engine                                     |
| (Stateless session orchestrator)                             |
+----------------------------+---------------------------------+
                             |
                             v
+----------------------------+---------------------------------+
| Capability Invocation Client                                 |
| (Injects Vault keys & maps call payload to consumer API)     |
+----------------------------+---------------------------------+
```

### 1. Protocol Adapters
Protocol adapters convert protocol-specific formats into internal structured session events:
* **REST Adapter (`/v1/conversation/message`):** Standard HTTP endpoints for transactional message exchanges.
* **WebSocket Adapter (`/v1/conversation/stream`):** Bidirectional TCP socket handler for streaming raw binary audio packets and receiving low-latency synthesized audio turns.
* **Model Context Protocol (MCP) Adapter:** Registers Lyra as an MCP client. This allows the Workflow Engine to dynamically invoke tools exposed by external MCP servers using standardized JSON-RPC schemas.

### 2. OpenAPI Import Engine
To facilitate rapid onboarding of tenant services, the Capability Registry includes an OpenAPI Parser:
* Reads OpenAPI v3 specifications (JSON/YAML) from registered tenant repositories.
* Automatically translates operations into Lyra capability schemas, mapping input parameters to JSON Schema Draft 2020-12 validations.
* Exposes registration validation logs via the developer CLI.

### 3. Authentication & Credential Injection
Lyra never stores plain-text API credentials. All authentication details are managed as follows:
* Credentials (API keys, OAuth2 client secrets, Mutual TLS certs) are namespace-isolated by tenant ID in secure vaults (e.g. HashiCorp Vault).
* During capability invocation, the client retrieves credentials dynamically using the tenant-scoped token.
* Credentials are injected into outgoing request headers (e.g., as `X-API-Key` or `Authorization: Bearer <token>`) at the outbound adapter boundary.
