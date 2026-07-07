# Traceability Matrix

## Purpose

This directory defines how Lyra connects requirements to architecture, APIs, implementation, tests, and documentation.

## Traceability Chain

Requirement → Architecture → API/Contract → Implementation → Tests → Documentation

## Required Evidence

| Link | Evidence |
| --- | --- |
| Requirement to Architecture | Specification section and related ADR. |
| Architecture to API/Contract | Contract, schema, or protocol document. |
| API/Contract to Implementation | Source files or module plans referencing requirement IDs. |
| Implementation to Tests | Test names, fixtures, and assertions referencing requirement IDs. |
| Tests to Documentation | PR summary and docs updated with behavior and compatibility notes. |

## Matrix Template

| Requirement ID | Architecture Doc | Contract/API | Implementation | Tests | Documentation | Status |
| --- | --- | --- | --- | --- | --- | --- |
| LYRA-FR-001 | `docs/architecture/system-overview.md` | `docs/contracts/README.md` | Not implemented | Not implemented | `docs/specifications/06-functional-requirements.md` | Planned |

## Operating Rule

If any cell is unknown for an implemented behavior, the repository is missing traceability and must be updated before the change is considered complete.
