# Implementation Process

## Maturity Metadata

**Status:** Approved.

**Intended Use:** Authoritative standard outlining the mandatory research, planning, and design steps that must occur before any code is modified.

## Overview

The Lyra implementation process is designed to ensure code changes match the architectural direction and do not introduce undocumented behavior or consumer-specific logic. Coding is the *last* step in the implementation flow, not the first.

---

## Pre-Implementation Research Checklist

Before opening an IDE or writing a line of code, every contributor (human and AI coding agent) must complete the following nine research steps:

### 1. Read `PROJECT.md`
Verify the core mission, boundaries, design principles, and maturity model. Ensure the proposed change aligns with these rules.

### 2. Read Relevant Specifications
Examine the functional and non-functional requirement specs in `docs/specifications/` to understand the target behavior and acceptance criteria.

### 3. Read Related ADRs
Review the decisions recorded in `docs/decisions/` to understand existing architectural constraints, tradeoffs made, and lessons learned.

### 4. Read Affected Contracts
Inspect any protocol or capability contracts in `docs/contracts/` or `docs/api/` that govern interaction boundaries.

### 5. Read Associated Schemas
Review the JSON schemas in `schemas/` to ensure your data shapes comply with established formats.

### 6. Read Playbooks
Read scenario-specific execution guides and instructions in `docs/playbooks/` and `.ai/` to ensure process compliance.

### 7. Identify Impacted Requirements
Look up the requirement IDs in `.ai/05-requirements-index.md` or `docs/specifications/` and ensure your change maps to active, approved requirements.

### 8. Review Similar Examples
Review existing implementations in `backend/`, `frontend/`, or `sdk/`, and sample integrations under `examples/` to match coding patterns and styles.

### 9. Construct and Document the Plan
Formulate a clear plan detailing:
* Which files will be modified or created.
* What tests will validate the code.
* What documentation or schemas must be updated.
* If a new ADR is required.

---

## Coding Rules

Once research and planning are complete, coding may begin. The following rules are non-negotiable:

* **No Undocumented Behavior:** Do not add features, endpoints, config flags, or behavior that is not documented in the approved specifications.
* **No Consumer Logic Leaks:** Never hardcode logic, routing rules, payment processes, or domain rules that belong in consumer applications.
* **Preserve Statelessness:** Ensure your components do not store conversational or business state in-memory or on-disk in an unmanaged fashion.
* **Comply with Coding Standards:** Follow language-specific linting, formatting, naming conventions, and style rules in [coding-standards.md](file:///Users/anonymous/Documents/Java/Workspaces/Python/lyra/docs/engineering/coding-standards.md).
* **Write Tests Concurrently:** Do not write code and defer tests for later. Tests must be written alongside code changes.
