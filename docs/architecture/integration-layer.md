# Integration Layer

## Maturity Metadata

**Status:** Draft.

**Intended Use:** Planning and review guidance; do not treat as implementation-ready unless the status is promoted.


## Purpose

Describe Lyra's integration layer in a way that supports future implementation without committing to premature code-level choices.

## Design Goals

* Preserve Lyra's stateless relationship to consumer business domains.
* Keep conversation orchestration separate from protocol adapters.
* Make capability invocation observable, auditable, and contract-driven.
* Support multi-tenant operation and least-privilege access.

## Future Diagrams Placeholder

Diagrams will be added under `docs/diagrams/` after the relevant specification and ADRs are approved.

## Architecture Decisions

Relevant decisions include ADR-0001 through ADR-0005. Future changes must add ADRs before implementation.

## Open Questions

* Which operational metrics are required for production readiness?
* What compatibility guarantees apply to contract evolution in this area?
* Which tenant controls must be configurable per environment?

## References

* `PROJECT.md`
* `docs/specifications/`
* `docs/decisions/`
