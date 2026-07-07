# Definition of Done (DoD)

## Maturity Metadata

**Status:** Approved.

**Intended Use:** Authoritative checklist defining the criteria that must be satisfied before any change is merged into the `main` branch or released.

## Overview

The Definition of Done (DoD) is the final quality gate that controls entry into the release cycle. Its purpose is to ensure that all deliverables are complete, validated, secure, documented, and traceable. No code change is merged to `main` until it meets the DoD.

---

## The Mandatory Done Checklist

A change is considered **Done** only when the following eight criteria are fully satisfied and verified:

### 1. Implementation Complete
* **Expectation:** All code changes (backend, frontend, SDK) are completed and comply with coding and naming standards.
* **Verification:** Code is checked in, compiles successfully, passes linters (ruff), and has no debug logging or temporary comments.

### 2. Tests Passing
* **Expectation:** The change is validated across all required testing layers: unit, integration, contract, security, regression, performance, and conversation.
* **Verification:** 100% pass rate in the automated test suite; test execution logs are attached.

### 3. Documentation Updated
* **Expectation:** All associated documentation, public APIs, schemas, configurations, and change logs are updated to reflect the final implementation.
* **Verification:** Documents are updated and promoted to `Approved` or `Implementation Ready` in their maturity metadata.

### 4. Requirements Satisfied
* **Expectation:** The code behaves exactly as described in the requirements' acceptance criteria.
* **Verification:** Developer and reviewer verify each acceptance criterion; manual or automated test execution proves compliance.

### 5. Traceability Matrix Updated
* **Expectation:** The traceability chain (Requirement → Architecture → Contract → Code → Test → Documentation) is complete.
* **Verification:** The central traceability log at [traceability README](file:///Users/anonymous/Documents/Java/Workspaces/Python/lyra/docs/traceability/README.md) is updated.

### 6. Architecture Confirmed
* **Expectation:** The architecture is either unchanged (for standard implementations) or updated via an approved ADR.
* **Verification:** No new architectural decisions are made in-code without a matching approved ADR.

### 7. Review Completed
* **Expectation:** Peer reviews are conducted, feedback is addressed, and required approvals are obtained.
* **Verification:** Pull request shows approvals from all required roles (e.g., Product Owner, Architecture Owner, Security Auditor).

### 8. Quality Gates Passed
* **Expectation:** The implementation, testing, and documentation quality gates are satisfied.
* **Verification:** The checklists in [quality-gates.md](file:///Users/anonymous/Documents/Java/Workspaces/Python/lyra/docs/governance/quality-gates.md) are completed and verified by the Release Manager.

---

## Artifact-Specific Done Checklists

In addition to this global DoD, contributors must consult and satisfy the artifact-specific checklists defined in [docs/engineering/review-process.md](file:///Users/anonymous/Documents/Java/Workspaces/Python/lyra/docs/engineering/review-process.md#L37). Checklists are provided for:
* Requirement Changes
* Architecture Changes
* ADRs
* Schema Changes
* Contract Changes
* Example/Playbook Changes
* Backend Implementation
* Frontend Implementation
* SDK Implementation
* Security-Sensitive Changes
