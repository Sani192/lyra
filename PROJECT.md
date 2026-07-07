# Lyra Project Constitution

## Maturity Metadata

**Status:** Approved.

**Intended Use:** Authoritative project constitution and repository policy; safe for implementation decisions about Lyra boundaries, workflows, and documentation maturity.

**Last Updated:** 2026-07-07

**Version:** 1.1.0

## Status

Approved and authoritative. This document is mandatory reading for every human contributor and AI coding agent before changing the repository.

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

* Lyra owns conversation orchestration, runtime coordination, transcripts, recordings, analytics, contracts, capability invocation metadata, and observability.
* Consumer applications own customers, orders, inventory, appointments, payments, loyalty state, pricing, policies, and business rules.
* Conversation state is not business state.

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

## Artifact-Specific Readiness and Done Criteria

The repository-wide Definition of Ready and Definition of Done are specialized by artifact type in `docs/engineering/review-process.md`. Contributors must use the applicable artifact-specific checklist for requirement changes, architecture changes, ADRs, schema changes, contract changes, examples/playbooks, backend implementation, frontend implementation, SDK implementation, and security-sensitive changes.

For every applicable category, readiness must identify required documentation, planned tests or validation, traceability targets, compatibility impact, and expected review evidence before work starts. Done means those documents, tests, traceability links, compatibility or migration notes, and review records are complete enough for a future contributor to audit the change without external context.

## Contribution Workflow

1. Read `PROJECT.md`, `README.md`, and `.ai/00-start-here.md`.
2. Identify affected requirements in `docs/specifications/` and `.ai/05-requirements-index.md`.
3. Review related ADRs in `docs/decisions/`.
4. Update specifications, contracts, schemas, examples, or standards before implementation.
5. Make the smallest coherent change.
6. Run relevant checks.
7. Document traceability and review evidence.

## AI Workflow

AI agents must assume no prior chat history. Before changing code or docs, read `.ai/00-start-here.md`, `.ai/10-implementation-readiness.md`, and the relevant numbered AI Knowledge Center documents; identify requirement IDs; inspect affected contracts and ADRs; state assumptions in the change; and avoid adding application features unless explicitly requested.

## Human Workflow

Human contributors should use the same standards as AI agents: write down decisions, keep changes reviewable, challenge hidden assumptions, and require traceability between requirements, architecture, implementation, tests, and documentation.

## Repository Map

| Path | Purpose |
| --- | --- |
| `.ai/` | Mandatory numbered AI Knowledge Center and operating guide, including `.ai/10-implementation-readiness.md` as the implementation-readiness gate. |
| `docs/specifications/` | Numbered product, platform, API, security, observability, deployment, and UI requirements. |
| `docs/architecture/` | Independent, production-grade architectural design specifications for platform components, events, scalability, and security. |
| `docs/decisions/` | Architecture Decision Records. |
| `docs/engineering/` | Consolidated engineering standards including coding style, formatting, branching, naming, review processes, versioning, and traceability. |
| `docs/traceability/` | Requirement-to-delivery traceability model. |
| `docs/api/` | API contract references and protocol adapter specifications. |
| `docs/deployment/` | Deployment environments, Kubernetes configs, and deployment guides. |
| `docs/diagrams/` | Visual architectural and flow diagrams. |
| `docs/examples/` | Domain example references and validation instructions. |
| `docs/glossary/` | Centralized terminology definition sheet. |
| `docs/playbooks/` | Scenario-specific AI execution scripts and prompt flows. |
| `docs/security/` | Threat modeling, authentication protocols, and isolation rules. |
| `docs/vision/` | Product scope, target personas, and roadmap narratives. |
| `examples/` | Domain examples demonstrating contracts, conversations, capabilities, expected JSON, and failure cases. |
| `schemas/` | JSON schemas for contracts, capabilities, conversations, events, organizations, and workflows. |
| `backend/`, `frontend/`, `sdk/` | Reserved implementation areas; do not add business logic without explicit implementation approval. |
| `tools/` | Automated platform validation tools, schema linter scripts. |
| `scripts/` | Development utility and onboarding automation scripts. |

## Repository Maturity Model

Every major documentation artifact must declare both a status and intended use before it can guide planning, review, or implementation. The status controls how much authority the artifact has in repository decisions.

