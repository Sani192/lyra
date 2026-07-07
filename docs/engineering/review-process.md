# Review Process

## Maturity Metadata

**Status:** Approved.

**Intended Use:** Authoritative standard guidelines for pull requests, self-reviews, approval levels, and artifact-specific Definition of Ready/Done gates for Lyra.

## Purpose

Establish clear expectations for code and documentation reviews, pull request requirements, and specific checklists to verify requirement traceability, architectural boundary preservation, security/privacy impact, and implementation correctness before changes are merged.

## Scope

Applies to all pull requests, branches, and merges in the Lyra repository.

## Pull Request Guidelines

1. **Self-Review:** Before submitting a PR, the author must review their own diff to ensure it contains no debug comments, print statements, or formatting violations.
2. **Branch Isolation:** Changes must be developed in feature branches named according to the branching strategy and never committed directly to `main`.
3. **Linear History:** Feature branches must be rebased against the latest `main` before submission. All merges to `main` must use squash-merging.
4. **Traceability in Descriptions:** Every pull request description must list the targeted requirement IDs.
5. **Review Roles:** The PR must be approved by the designated role owners (e.g., Product Owner, Architecture Owner) as defined in the governance model.

## General Review Checklist

- [ ] All code changes trace directly back to active requirement IDs.
- [ ] Pull request description explicitly lists the targeted requirement IDs.
- [ ] Variable and function names follow PascalCase / snake_case rules.
- [ ] Line lengths do not exceed 100 characters.
- [ ] Imports are sorted and grouped correctly.
- [ ] Comments are up to date and describe implementation rationale.
- [ ] Affected documents are cross-referenced and markdown links are valid.
- [ ] Compatibility, migration, and security impacts are explicitly stated.
- [ ] The change is understandable without external chat history.

## Artifact-Specific Definition of Ready and Definition of Done

Use these checklists in addition to the repository-wide Definition of Ready and Definition of Done in `PROJECT.md`. "Ready" evidence should exist before implementation starts. "Done" evidence must be present in the pull request, commit, or review record before merge.

### 1. Requirement Changes

**Definition of Ready**

- **Required documentation:** Identify the affected specification files, current maturity status, requirement IDs to add/change/deprecate, acceptance criteria, user/operator impact, and any affected `.ai/` readiness guidance.
- **Tests:** Define the expected validation strategy for each changed acceptance criterion, including unit, integration, contract, documentation, or manual review checks as applicable.
- **Traceability:** Map each requirement ID to affected architecture, schemas/contracts, implementation areas, examples, tests, and documentation indexes.
- **Compatibility notes:** State whether behavior, public API expectations, data retention, observability, security posture, or migration promises change.
- **Review evidence:** Name the required product/specification owner, engineering reviewer when implementation impact exists, and any architecture, API, compatibility, or security reviewers required by the change.

**Definition of Done**

- **Required documentation:** Updated specifications include stable requirement IDs, maturity metadata, acceptance criteria, and cross-links to dependent artifacts.
- **Tests:** Planned validation is implemented or explicitly recorded as not applicable with reviewer agreement.
- **Traceability:** Requirement indexes and traceability records connect the requirement to architecture, contracts, implementation, tests, examples, and docs.
- **Compatibility notes:** Compatibility, migration, deprecation, or non-impact rationale is documented in the affected spec and review notes.
- **Review evidence:** Review comments or approvals show requirement-owner acceptance and confirmation that downstream artifact updates are complete or intentionally deferred with tracked follow-up.

### 2. Architecture Changes

**Definition of Ready**

