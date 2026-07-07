# 10 Implementation Readiness

## Maturity Metadata

**Status:** Approved.

**Intended Use:** Authoritative AI-agent readiness gate for deciding whether repository work may proceed to implementation; safe for implementation-readiness, traceability, and review-scope decisions.

## Purpose

This document defines what an AI agent may implement immediately, what must not be implemented yet, which documents are required before touching implementation surfaces, the minimum traceability evidence a change must carry, and the assumptions an AI agent must not make.

## 1. What an AI Agent May Implement Today

An AI agent may implement only work that is explicitly requested and already supported by approved or implementation-ready documentation. Safe work includes:

* Documentation-only improvements that clarify existing approved requirements, architecture, contracts, examples, traceability, or AI-agent guidance without inventing new behavior.
* Compatibility redirects, index updates, link fixes, typo fixes, formatting fixes, and repository navigation improvements that preserve existing meaning.
* Small examples or schema/documentation corrections when the governing requirement IDs, contract boundaries, compatibility expectations, and validation expectations are already documented.
* Implementation scaffolding only when the relevant approved documents identify the target component, ownership boundary, requirement IDs, compatibility impact, and test strategy.
* Tests or checks for already-documented behavior when they cite the applicable requirement IDs and do not introduce new product behavior.

If a change affects runtime behavior, public APIs, schemas, contracts, SDKs, examples, security posture, observability, storage, tenant isolation, or compatibility, the agent must first prove that the required documents in this file exist and are mature enough to authorize implementation.

## 2. What Is Explicitly Not Ready for Implementation

The following work is not ready for implementation unless the repository contains approved or implementation-ready source documents that authorize it for the specific scope:

* Backend runtime services, orchestration engines, persistence layers, job workers, protocol adapters, authentication, authorization, tenant isolation, observability pipelines, and deployment automation.
* Frontend applications, dashboards, operator workflows, analytics views, configuration screens, and user-facing product behavior.
* SDK packages, generated clients, public API helpers, runtime libraries, or consumer integration tooling.
* New or changed JSON schemas, consumer contracts, OpenAPI/MCP/REST conventions, event formats, webhooks, compatibility rules, or versioning behavior.
* Examples that imply Lyra owns consumer business state, encodes consumer business policy, or provides hidden platform behavior not documented in specifications and contracts.
* Domain-specific business logic for customers, orders, inventory, appointments, payments, loyalty, pricing, eligibility, fulfillment, refunds, or other consumer-owned decisions.
* Any material feature that lacks requirement IDs, acceptance criteria, architecture alignment, security/privacy review expectations, compatibility notes, and test evidence.

Draft, placeholder, deprecated, or superseded documents are not sufficient implementation authority. Review-ready documents may inform planning only when paired with an approved companion source that resolves the relevant implementation decision.

## 3. Required Documents Before Touching Implementation Surfaces

Before touching backend, frontend, SDK, schemas, contracts, or examples, an AI agent must read and cite the applicable sources below in the change evidence.

| Surface | Required documents before edits |
| --- | --- |
| Backend | `PROJECT.md`, `.ai/00-start-here.md`, `.ai/05-requirements-index.md`, relevant `docs/specifications/` requirement chapters, related `docs/architecture/` documents, related ADRs in `docs/decisions/`, relevant engineering standards in `docs/engineering/`, and affected contracts/schemas/examples. |
| Frontend | `PROJECT.md`, `.ai/00-start-here.md`, `.ai/05-requirements-index.md`, UI and API requirement chapters, relevant architecture documents, related ADRs, frontend engineering standards, affected API contracts/schemas, and visible examples or operator workflows. |
| SDK | `PROJECT.md`, `.ai/00-start-here.md`, `.ai/05-requirements-index.md`, API and contract requirements, versioning/compatibility standards, related ADRs, affected schemas/contracts, and examples that demonstrate supported integration behavior. |
| Schemas | `PROJECT.md`, `.ai/00-start-here.md`, `.ai/05-requirements-index.md`, relevant requirement chapters, schema/versioning/compatibility standards, related ADRs, affected contracts, validation expectations, migration notes, and examples. |
| Contracts | `PROJECT.md`, `.ai/00-start-here.md`, `.ai/05-requirements-index.md`, relevant contract and API specifications, related ADRs, affected schemas, compatibility/versioning standards, validation expectations, security/privacy requirements, and examples. |
| Examples | `PROJECT.md`, `.ai/00-start-here.md`, `.ai/02-core-principles.md`, `.ai/05-requirements-index.md`, relevant requirements, affected contracts/schemas, architecture boundary documents, and any ADR that constrains the example behavior. |

If any required document is missing, immature for the intended implementation authority, or contradictory, the agent must stop implementation and update or request the required documentation path first.

## 4. Minimum Traceability Evidence Required in a Change

Every material change must include traceability evidence that a reviewer can verify without external chat history. At minimum, the change must identify:

1. Requirement IDs that authorize the change, or a clear statement that the change is documentation/navigation-only and does not alter requirements or behavior.
2. Source documents read, including the relevant specification, architecture, ADR, contract, schema, example, or engineering standard files.
3. Affected implementation surfaces such as backend, frontend, SDK, schemas, contracts, examples, documentation, or tests.
4. Boundary analysis confirming Lyra does not become the owner of consumer business state or consumer business logic.
5. Compatibility impact, including whether the change is additive, breaking, deprecated, migration-related, or behavior-preserving.
6. Test or validation evidence, including commands run, files checked, or a documented reason when no executable check applies.
7. Documentation updates made with the implementation, or an explanation of why existing approved documentation already covers the change.
8. Assumptions that remain after review, especially where future work, ADRs, or specifications are still needed.

A change that cannot provide this evidence is not ready to merge and should not proceed beyond documentation preparation.

## 5. Red-Flag Assumptions an AI Agent Must Not Make

An AI agent must not assume that:

* A directory name such as `backend/`, `frontend/`, `sdk/`, `schemas/`, `docs/contracts/`, or `examples/` means implementation is approved.
* A placeholder, draft, deprecated, superseded, or unnumbered compatibility file is authoritative.
* Missing requirements may be invented from prior chat context, common SaaS patterns, framework defaults, or inferred product intent.
* Lyra may store consumer-owned business records because doing so is convenient for orchestration.
* Lyra may encode consumer pricing, inventory, appointment, payment, loyalty, eligibility, fulfillment, refund, or policy decisions.
* Protocol-specific behavior may leak into core domain models instead of remaining at protocol adapters or contract boundaries.
* REST, OpenAPI, and MCP integrations may have different domain semantics for the same capability.
* Examples may demonstrate behavior not supported by requirements, schemas, contracts, and architecture decisions.
* Observability, auditability, security, privacy, tenant isolation, validation, versioning, or compatibility can be added later without design authority.
* Tests alone make a feature ready when requirements, ADRs, schemas, contracts, or compatibility notes are missing.
* A small implementation change is exempt from traceability, documentation, or review evidence.

When any red flag appears, the agent must pause implementation and prepare the missing documentation, decision record, requirement, contract, schema, example, or traceability update first.
