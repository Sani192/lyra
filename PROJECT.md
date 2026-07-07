# Lyra Project Constitution

## Status

Authoritative. This document is mandatory reading for every human contributor and AI coding agent before changing the repository.

## Mission

Lyra makes production voice automation safe, observable, and integration-friendly. It orchestrates customer conversations, understands intent, invokes consumer-owned capabilities through explicit contracts, and records the evidence needed to operate those conversations responsibly.

## Vision

Lyra should become the neutral orchestration layer between conversational AI and business systems. Any organization should be able to expose capabilities through REST, OpenAPI, MCP, or future protocols while Lyra coordinates the conversation without absorbing consumer business logic or becoming a domain-specific application.

## Engineering Philosophy

* Prefer explicit contracts over implicit behavior.
* Prefer documented decisions over tribal knowledge.
* Prefer boring, observable, testable components over clever abstractions.
* Prefer protocol-agnostic domain models with protocol-specific adapters at the edge.
* Prefer compatibility, migration paths, and clear deprecation over silent breaking changes.

## Architecture Philosophy

Lyra owns conversation orchestration, runtime coordination, transcripts, recordings, analytics, contracts, capability invocation metadata, and observability. Consumer applications own customers, orders, inventory, appointments, payments, loyalty state, pricing, policies, and business rules. Conversation state is not business state.

## Repository Philosophy

The repository is the single source of truth. Every important requirement, domain term, architecture decision, contract convention, and engineering standard belongs in version control. Documents must be understandable without previous chat history.

## Documentation Philosophy

Documentation precedes implementation. Specifications explain what must be true, ADRs explain why architectural choices were made, standards explain how contributors work, examples show safe integration patterns, and traceability links requirements to architecture, APIs, implementation, tests, and documentation.

## Design Principles

1. Lyra never owns consumer business state.
2. Consumer applications own business logic.
3. Integrations are contract-driven.
4. Capabilities are protocol-agnostic.
5. REST, OpenAPI, and MCP are first-class protocols.
6. Observability is a product feature.
7. Security, privacy, and tenant isolation are design constraints.
8. Requirement IDs are stable references for planning, reviews, commits, tests, and documentation.
9. Architecture decisions require ADRs.
10. Examples must reinforce boundaries rather than imply hidden platform behavior.

## Decision-Making Framework

When evaluating a change, answer these questions in order:

1. Which requirement IDs justify the change?
2. Does the change keep business state and business logic in the consumer application?
3. Does the change preserve protocol agnosticism?
4. Does the change require a new or updated ADR?
5. What documentation, contracts, examples, and tests must change with it?
6. What compatibility or migration impact does it create?
7. How will operators observe and debug the behavior?

## Non-Negotiable Rules

* Never introduce consumer-specific business logic into Lyra.
* Never make Lyra the system of record for external business domains.
* Never hardcode behavior for one consumer when a contract, playbook, or configuration should describe it.
* Never implement a material feature without requirement IDs and documentation.
* Never bypass contract validation, traceability, security review, or ADR requirements.

## Definition of Ready

A change is ready for implementation only when the relevant requirement IDs, affected documents, compatibility impact, test strategy, and architecture decision status are known.

## Definition of Done

A change is done only when documentation is updated, requirement IDs are traceable, tests/checks are recorded, compatibility impact is documented, examples are updated when behavior is visible, and reviewers can understand the change without external context.

## Contribution Workflow

1. Read `PROJECT.md`, `README.md`, and `.ai/00-start-here.md`.
2. Identify affected requirements in `docs/specifications/` and `.ai/05-requirements-index.md`.
3. Review related ADRs in `docs/decisions/`.
4. Update specifications, contracts, schemas, examples, or standards before implementation.
5. Make the smallest coherent change.
6. Run relevant checks.
7. Document traceability and review evidence.

## AI Workflow

AI agents must assume no prior chat history. Before changing code or docs, read the AI Knowledge Center, identify requirement IDs, inspect affected contracts and ADRs, state assumptions in the change, and avoid adding application features unless explicitly requested.

## Human Workflow

Human contributors should use the same standards as AI agents: write down decisions, keep changes reviewable, challenge hidden assumptions, and require traceability between requirements, architecture, implementation, tests, and documentation.

## Repository Map

| Path | Purpose |
| --- | --- |
| `.ai/` | Mandatory AI Knowledge Center and operating guide. |
| `docs/specifications/` | Numbered product, platform, API, security, observability, deployment, and UI requirements. |
| `docs/architecture/` | Component, lifecycle, protocol, storage, security, scalability, and deployment architecture. |
| `docs/contracts/` | Consumer contract guidance and integration expectations. |
| `docs/decisions/` | Architecture Decision Records. |
| `docs/engineering/` | Engineering standards for coding, documentation, versioning, branching, review, testing, conventions, and traceability. |
| `docs/traceability/` | Requirement-to-delivery traceability model. |
| `examples/` | Domain examples demonstrating contracts, conversations, capabilities, expected JSON, and failure cases. |
| `schemas/` | JSON schemas for contracts, capabilities, conversations, events, organizations, and workflows. |
| `backend/`, `frontend/`, `sdk/` | Reserved implementation areas; do not add business logic without explicit implementation approval. |

## Quality Standards

All repository content must be accurate, cross-referenced, professionally written, and useful to a future contributor. Placeholder text, unexplained TODOs, broken links, and ambiguous ownership are not acceptable.