- **Required documentation:** Identify affected architecture documents, component boundaries, data ownership, lifecycle, protocol, deployment, observability, and operational responsibilities.
- **Tests:** Define validation for architectural behavior, including integration tests, failure-mode tests, scalability checks, contract validation, or architecture review walkthroughs.
- **Traceability:** Link the proposed architecture change to requirement IDs, existing or planned ADRs, schemas/contracts, examples, implementation areas, and operational docs.
- **Compatibility notes:** State impact on existing deployments, protocols, persistence, public APIs, tenant isolation, observability, and migration/rollback paths.
- **Review evidence:** Name the architecture owner, affected component maintainers, and security/compatibility reviewers when boundaries, data flow, or external behavior change.

**Definition of Done**

- **Required documentation:** Architecture docs and any required ADRs are updated with diagrams or prose sufficient to explain responsibilities, boundaries, and tradeoffs.
- **Tests:** Relevant architectural validation, integration checks, or documented review walkthroughs are complete and recorded.
- **Traceability:** Requirement-to-architecture-to-implementation/test links are updated in traceability materials.
- **Compatibility notes:** Migration, rollout, rollback, observability, and operational impacts are documented or explicitly marked not applicable.
- **Review evidence:** Architecture approval and affected maintainer review are recorded, with open risks tracked outside the merge path.

### 3. ADRs

**Definition of Ready**

- **Required documentation:** Identify the decision question, status, context, options considered, affected requirements, affected architecture docs, and superseded or related ADRs.
- **Tests:** Define what evidence will validate the decision, such as prototypes, benchmarks, threat-model notes, contract checks, implementation tests, or review-only rationale.
- **Traceability:** Link the ADR to requirement IDs, architecture sections, contracts/schemas, implementation areas, examples, and follow-up work.
- **Compatibility notes:** State the decision's impact on existing behavior, migration, deprecation, vendor/protocol lock-in, and rollback feasibility.
- **Review evidence:** Identify the architecture owner/technical lead, affected maintainers, and product, security, API, or compatibility reviewers as needed.

**Definition of Done**

- **Required documentation:** ADR status, context, decision, consequences, alternatives, and links to related/superseded decisions are complete.
- **Tests:** Supporting evidence is linked or summarized, and any deferred validation has explicit owner and follow-up.
- **Traceability:** Traceability materials and affected docs cite the ADR as the architectural authority.
- **Compatibility notes:** Compatibility and migration consequences are recorded in the ADR and any affected standards/specs.
- **Review evidence:** Required decision approvers accepted the ADR, and unresolved objections are captured as risks or follow-up decisions.

### 4. Schema Changes

**Definition of Ready**

- **Required documentation:** Identify schemas, generated artifacts, validation rules, examples, contract guidance, and documentation that must change.
- **Tests:** Define schema validation, negative/positive fixtures, compatibility checks, generated-code checks, and contract/example validation required for the change.
- **Traceability:** Link schema fields and constraints to requirement IDs, contract docs, architecture expectations, examples, implementation validators, and tests.
- **Compatibility notes:** Classify additive, backward-compatible, breaking, deprecated, or migration-required changes; state versioning and rollout expectations.
- **Review evidence:** Identify schema maintainer, contract/API owner, compatibility reviewer, and security reviewer if data sensitivity or tenant isolation is affected.

**Definition of Done**

- **Required documentation:** Schemas, schema metadata, contract docs, examples, and generated artifacts are updated consistently.
- **Tests:** Schema validation and compatibility checks pass with positive and negative coverage for changed fields or constraints.
- **Traceability:** Requirements, schema paths, examples, validators, and tests are cross-linked.
- **Compatibility notes:** Versioning, migration, deprecation, and consumer impact notes are documented.
- **Review evidence:** Schema/API/compatibility approvals are recorded, including explicit acceptance of any breaking-change plan.

### 5. Contract Changes

**Definition of Ready**

