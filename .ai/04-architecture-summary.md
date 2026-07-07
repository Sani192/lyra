# 04 Architecture Summary

## Major Components

* Conversation Engine: manages turn-taking, context, transcripts, and session lifecycle.
* AI Agent Layer: performs intent/entity extraction and response planning.
* Capability Registry: discovers and describes available consumer actions.
* Protocol Layer: adapts REST, OpenAPI, MCP, and webhooks to capability semantics.
* Workflow Engine: coordinates playbooks, prompts, capability calls, and escalation.
* Observability Layer: records events, decisions, invocations, errors, and audit evidence.
* Contract Layer: validates consumer contracts, schemas, versions, and compatibility.

## Boundaries and Data Ownership

Lyra owns orchestration metadata. Consumer applications own business state and business decisions. Protocol adapters translate, but do not reinterpret, consumer business behavior.

## Extension Points

New protocols, capability metadata, observability sinks, workflow patterns, AI providers, and SDKs may be added if they preserve contract-driven boundaries.

## Future Scalability

The architecture should support multi-tenant isolation, horizontal scaling of stateless runtime services, event-driven processing, versioned contracts, and independent protocol adapter evolution.
