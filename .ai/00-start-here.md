# 00 Start Here

## Maturity Metadata

**Status:** Approved.

**Intended Use:** Authoritative AI-agent operating context; safe for repository navigation and contribution workflow decisions.


## Purpose

This is the first AI-specific document every AI coding agent must read. It explains where to find authoritative context and how to avoid unsafe assumptions.

## Repository Purpose

Lyra is an AI Voice Orchestration Platform. It coordinates conversations and invokes consumer-owned capabilities through explicit contracts while consumer applications remain systems of record for business state and business rules.

## Mandatory Reading Order

1. [`PROJECT.md`](../PROJECT.md)
2. [`README.md`](../README.md)
3. [`.ai/`](./00-start-here.md)
4. [`docs/specifications/`](../docs/specifications/01-introduction.md)
5. [`docs/architecture/`](../docs/architecture/system-overview.md)
6. [`docs/contracts/`](../docs/contracts/README.md)
7. [`docs/decisions/`](../docs/decisions/ADR-0001.md)
8. [`examples/`](../examples/restaurant/README.md)
9. Code or implementation directories only after the documents above are understood.

## Mandatory Rules

* Treat numbered `.ai/` files as authoritative; unnumbered `.ai/` files are compatibility redirects only.
* Do not assume previous conversation history.
* Do not implement application features unless explicitly asked.
* Reference requirement IDs for requirement-impacting work.
* Update documentation before implementation.
* Preserve Lyra's stateless, contract-driven, protocol-agnostic architecture.

## Navigation Guide

Use the canonical numbered files only: `01-product-summary.md` for product context, `02-core-principles.md` for non-negotiable rules, `03-domain-model.md` for terminology, `04-architecture-summary.md` for boundaries, `05-requirements-index.md` for IDs, `06-coding-standards.md` for implementation standards, `07-prompt-guidelines.md` for AI prompt guidance, `08-common-mistakes.md` for pitfalls, and `09-agent-checklist.md` before making changes.
