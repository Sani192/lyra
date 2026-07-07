# Testing Process and Evidence Standards

## Maturity Metadata

**Status:** Approved.

**Intended Use:** Authoritative testing standard defining the required testing layers, automated validations, and verification evidence for the Lyra repository.

## Overview

Testing ensures that Lyra operates safely, adheres to contract specifications, and does not regress. We require multi-layered testing for all code changes, with special emphasis on contract validation and conversation simulation.

---

## Testing Levels

Every material code change must satisfy expectations across the following nine testing layers:

### 1. Unit Tests
* **Objective:** Validate individual classes, functions, and logic blocks in isolation.
* **Expectation:** Fast execution, high branch coverage (minimum 85%), mocking external system integrations.

### 2. Integration Tests
* **Objective:** Validate cooperation between internal modules and adapters (e.g., storage adapters, caching, database queries).
* **Expectation:** Uses local dockerized instances or test databases; verifies data mapping and error handling.

### 3. Contract Tests
* **Objective:** Verify that API adapters, events, and capability registry inputs adhere strictly to JSON schemas.
* **Expectation:** Ensures no breaking changes occur to the schemas located in `schemas/`. Run automatically on every commit.

### 4. Regression Tests
* **Objective:** Verify that system updates do not break previously functional behavior.
* **Expectation:** Test suites include historical bug regression tests, explicitly named after the issues they resolved.

### 5. Performance Tests
* **Objective:** Verify response latencies, throughput boundaries, and resource consumption (CPU/Memory).
* **Expectation:** Mandatory for changes to connection handlers, audio streaming codecs, database queries, and caching mechanisms.

### 6. Security Tests
* **Objective:** Validate tenant isolation, authentication controls, and authorization logic.
* **Expectation:** Negative tests attempting to bypass credentials, access cross-tenant data, or inject malicious inputs must pass securely (rejecting unauthorized access).

### 7. Conversation Tests
* **Objective:** Simulate voice/text conversations across multiple turns to verify orchestration state transition.
* **Expectation:** Uses mock channels to run conversation designer playbooks and verify transcript collection, action dispatching, and state resets.

### 8. End-to-End (E2E) Tests
* **Objective:** Validate the complete path from a simulated user call down to mock consumer API invocation and response tracking.
* **Expectation:** Validates deployment readiness in staging environments.

### 9. Acceptance Tests
* **Objective:** Verify that the system delivers the exact behavior described in the requirement's acceptance criteria.
* **Expectation:** Direct alignment with functional requirement specs.

---

## Required Testing Evidence

Before a pull request can be merged, the author (human or AI) must record and attach the following evidence:

### Code Change Evidence Checklist

- [ ] **Test Execution Logs:** Output logs showing 100% test pass rate for the modified modules.
- [ ] **Coverage Reports:** Evidence of satisfying the code coverage thresholds.
- [ ] **Contract Validation Reports:** Outputs from schema linting tools confirming contract compliance.
- [ ] **Performance Benchmarks:** Execution records for performance-sensitive changes.
- [ ] **Security Matrix Verification:** Test results proving that cross-tenant access is securely rejected.
- [ ] **Traceability Tags:** All test cases must contain comments referencing the Requirement IDs they validate (e.g., `# Traces: LYRA-FR-001`).

If testing evidence is missing, the change fails the testing quality gate and must not be merged.