- **Required documentation:** Identify affected contract guidance, protocol mappings, request/response shapes, error semantics, capability metadata, schemas, and consumer-facing examples.
- **Tests:** Define contract tests, fixture validation, protocol adapter checks, backward/forward compatibility checks, and error-case tests.
- **Traceability:** Link contract behavior to requirement IDs, schemas, architecture docs, examples/playbooks, SDK surfaces, backend/frontend behavior, and tests.
- **Compatibility notes:** State public API impact, versioning, deprecation, migration guidance, consumer notification needs, and fallback behavior.
- **Review evidence:** Identify API/contract owner, compatibility reviewer, affected SDK/integration maintainer, documentation reviewer, and security reviewer for sensitive data or authorization changes.

**Definition of Done**

- **Required documentation:** Contract docs, schemas, examples, SDK notes, and protocol-specific guidance are updated together.
- **Tests:** Contract, adapter, fixture, and compatibility tests pass or documented non-applicability is approved.
- **Traceability:** Requirement-to-contract-to-schema-to-implementation/test links are complete.
- **Compatibility notes:** Consumer impact, versioning, deprecation, and migration notes are documented where reviewers can find them.
- **Review evidence:** API/contract, compatibility, documentation, and affected maintainer approvals are recorded.

### 6. Example/Playbook Changes

**Definition of Ready**

- **Required documentation:** Identify examples, playbooks, fixtures, narratives, expected JSON, failure cases, and boundary statements that need updates.
- **Tests:** Define linting, schema validation, contract validation, snapshot checks, or manual walkthroughs for the changed examples.
- **Traceability:** Link examples to requirement IDs, contract/schema docs, architecture boundaries, implementation behavior, and tests they illustrate.
- **Compatibility notes:** State whether the example demonstrates new behavior, removes old behavior, changes public guidance, or is non-normative clarification only.
- **Review evidence:** Identify documentation reviewer, contract/schema reviewer when shapes change, and product or security reviewer when examples affect user expectations or sensitive flows.

**Definition of Done**

- **Required documentation:** Examples and playbooks are accurate, boundary-safe, and updated with expected inputs, outputs, error cases, and explanatory context.
- **Tests:** Example validation, schema checks, or documented manual walkthroughs are complete.
- **Traceability:** Examples cite or are linked from relevant requirements, contracts, schemas, and tests.
- **Compatibility notes:** Review notes explain whether the change is normative, illustrative, migration-related, or compatibility-neutral.
- **Review evidence:** Documentation and affected artifact reviewers confirm that examples do not imply hidden Lyra business logic or unsupported behavior.

### 7. Backend Implementation

**Definition of Ready**

- **Required documentation:** Identify approved requirements, architecture/ADR authority, backend modules, APIs/contracts, schemas, operational docs, and observability expectations affected.
- **Tests:** Define unit, integration, contract, database/migration, authorization, failure-mode, observability, and regression tests required for the backend change.
- **Traceability:** Link code paths to requirement IDs, architecture docs, contracts/schemas, ADRs, examples, and test cases.
- **Compatibility notes:** State API, persistence, deployment, configuration, migration, performance, rollback, and operator-impact expectations.
- **Review evidence:** Identify backend maintainer, architecture/API/compatibility reviewer as applicable, and security reviewer for authentication, authorization, tenant isolation, data handling, or secrets.

**Definition of Done**

- **Required documentation:** Backend behavior, configuration, operational notes, contracts, schemas, and examples are updated when visible or externally observable.
- **Tests:** Relevant backend tests and checks pass, including contract/security/migration coverage when applicable.
- **Traceability:** Code, tests, and docs cite or can be traced to requirement IDs and architectural authority.
- **Compatibility notes:** Rollout, rollback, migration, deprecation, and operational impact notes are recorded.
- **Review evidence:** Backend maintainer and required specialist approvals are present, with test output and known risks captured.

### 8. Frontend Implementation

**Definition of Ready**

