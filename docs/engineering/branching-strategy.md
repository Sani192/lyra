# Branching Strategy

## Purpose

Branching strategy favors small requirement-scoped branches named with requirement IDs, for example `docs/LYRA-FR-001-contract-traceability`.

## Scope

Applies to all Lyra documentation and future implementation unless a more specific standard supersedes it.

## Standard

* Reference stable requirement IDs for requirement-impacting changes.
* Preserve Lyra's stateless, contract-driven, protocol-agnostic boundary.
* Keep consumer business logic and business state outside Lyra.
* Update related specifications, ADRs, contracts, schemas, examples, and traceability notes together.
* Prefer explicit ownership, lifecycle, validation, compatibility, and operational guidance.

## Review Checklist

- Requirement IDs are present where needed.
- Affected documents are cross-referenced.
- Compatibility and security impacts are stated.
- The change is understandable without external chat history.
