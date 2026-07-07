# 04 Architecture Summary

## Maturity Metadata

**Status:** Approved.

**Intended Use:** Authoritative AI-agent operating context; safe for repository navigation and architectural boundary verification.

## Technology Stack

Lyra is implemented using:
- **Language:** Python 3.11+ (static typing enforced).
- **Core Framework:** FastAPI for asynchronous REST endpoints.
- **Validation Engine:** Pydantic and jsonschema.
- **Database / Logs:** PostgreSQL for conversation metadata; S3 for transcripts and audio recordings.

## Major Components

1. **Protocol Adapters:** Expose REST, OpenAPI, and MCP endpoints, converting inbound audio/text into platform-neutral session events.
2. **Conversation Engine:** Coordinates conversational turns, managing session context and persisting transcripts/recordings.
3. **AI Agent Layer:** Performs NLU tasks (intent resolution, entity extraction, response prompt generation).
4. **Workflow Engine:** Coordinates sequential logic defined in playbooks, handling multi-step processes and escalations.
5. **Capability Registry:** Discovers and registers consumer contracts. Validates payload schemas at invocation boundaries.
6. **Observability Layer:** Emits structured events for auditable tracing of all routing decisions and API calls.

## Component Interaction Flow

```
+----------+      1. Event      +--------------------+      2. Query      +----------------+
|  Client  | ------------======>|  Protocol Adapter  | ==================>|  Conversation  |
+----------+                    +--------------------+                    |     Engine     |
     ^                                                                    +-------+--------+
     |                                                                            |
     |                                                                            | 3. Get Context
     |                                                                            v
     |                          +--------------------+      4. Extract    +-------+--------+
     | 7. Response              |   Workflow Engine  | <================= |    AI Agent    |
     +------------------------- | (Execute Playbook) |                    |     Layer      |
                                +---------+----------+                    +----------------+
                                          |
                                          | 5. Invoke (Validate)
                                          v
                                +---------+----------+      6. REST/MCP   +----------------+
                                | CapabilityRegistry | ==================>|  Consumer API  |
                                +--------------------+                    +----------------+
```

## Boundaries and Data Ownership

* **Lyra owns:** Orchestration metadata, turn logs, transcripts, audio recordings, capability contracts.
* **Consumer owns:** Customer profiles, orders, inventories, transaction rules, pricing calculations.

## Related Documents

- Detailed component definitions: [Component Architecture](../docs/architecture/component-architecture.md)
- Conversation flow details: [Conversation Lifecycle](../docs/architecture/conversation-lifecycle.md)
- Invocation mechanics: [Capability Invocation](../docs/architecture/capability-invocation.md)
