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
| Governance Framework | `docs/governance/*.md`, `docs/governance/README.md` | Approved | Authoritative processes, workflows, and roles for repository management. |
| Documentation standards | `docs/engineering/documentation-standards.md` | Approved | Authoritative status and intended-use rules. |
| Review process | `docs/engineering/review-process.md` | Approved | Authoritative checklists. |
| Specific standards | `docs/engineering/*.md` | Approved | Consolidated engineering, style, naming, branching, and commit guidelines. |
| Architecture decisions | `docs/decisions/ADR-0001.md` through `docs/decisions/ADR-0006.md` | Approved | Accepted ADRs are safe within their documented scope. |
| ADR creation | `docs/decisions/ADR-template.md` | Implementation Ready | Safe template for new ADRs. |
| Core architecture | `system-overview.md`, `component-architecture.md`, `conversation-lifecycle.md`, `capability-invocation.md`, `caching.md`, `deployment-architecture.md`, `event-architecture.md`, `integration-layer.md`, `multi-tenancy.md`, `scalability.md`, `security-architecture.md`, `storage-strategy.md`, `voice-pipeline.md` | Approved | Independent, production-grade architectural design specifications. |
| JSON Schemas | `schemas/*.schema.json`, `schemas/README.md` | Approved | Machine-readable validation rules. |
| Domain examples | `examples/*/*.md`, `examples/*/expected.json` | Approved | Realistic integration flows and sample payloads. |
| Playbooks | `docs/playbooks/*.md` | Approved | Scenario-specific AI execution flows. |
| Glossary | `docs/glossary/README.md` | Approved | Definitive terminology index. |
| AI Knowledge Center | `.ai/*.md` | Approved | Safe for AI-agent workflow, repository navigation, and contribution process decisions. |

## Not Safe as Standalone Implementation Authority Yet

| Area | Documents | Current Status | Intended Use |
| --- | --- | --- | --- |
| Specifications | `docs/specifications/*.md` | Draft | Product and platform planning; promote before implementation. |

## Maintenance

Update this index whenever a major documentation file is added, removed, promoted, deprecated, or superseded. The status listed here must match the status declared in the document itself.
