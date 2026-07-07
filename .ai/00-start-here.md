# 00 Start Here

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

* Do not assume previous conversation history.
* Do not implement application features unless explicitly asked.
* Reference requirement IDs for requirement-impacting work.
* Update documentation before implementation.
* Preserve Lyra's stateless, contract-driven, protocol-agnostic architecture.

## Navigation Guide

Use `01-product-summary.md` for product context, `02-core-principles.md` for non-negotiable rules, `03-domain-model.md` for terminology, `04-architecture-summary.md` for boundaries, `05-requirements-index.md` for IDs, and `09-agent-checklist.md` before making changes.
