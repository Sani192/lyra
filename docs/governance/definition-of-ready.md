# Definition of Ready (DoR)

## Maturity Metadata

**Status:** Approved.

**Intended Use:** Authoritative checklist defining the criteria that must be satisfied before any feature or change is approved for implementation.

## Overview

The Definition of Ready (DoR) is the quality gate that controls entry into the Implementation phase. Its purpose is to ensure that developers (human and AI) have complete, unambiguous, and approved requirements and designs before writing code. This eliminates developer guesswork, prevents architectural drift, and avoids wasting engineering resources.

---

## The Mandatory Readiness Checklist

A feature is considered **Ready** for implementation only when the following seven criteria are fully satisfied and recorded:

### 1. Requirements Approved
* **Expectation:** The functional, non-functional, or security requirements are documented in `docs/specifications/`, indexed in `.ai/05-requirements-index.md`, and marked as `Approved` or `Implementation Ready`.
* **Verification:** PR approvals from the Product Owner (`@Sani192`) and PM (`@PM_Lyra`) are recorded.

### 2. Architecture Approved
* **Expectation:** The component designs, data flows, and state machines are finalized. If the change is Architecture-changing, an ADR must be written and approved.
* **Verification:** Approved ADR (with status `Accepted` or `Implementation Ready`) is merged in `docs/decisions/`.

### 3. Dependencies Identified
* **Expectation:** All internal module dependencies, external platform APIs, and database migrations are identified, documented, and checked for compatibility.
* **Verification:** The "Dependencies" field in the requirement and the ADR is fully populated (not marked "TBD" or "None" if dependencies exist).

### 4. Acceptance Criteria Defined
* **Expectation:** Each requirement has clear, testable, and unambiguous acceptance criteria.
* **Verification:** Acceptance criteria are written in the specification file in a verifiable format (e.g., Gherkin-style Given-When-Then or explicit check items).

### 5. Contracts and Schemas Updated
* **Expectation:** If the change affects public APIs, event signatures, or component boundaries, the matching JSON schemas and contract guides are updated.
* **Verification:** JSON schema files in `schemas/` are updated, and validation scripts confirm the changes are syntactically correct and backward compatible.

### 6. Risks Documented
* **Expectation:** Technical, operational, security, and integration risks have been explicitly evaluated.
* **Verification:** The "Risks" section of the vision, specification, or ADR is complete, and mitigation plans are defined.

### 7. Documentation Updated
* **Expectation:** The documentation files reflecting the target state of the feature are written and checked into version control.
* **Verification:** Specifications, architecture docs, schemas, and examples are updated in draft/review status in the repository.

---

## Artifact-Specific Readiness Checklists

In addition to this global DoR, contributors must consult and satisfy the artifact-specific checklists defined in [docs/engineering/review-process.md](file:///Users/anonymous/Documents/Java/Workspaces/Python/lyra/docs/engineering/review-process.md#L37). Checklists are provided for:
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
