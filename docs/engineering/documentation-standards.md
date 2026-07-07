# Documentation Standards

## Maturity Metadata

**Status:** Approved.

**Intended Use:** Authoritative documentation standard for repository documentation structure, status metadata, review expectations, and implementation-decision safety.

## Purpose

Documentation standards require purpose, scope, definitions, requirements, acceptance criteria, examples, references, status, revision history, open questions, and related ADRs for specification chapters.

## Scope

Applies to all Lyra documentation and future implementation unless a more specific standard supersedes it.

## Repository Maturity Model

Every major documentation file in `docs/specifications/`, `docs/architecture/`, `docs/decisions/`, `schemas/`, `examples/`, and `.ai/` must declare its maturity status and intended use. This metadata tells contributors and AI agents whether a document can safely guide implementation decisions.

| Status | Definition | Required Action Before Implementation Use |
| --- | --- | --- |
| `Placeholder` | A reserved location or intentionally incomplete outline. | Replace with reviewed content or cite an approved source. |
| `Draft` | Early content that may be incomplete, unvalidated, or missing traceability. | Promote through review before relying on it. |
| `Review Ready` | Complete enough for formal review but not yet accepted. | Complete review and resolve findings. |
| `Approved` | Accepted as authoritative for the stated scope. | May be used for implementation decisions within scope. |
| `Implementation Ready` | Approved and detailed enough to drive engineering work, including acceptance criteria, compatibility notes, and traceability. | May be used as primary implementation authority. |
| `Deprecated` | Retained for history but no longer recommended for new work. | Use a current replacement or obtain explicit approval. |
| `Superseded` | Replaced by another document or schema. | Use the named replacement source. |

## Metadata Format

Markdown documents must include this section near the top:

```markdown
## Maturity Metadata

**Status:** Draft.

**Intended Use:** Explain what the document may be used for and whether it is safe for implementation decisions.
```

JSON documents must include explicit status and intended-use metadata. JSON schemas should use `x-documentationStatus` and `x-intendedUse`; JSON examples should use `documentation_status` and `intended_use` unless a narrower schema defines a more specific field.

## Implementation Decision Safety

Only `Approved` and `Implementation Ready` documents are safe standalone sources for implementation decisions. `Review Ready` documents may support planning and review but require an approved companion source before engineering work starts. `Placeholder`, `Draft`, `Deprecated`, and `Superseded` documents are not safe as standalone implementation authority.

## Standard

* Reference stable requirement IDs for requirement-impacting changes.
* Preserve Lyra's stateless, contract-driven, protocol-agnostic boundary.
* Keep consumer business logic and business state outside Lyra.
* Update related specifications, ADRs, contracts, schemas, examples, and traceability notes together.
* Prefer explicit ownership, lifecycle, validation, compatibility, and operational guidance.
* Keep maturity metadata current when content changes or review status changes.
* Update `docs/index.md` when a major document is added, removed, promoted, deprecated, or superseded.

## Review Checklist

- Requirement IDs are present where needed.
- Affected documents are cross-referenced.
- Compatibility and security impacts are stated.
- The change is understandable without external chat history.
- Maturity status and intended use are declared near the top of every affected major document.
- Documents cited for implementation decisions are `Approved` or `Implementation Ready`, or are paired with an approved companion source.
