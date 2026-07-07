# AI Agent Development Workflow

## Maturity Metadata

**Status:** Approved.

**Intended Use:** Authoritative operational workflow, constraints, and requirements governing how AI coding agents plan, implement, review, and document changes in this repository.

## Overview

AI agents are engineering collaborators, not autonomous decision-makers. They must follow a strict, systematic workflow to guarantee architectural boundary compliance, security, and traceability. Bypassing these steps is not permitted.

---

## The AI Agent Development Lifecycle

Every AI coding agent must execute changes in these seven sequential phases:

```
[Phase 1: Understand] → [Phase 2: Context Review] → [Phase 3: Plan] → [Phase 4: Implement] → [Phase 5: Self-Review] → [Phase 6: Verify] → [Phase 7: Doc Update]
```

### Phase 1: Understand the Problem
* Read the user request thoroughly.
* Identify the target user persona and core objectives.
* If requirements are ambiguous, stop and ask the user for clarification.

### Phase 2: Context Review
Before modifying any files, the agent must read the repository context:
1. **Read `PROJECT.md`** to review core design principles and boundaries.
2. **Read relevant specifications** in `docs/specifications/` to check target behavior.
3. **Read related ADRs** in `docs/decisions/` to understand existing architectural constraints.
4. **Identify Requirement IDs** in the requirements index (`.ai/05-requirements-index.md`).
5. **Inspect affected contracts** in `docs/contracts/` or `docs/api/`.
6. **Review JSON schemas** in `schemas/` to understand data structures.
7. **Review similar implementations** in the codebase to align with patterns and styles.

### Phase 3: Plan Changes
* Construct a detailed implementation plan.
* List all target files, scheduled edits, testing strategies, and documentation changes.
* Submit the plan for user review and wait for explicit approval.

### Phase 4: Implement
* Execute the code changes in small, logical steps.
* Maintain all existing comments and docstrings.
* Comply with coding, naming, and style standards.

### Phase 5: Run Self-Review
* Review the git diff of your changes.
* Ensure no debug statements, print logs, or temporary code remains.
* Verify that formatting guidelines are satisfied.

### Phase 6: Verify Requirements
* Run the automated test suite.
* Ensure all unit, integration, and contract tests pass.
* Verify that every changed behavior matches the requirement's acceptance criteria.

### Phase 7: Update Documentation
* Update specifications, architecture docs, schemas, and README files.
* Update the centralized traceability matrix in `docs/traceability/README.md`.
* Promote document maturity status if applicable.

---

## Critical AI Agent Guardrails

AI agents are subject to the following non-negotiable rules:

* **Never Skip Architecture:** Do not bypass ADR processes. If a change affects boundaries, file an ADR draft.
* **Never Invent Undocumented Behavior:** Implement *only* what is described in the approved requirements. Do not add hidden configurations, endpoints, or features.
* **Never Introduce Consumer-Specific Logic:** Keep Lyra protocol-agnostic and business-logic free. All business rules belong in consumer systems.
* **Never Violate Lyra Principles:** Preserve statelessness, contract-driven interfaces, and multi-tenant security boundaries at all times.
