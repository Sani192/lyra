# Testing Strategy

## Maturity Metadata

**Status:** Approved.

**Intended Use:** Authoritative testing framework, coverage rules, and test verification standards for Lyra developers and AI agents.

## Purpose

Define the testing methodology, validation tools, and verification gates required to maintain the stability, security, and contract compliance of the Lyra platform.

## Scope

Applies to all verification activities, automated tests, contract checks, and manual review records.

## Testing Levels

1. **Unit Testing:**
   - **Purpose:** Validate individual functions, modules, and component behaviors in isolation.
   - **Tooling:** Use `pytest` for Python backend testing.
   - **Expectation:** Mock all external network, database, and system-level dependencies. 100% logic coverage is preferred for core orchestration functions.

2. **Schema & Contract Testing:**
   - **Purpose:** Validate that registered consumer contracts and JSON schemas are structurally valid and that Lyra's output messages conform to these schemas.
   - **Tooling:** Automated JSON Schema validator checking all payloads in test fixtures against the schemas under `schemas/`.
   - **Expectation:** Both positive and negative test cases verifying validation failure handling.

3. **Integration Testing:**
   - **Purpose:** Verify end-to-end communication between the Conversation Engine, AI Agent Layer, Capability Registry, and Protocol adapters using mock consumer APIs.
   - **Tooling:** Fast, in-memory integration mocks or local integration servers.
   - **Expectation:** Test complete conversation playbooks, turning intent resolution, slot filling, and error recovery.

4. **Security & Isolation Testing:**
   - **Purpose:** Verify tenant isolation, credential protection, and PII redaction.
   - **Expectation:** Tests must assert that tenant data is never leaked or mixed across session boundaries.

## Review Checklist

- [ ] All new functions have accompanying unit tests in the appropriate `tests/` directory.
- [ ] Schema validation tests cover both positive and negative cases.
- [ ] No database or external API dependencies are unmocked in unit tests.
- [ ] Tenant isolation test cases are executed and pass.
- [ ] Coverage requirements meet the defined standards.
