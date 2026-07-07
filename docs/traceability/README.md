# Traceability Matrix

## Maturity Metadata

**Status:** Approved.

**Intended Use:** Authoritative requirement-to-delivery mapping matrix.

## Purpose

This directory defines how Lyra connects requirements to architecture, APIs, implementation, tests, and documentation.

## Traceability Chain

```
Requirement → Architecture → API/Contract → Implementation → Tests → Documentation
```

## Required Evidence

| Link | Evidence |
| --- | --- |
| Requirement to Architecture | Specification section and related ADR. |
| Architecture to API/Contract | Contract, schema, or protocol document. |
| API/Contract to Implementation | Source files or module plans referencing requirement IDs. |
| Implementation to Tests | Test names, fixtures, and assertions referencing requirement IDs. |
| Tests to Documentation | PR summary and docs updated with behavior and compatibility notes. |

## Matrix

| Requirement ID | Architecture Doc | Contract/API | Implementation | Tests | Documentation | Status |
| --- | --- | --- | --- | --- | --- | --- |
| **LYRA-FR-001** (Stateless Orchestration) | `docs/architecture/system-overview.md` | `schemas/conversation.schema.json` | Reserved (`backend/`) | Planned | `docs/specifications/06-functional-requirements.md` | Planned |
| **LYRA-FR-002** (Contract-Driven Calling) | `docs/architecture/capability-invocation.md` | `schemas/contract.schema.json`, `schemas/capability.schema.json` | Reserved (`backend/`) | Planned | `docs/specifications/06-functional-requirements.md` | Planned |
| **LYRA-NFR-001** (Tenant Isolation) | `docs/architecture/system-overview.md` | `schemas/organization.schema.json` | Reserved (`backend/`) | Planned | `docs/specifications/07-non-functional-requirements.md` | Planned |
| **LYRA-NFR-002** (Observability Tracing) | `docs/architecture/system-overview.md` | `schemas/event.schema.json` | Reserved (`backend/`) | Planned | `docs/specifications/07-non-functional-requirements.md` | Planned |

## Operating Rule

If any cell is unknown for an implemented behavior, the repository is missing traceability and must be updated before the change is considered complete.