| Status | Meaning | Implementation Authority |
| --- | --- | --- |
| `Placeholder` | The file exists to reserve a topic, location, or future contract but is intentionally incomplete. | Not safe for implementation decisions. |
| `Draft` | The document contains initial content that needs review, validation, or traceability before it becomes authoritative. | Not safe as the sole basis for implementation decisions. |
| `Review Ready` | The content is complete enough for formal product, architecture, security, or engineering review. | Safe for review planning, not implementation unless paired with approved sources. |
| `Approved` | The document has been accepted as authoritative for its stated scope. | Safe for implementation decisions within its scope. |
| `Implementation Ready` | The document is approved and has enough acceptance criteria, compatibility notes, and traceability for engineering work to start. | Safe and preferred for implementation decisions. |
| `Deprecated` | The document remains available for historical context, but should not guide new work. | Not safe for new implementation decisions. |
| `Superseded` | The document has been replaced by another source of truth. | Not safe; use the replacement document named in the file. |

Major documentation files under `docs/specifications/`, `docs/architecture/`, `docs/decisions/`, `schemas/`, `examples/`, and `.ai/` must include status metadata and intended-use guidance. Markdown files should use a `Maturity Metadata` section near the top. JSON files should use explicit status and intended-use metadata fields appropriate to the file type.

Implementation work may rely on `Approved` or `Implementation Ready` documents. `Review Ready` documents may inform implementation only when the pull request cites the approved companion source that resolves the relevant decision. `Placeholder`, `Draft`, `Deprecated`, and `Superseded` documents must not be used as standalone implementation authority.

## Governance

Governance defines which repository artifacts have authority, who must approve material changes, how conflicts are resolved, and when work may move from specification to implementation. It supplements the review evidence required by `docs/engineering/review-process.md` and the requirement-to-delivery chain defined in `docs/traceability/README.md`.

### Document Authority Hierarchy

Authoritative decisions must be made from the highest applicable source in this order:

1. `PROJECT.md` establishes repository-wide mission, boundaries, contribution rules, maturity rules, and governance.
2. Approved `.ai/` operating documents establish AI-agent workflow, implementation-readiness checks, and repository navigation rules.
3. Approved or Implementation Ready specifications in `docs/specifications/` establish product, platform, API, security, observability, deployment, and UI requirements.
4. Approved architectural design specifications in `docs/architecture/` establish components boundaries, lifecycle state machines, and protocols adapter specifications.
5. Approved ADRs in `docs/decisions/` establish architectural decisions and accepted tradeoffs.
6. Approved schemas in `schemas/` and contract guidance in `docs/contracts/` establish machine-readable contract constraints and integration expectations.
7. Approved examples in `examples/` demonstrate expected usage, safe integration patterns, and failure cases but do not create requirements by themselves.
8. Implementation in `backend/`, `frontend/`, `sdk/`, and related source areas demonstrates current behavior but must be corrected when it conflicts with authoritative documentation.

Lower-authority artifacts may clarify higher-authority documents, but they must not override them. If a lower-authority artifact appears to add, remove, or contradict a requirement, reviewers must classify the change and update the higher-authority source first.

### Required Approvers

Changes require reviewers with authority over the highest-impact classification involved:

| Change area | Required approvers | Designated Role Assignments |
| --- | --- | --- |
| Specifications | Product owner or designated Product Managers, plus Engineering Lead. | **Product Owner:** `@Sani192`<br>**Product Manager:** `@PM_Lyra` |
| ADRs | Architecture owner or designated Technical Leads, plus component maintainers. | **Architecture Owner:** `@Sani192`<br>**Architectural Board:** `@Arch_Guild` |
| Schemas and contracts | Schema owner, API Lead, and designated Integration Reviewers. | **Schema & API Owner:** `@Sani192`<br>**Integration Lead:** `@API_Lead` |
| Security-sensitive changes | Security owner, plus Architecture Owner when boundaries change. | **Security Owner:** `@Sani192`<br>**Security Auditor:** `@Sec_Auditor` |
| Public API changes | API owner, SDK Maintainer, and designated Technical Writers. | **API Owner:** `@Sani192`<br>**Tech Writer:** `@Docs_Lead` |

When one change spans multiple areas, all applicable approver groups are required. Reviewers must verify the review checklist in `docs/engineering/review-process.md` and ensure traceability evidence is complete according to `docs/traceability/README.md`.

### Conflict Resolution Order

When repository sources disagree, resolve the conflict in this order:

1. Preserve Lyra's non-negotiable rules and project boundaries in this document.
2. Prefer the artifact with higher authority in the document authority hierarchy.
3. Prefer `Implementation Ready` over `Approved`, `Approved` over `Review Ready`, and reviewed documents over `Draft` or `Placeholder` documents.
4. Prefer the more specific approved artifact when it does not contradict a higher-authority source. For example, an ADR may refine a specification's implementation approach, and a schema may constrain a contract field.
5. Prefer the newer approved ADR or specification when it explicitly supersedes an older decision and names the superseded source.
6. Treat examples and implementation as evidence of current behavior, not authority to bypass requirements, ADRs, schemas, or security review.
7. If the conflict affects requirements, architecture, schema compatibility, security, or public APIs, stop implementation until the authoritative document is updated and approved.

### Change Classification

Every non-trivial change must be classified in the pull request and reviewed according to the highest applicable class:

| Classification | Meaning | Governance expectations |
| --- | --- | --- |
| Documentation-only | Clarifies wording, fixes links, improves examples, or corrects non-normative text without changing requirements, architecture, schemas, APIs, or behavior. | Requires documentation review and link/check evidence. |
| Requirement-changing | Adds, removes, reinterprets, or changes acceptance criteria, requirement IDs, user-visible behavior, compatibility promises, or readiness expectations. | Requires specification updates, requirement IDs, traceability updates, and product/specification approval before implementation. |
| Architecture-changing | Changes component responsibilities, system boundaries, data ownership, lifecycle, protocols, persistence, deployment topology, or material tradeoffs. | Requires an ADR or ADR update, architecture approval, affected documentation updates, and traceability to requirements. |
| Schema-changing | Changes JSON schemas, contracts, validation behavior, compatibility rules, examples that assert contract shape, or generated artifacts. | Requires schema/contract approval, compatibility notes, migration guidance when needed, and tests or validation evidence. |
| Implementation-changing | Changes runtime behavior, source code, build outputs, tests, or operational behavior without changing approved requirements or architecture. | Requires requirement traceability, relevant tests/checks, documentation updates for visible behavior, and component maintainer review. |

If a change could reasonably fit more than one class, use the more restrictive classification and document why. Security-sensitive and public API changes always require the approvers named above even when the textual diff appears small.

### Release and Readiness Gates

Work may move from specification to implementation only after all applicable gates are satisfied:

1. The relevant requirement IDs exist, are stable, and are cited in the planned change.
2. Affected specifications are `Approved` or `Implementation Ready`, or the pull request cites an approved companion source that resolves any `Review Ready` material.
3. Required ADRs exist and are approved for architecture-changing work.
4. Schemas, contracts, and examples are updated before or alongside implementation when behavior is externally visible.
5. Security, privacy, tenant isolation, compatibility, migration, and observability impacts are explicitly assessed.
6. The traceability chain from requirement to architecture, API/contract, implementation, tests, and documentation is known or updated according to `docs/traceability/README.md`.
7. Required approvers have reviewed the change under `docs/engineering/review-process.md`.
8. Relevant validation checks, contract checks, tests, and documentation checks are recorded before release or merge.

A change that fails any gate is not ready for implementation. If implementation already exists and governance evidence is missing, the next change must either add the missing evidence or roll the behavior back behind an approved plan.

### Constitution Amendment Procedure

Amending `PROJECT.md` is classified as an **Architecture-changing** modification. Any change to this document must:
1. File an issue outlining the constitutional gap or conflict.
2. Draft the proposed change in a feature branch.
3. Obtain unanimous approval from the designated Architecture Owner (`@Sani192`) and Product Owner (`@Sani192`).
4. Record the version bump and date in the Revision History of this document.

## Quality Standards

All repository content must be accurate, cross-referenced, professionally written, and useful to a future contributor. Placeholder text, unexplained TODOs, broken links, and ambiguous ownership are not acceptable.

## Revision History

| Date | Version | Author | Notes |
| --- | --- | --- | --- |
| 2026-07-07 | 1.1.0 | Lyra Architecture Team | Consolidate standards under engineering directory, resolve ID patterns, add ADR-0006 playbook decision, and expand reviewer roles. |
| 2026-07-07 | 1.0.0 | Lyra Architecture Team | Complete remediation audit updates, repository map alignment, named approvers, and amendment procedure. |