- **Required documentation:** Identify approved UI/product requirements, UX guidance, frontend modules, routes/components, API contracts, accessibility expectations, and user-facing documentation.
- **Tests:** Define component, unit, integration, end-to-end, accessibility, visual regression, contract/mock, and browser compatibility checks as applicable.
- **Traceability:** Link UI behavior to requirement IDs, design/architecture docs, contracts, backend dependencies, examples, and tests.
- **Compatibility notes:** State user-visible behavior changes, browser/support impact, feature-flag or rollout plan, API compatibility, localization/accessibility impact, and rollback path.
- **Review evidence:** Identify frontend maintainer, product/UX reviewer, accessibility reviewer when UI semantics change, API reviewer for contract use, and security reviewer for sensitive data flows.

**Definition of Done**

- **Required documentation:** User-facing docs, UI specs, screenshots or walkthroughs when perceptible, contract usage notes, and accessibility notes are updated.
- **Tests:** Relevant frontend, accessibility, browser, and contract/mock checks pass or documented limitations are approved.
- **Traceability:** UI changes, API dependencies, tests, and docs are linked to requirements.
- **Compatibility notes:** Rollout, feature flags, compatibility, accessibility, and user-impact notes are documented.
- **Review evidence:** Frontend, product/UX, and required specialist approvals are recorded with screenshots or review artifacts when useful.

### 9. SDK Implementation

**Definition of Ready**

- **Required documentation:** Identify SDK package/API surface, supported languages or runtimes, contract/schema authority, generated artifacts, examples, migration guide, and release notes affected.
- **Tests:** Define unit, contract, generated-code, compatibility, sample app, documentation snippet, package/build, and versioning checks.
- **Traceability:** Link SDK APIs to requirement IDs, public contracts, schemas, examples, backend behavior, and tests.
- **Compatibility notes:** State semantic versioning impact, public API additions/removals, deprecations, runtime support, migration needs, and consumer rollout expectations.
- **Review evidence:** Identify SDK maintainer, API/contract owner, compatibility reviewer, documentation reviewer, and security reviewer for credential/auth or sensitive data handling.

**Definition of Done**

- **Required documentation:** SDK docs, API references, examples, migration notes, generated files, and release notes are updated consistently.
- **Tests:** SDK tests, contract compatibility, package/build, and sample validation checks pass.
- **Traceability:** SDK APIs and tests map back to requirements, contracts, schemas, and backend behavior.
- **Compatibility notes:** Versioning, deprecation, migration, runtime support, and release notes are complete.
- **Review evidence:** SDK/API/compatibility approvals are recorded with package or generated-artifact evidence.

### 10. Security-Sensitive Changes

**Definition of Ready**

- **Required documentation:** Identify affected security requirements, threat model, data classification, authentication/authorization behavior, tenant isolation, secrets handling, audit logging, privacy, retention, and incident-response docs.
- **Tests:** Define security unit/integration tests, authorization matrix checks, tenant-isolation tests, negative tests, dependency scans, secret scans, audit-log checks, and manual review steps.
- **Traceability:** Link security controls to requirement IDs, architecture/security docs, ADRs, schemas/contracts, implementation areas, tests, and operational evidence.
- **Compatibility notes:** State impact on existing credentials, permissions, data access, audit events, privacy guarantees, compliance posture, migration/rotation needs, and rollback constraints.
- **Review evidence:** Identify security reviewer, architecture owner when boundaries change, affected component maintainer, API/compatibility reviewer for public behavior, and privacy/compliance reviewer when regulated data is involved.

**Definition of Done**

- **Required documentation:** Security, privacy, operational, contract/schema, and user/admin documentation is updated to describe the final control behavior.
- **Tests:** Required security, isolation, negative, scan, and audit checks pass or approved compensating evidence is recorded.
- **Traceability:** Security requirements, controls, code/tests, and operational evidence are cross-linked.
- **Compatibility notes:** Permission changes, credential rotation, audit changes, migration/rollback, and compliance impact are documented.
- **Review evidence:** Security approval and affected maintainer approvals are recorded, with residual risks explicitly accepted or tracked before merge.
