# Quality Gates

## Maturity Metadata

**Status:** Approved.

**Intended Use:** Authoritative specification of the mandatory quality gates, artifacts, checks, approval roles, and exit criteria required for lifecycle transitions.

## Overview

Quality Gates are formal checkpoints that must be satisfied before a feature, schema change, or architectural decision can advance to the next lifecycle stage. Bypassing any quality gate is not permitted.

---

## The Quality Gate Sequence

```
[Product Gate] → [Requirements Gate] → [Architecture Gate] → [Implementation Gate] → [Testing Gate] → [Documentation Gate] → [Release Gate]
```

---

## 1. Product Gate (Idea to Discovery)
* **Required Artifacts:** Feature Proposal Ticket, Draft Product Vision doc.
* **Review Checklist:**
  - Does this feature align with Lyra's core mission?
  - Does it provide defined business or operational value?
* **Approval Authority:** Product Owner (`@Sani192`).
* **Failure Criteria:** The proposal introduces domain-specific consumer business logic, or fails to define target users.
* **Exit Criteria:** Approved Product Vision doc saved under `docs/vision/`.

## 2. Requirements Gate (Discovery to Specification)
* **Required Artifacts:** Final Product Vision doc, Numbered Specifications (`docs/specifications/`).
* **Review Checklist:**
  - Are requirements written with stable, unique IDs (functional/non-functional/security)?
  - Are acceptance criteria testable and unambiguous?
* **Approval Authority:** Product Owner (`@Sani192`) and PM (`@PM_Lyra`).
* **Failure Criteria:** Requirements lack clear ownership, priorities, or acceptance criteria.
* **Exit Criteria:** Requirements approved, indexed in `.ai/05-requirements-index.md`, and marked `Approved` in the traceability matrix.

## 3. Architecture Gate (Specification to Ready-for-Dev)
* **Required Artifacts:** System Architecture Updates, Draft ADRs, JSON Schemas, API Contracts.
* **Review Checklist:**
  - Does the design preserve statelessness and tenant isolation?
  - Have tradeoffs and alternatives been assessed and documented?
  - Are JSON schemas updated and lint-checked?
* **Approval Authority:** Architecture Owner (`@Sani192`) and Architectural Board (`@Arch_Guild`).
* **Failure Criteria:** Design introduces database or communication locks, bypasses schema validation, or leaves architectural tradeoffs undocumented.
* **Exit Criteria:** Approved ADRs in `docs/decisions/` and schemas updated. Satisfies the **Definition of Ready** (DoR).

## 4. Implementation Gate (Ready-for-Dev to Coding Complete)
* **Required Artifacts:** Source Code changes in feature branch, inline code documentation, trace-linked comments.
* **Review Checklist:**
  - Does the implementation trace 100% to approved Requirement IDs?
  - Does it follow ruff/toml style guides and naming conventions?
  - Is there zero hardcoded consumer-specific behavior?
* **Approval Authority:** Lead Backend/Frontend/SDK Maintainer.
* **Failure Criteria:** The code implements undocumented features, breaks coding standards, or leaks consumer domains.
* **Exit Criteria:** Merged branch compiles successfully, and code passes static analysis.

## 5. Testing Gate (Coding Complete to Validated)
* **Required Artifacts:** Automated test suites, test logs, coverage reports, contract validation results, security matrix checks.
* **Review Checklist:**
  - Do all unit, integration, contract, security, and conversation tests pass?
  - Is code coverage >= 85%?
  - Are test assertions linked to Requirement IDs?
* **Approval Authority:** QA Lead and Component Maintainers.
* **Failure Criteria:** Test suite failure, coverage dropping below threshold, or missing security isolation validation.
* **Exit Criteria:** 100% test success rate, verified security matrix, and testing evidence recorded in the PR.

## 6. Documentation Gate (Validated to Done)
* **Required Artifacts:** Updated markdown documents, updated `CHANGELOG.md`, updated Traceability Matrix.
* **Review Checklist:**
  - Are all affected specifications, ADRs, schemas, and READMEs updated to match the code?
  - Do all markdown files pass link verification?
* **Approval Authority:** Tech Writer / Docs Lead (`@Docs_Lead`).
* **Failure Criteria:** Outdated examples, broken markdown links, or undocumented public API parameters.
* **Exit Criteria:** Documentation review approved. Satisfies the **Definition of Done** (DoD).

## 7. Release Gate (Done to Released)
* **Required Artifacts:** Release Candidate build, Release Checklist, Rollback Plan, Migration down-scripts, Release notes.
* **Review Checklist:**
  - Has the release checklist been completed?
  - Are rollback and database migrations tested in staging?
* **Approval Authority:** Release Owner (`@Sani192`) and Security Auditor (`@Sec_Auditor`).
* **Failure Criteria:** Rollback plan failure, security scanner alerts, or incomplete migration scripts.
* **Exit Criteria:** Release version tagged (SemVer), CHANGELOG published, and post-release validation passed in production.
