# Lyra

[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](LICENSE)
[![Python Version](https://img.shields.io/badge/Python-3.11+-blue.svg)](https://www.python.org/downloads/)
[![CI Status](https://img.shields.io/badge/CI-Pending-lightgrey.svg)](#validation)

Lyra is an AI Voice Orchestration Platform for receiving customer conversations, understanding intent, invoking consumer application capabilities through standardized contracts, and coordinating the conversational experience from start to finish.

Lyra does **not** own business state. Consumer applications remain the systems of record for orders, customers, inventory, appointments, payments, loyalty, pricing, policies, and business rules. Lyra owns conversation context, AI orchestration, capability invocation, transcripts, recordings, analytics, events, contracts, and observability.

---

## Architecture Overview

```
              +------------------------------------------+
              |               Client (Voice)             |
              +--------------------+---------------------+
                                   | HTTP/WebSocket
                                   v
              +--------------------+---------------------+
              |           Lyra Protocol Adapters         |
              |             (REST / OpenAPI / MCP)       |
              +--------------------+---------------------+
                                   |
                                   v
  +--------------------------------+--------------------------------+
  |                                                                 |
  |   +--------------------------+     +------------------------+   |
  |   |    Conversation Engine   |     |    Workflow Engine     |   |
  |   |  (Turn taking & Session) |     |  (Playbook Execution)  |   |
  |   +------------+-------------+     +-----------+------------+   |
  |                |                               |                |
  |                +---------------+---------------+                |
  |                                |                                |
  |                                v                                |
  |   +----------------------------+----------------------------+   |
  |   |                     AI Agent Layer                      |   |
  |   |             (Intent & Entity Extraction)                |   |
  |   +----------------------------+----------------------------+   |
  |                                |                                |
  +--------------------------------+--------------------------------+
                                   |
                                   v
              +--------------------+---------------------+
              |             Capability Registry          |
              |            (Contract Validation)         |
              +--------------------+---------------------+
                                   | REST / MCP
                                   v
              +--------------------+---------------------+
              |             Consumer Application         |
              |            (System of Record)            |
              +------------------------------------------+
```

---

## Primary Technology Stack

Lyra is built with modern, production-grade tools:
- **Programming Language:** Python 3.11+ (static typing enforced via `mypy`).
- **Web Framework:** FastAPI for high-performance, asynchronous REST APIs.
- **Data Validation:** Pydantic and JSON Schema (Draft 2020-12) for contract compliance validation.
- **Eventing & Persistence:** PostgreSQL (metadata) and standard S3-compatible object storage (audio recordings and raw transcripts).

---

## Current Repository Status

Lyra is currently in a **documentation-first/bootstrap** state. The repository defines the product boundaries, governance model, requirements, architecture direction, contracts, schemas, and examples that future implementation must follow, but it does not yet contain production runtime components.

The implementation directories (`backend/`, `frontend/`, and `sdk/`) are reserved and document-only. Many specifications, schemas, contracts, examples, and architecture notes are drafts. Check their maturity status using the [Documentation Status Index](./docs/index.md) before making implementation decisions.

Authoritative documents today are:

* `PROJECT.md` for the project constitution, repository boundaries, governance, maturity model, and contribution workflow.
* Numbered `.ai/` documents, especially `.ai/00-start-here.md` and `.ai/10-implementation-readiness.md`, for AI-agent operating guidance.
* Approved ADRs in `docs/decisions/` for accepted architectural decisions.
* Approved or Implementation Ready specifications in `docs/specifications/` when their maturity metadata explicitly grants that authority.

---

## Validation

No repository-wide static-check toolchain is available during bootstrap. Once tooling is introduced, it will automate:
* Markdown formatting, linting, heading structure, and link validation.
* JSON syntax and JSON Schema validation for files in `schemas/` and contract examples.
* Requirement ID format, uniqueness, and traceability validation.
* Static type checking (`mypy`), linting (`ruff`), and code formatting (`black`/`ruff`).

---

## Repository Structure

| Path | Purpose |
| --- | --- |
| `PROJECT.md` | Lyra constitution and mandatory first read for humans and AI agents. |
| `.ai/` | Numbered, canonical AI Knowledge Center documents for AI coding agents. |
| `docs/specifications/` | Numbered product and platform specifications. |
| `docs/architecture/` | Architecture narratives, diagrams, and components descriptions. |
| `docs/decisions/` | Architecture Decision Records. |
| `docs/playbooks/` | Scenario-specific AI orchestration playbooks. |
| `docs/engineering/` | Consolidated engineering and style standards (coding, style, testing, branching, commit, review process). |
| `docs/glossary/` | Centralized terminology definitions. |
| `schemas/` | JSON schemas for contracts, capabilities, events, and workflows. |
| `examples/` | Consumer-domain examples (e.g. restaurant booking). |
| `backend/`, `frontend/`, `sdk/` | Reserved implementation areas; documentation-only at bootstrap. |
| `tools/`, `scripts/` | Reserved operational helper areas for development automation. |

---

## Getting Started

1. Read `PROJECT.md` to understand non-negotiable principles.
2. Read `.ai/00-start-here.md` if you are an AI agent or operating with one; treat the numbered `.ai/` documents as canonical.
3. Review the [Documentation Status Index](./docs/index.md) to check which files are authoritative.
4. Review `docs/specifications/06-functional-requirements.md` and `docs/specifications/07-non-functional-requirements.md` before proposing implementation.
5. Check `docs/decisions/` before changing architecture.
6. Update documentation and requirement references before writing code.

---

## Contribution Guidelines

See `CONTRIBUTING.md` and the standards in `docs/engineering/`. Contributions should be small, reviewable, linked to requirement IDs, and aligned with the product constitution in `PROJECT.md`.
