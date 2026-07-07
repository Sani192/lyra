# Documentation Status Index

## Maturity Metadata

**Status:** Approved.

**Intended Use:** Authoritative index for determining which Lyra documents are safe to use for implementation decisions.

## Purpose

This index summarizes repository documentation maturity so contributors can quickly identify which documents may guide implementation decisions.

## Implementation Decision Rule

Documents with `Approved` or `Implementation Ready` status are safe to use for implementation decisions within their stated scope. Documents with `Placeholder`, `Draft`, `Review Ready`, `Deprecated`, or `Superseded` status are not safe standalone implementation authorities.

## Safe for Implementation Decisions

| Area | Documents | Status | Notes |
| --- | --- | --- | --- |
| Project constitution | `PROJECT.md` | Approved | Mandatory repository policy and maturity model. |
| Documentation standards | `docs/engineering/documentation-standards.md` | Approved | Authoritative status and intended-use rules. |
| Architecture decisions | `docs/decisions/ADR-0001.md` through `docs/decisions/ADR-0005.md` | Approved | Accepted ADRs are safe within their documented scope. |
| ADR creation | `docs/decisions/ADR-template.md` | Implementation Ready | Safe template for new ADRs. |
| AI Knowledge Center | `.ai/*.md` | Approved | Safe for AI-agent workflow, repository navigation, and contribution process decisions. |

## Not Safe as Standalone Implementation Authority Yet

| Area | Documents | Current Status | Intended Use |
| --- | --- | --- | --- |
| Specifications | `docs/specifications/*.md` | Draft | Product and platform planning; promote before implementation. |
| Architecture narratives | `docs/architecture/*.md` | Draft | Architecture planning; pair with approved ADRs before implementation. |
| Schemas | `schemas/*.json`, `schemas/README.md` | Draft | Schema design and validation planning; promote before implementation. |
| Domain examples | `examples/*/*.md`, `examples/*/expected.json` | Draft | Illustrative integration guidance and review examples; not authoritative test data yet. |

## Maintenance

Update this index whenever a major documentation file is added, removed, promoted, deprecated, or superseded. The status listed here must match the status declared in the document itself.
