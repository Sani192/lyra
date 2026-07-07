# Lyra

Lyra is an AI Voice Orchestration Platform for receiving customer conversations, understanding intent, invoking consumer application capabilities through standardized contracts, and coordinating the conversational experience from start to finish.

Lyra does **not** own business state. Consumer applications remain the systems of record for orders, customers, inventory, appointments, payments, loyalty, pricing, policies, and business rules. Lyra owns conversation context, AI orchestration, capability invocation, transcripts, recordings, analytics, events, contracts, and observability.

## Product Vision

Lyra makes voice automation safe, auditable, and integration-friendly by separating conversation intelligence from business systems. The platform should allow any consumer application to expose capabilities through REST, OpenAPI, or MCP contracts while Lyra orchestrates conversations against those capabilities without embedding consumer-specific logic.

## Documentation-First Philosophy

This repository is the source of truth for Lyra. Requirements, domain language, architectural decisions, contracts, standards, and playbooks must be documented before implementation begins. Implementation is expected to follow documented requirements and reference stable requirement IDs.

## Repository Structure

| Path | Purpose |
| --- | --- |
| `PROJECT.md` | Lyra constitution and mandatory first read for humans and AI agents. |
| `.ai/` | Numbered, canonical AI Knowledge Center documents for AI coding agents; unnumbered files are compatibility redirects only. |
| `docs/specifications/` | Numbered product and platform specifications. |
| `docs/architecture/` | Architecture narratives, open questions, and diagram placeholders. |
| `docs/decisions/` | Architecture Decision Records. |
| `docs/playbooks/` | Scenario-specific orchestration playbooks. |
| `docs/engineering/`, `docs/standards/` | Documentation, naming, versioning, branching, review, and coding standards. |
| `schemas/` | Draft schema documentation for contracts, capabilities, conversations, events, organizations, and workflows. |
| `examples/` | Consumer-domain examples for restaurants, clinics, hotels, CRM, and ERP systems. |
| `backend/`, `frontend/`, `sdk/` | Reserved implementation areas; intentionally documentation-only at bootstrap. |
| `tools/`, `scripts/` | Reserved operational helper areas; no runnable tooling is introduced during bootstrap. |

## Getting Started

1. Read `PROJECT.md` to understand non-negotiable principles.
2. Read `.ai/00-start-here.md` if you are an AI agent or operating with one; treat the numbered `.ai/` documents as canonical.
3. Review `docs/specifications/06-functional-requirements.md` and `docs/specifications/07-non-functional-requirements.md` before proposing implementation.
4. Check `docs/decisions/` before changing architecture.
5. Update documentation and requirement references before writing code.

## Repository Standards

* Lyra is contract driven and protocol agnostic.
* Architecture decisions require ADRs.
* Backward compatibility must be preserved where reasonable.
* Consumer-specific business rules must remain outside Lyra.
* Documentation changes should accompany any requirement, architecture, or behavior change.

## Contribution Guidelines

See `CONTRIBUTING.md` and the standards in `docs/engineering/`, `docs/standards/`. Contributions should be small, reviewable, linked to requirement IDs, and aligned with the product constitution in `PROJECT.md`.

## Future Roadmap

The roadmap begins with contract modeling, capability registry design, conversation lifecycle definitions, event semantics, observability requirements, and reference consumer examples. Implementation will follow only after the core specifications and ADRs are approved.
