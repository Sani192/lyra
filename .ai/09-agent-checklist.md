# 09 Agent Checklist

## Maturity Metadata

**Status:** Approved.

**Intended Use:** Authoritative checklist for automated linter gates and manual verification during developer pull requests.

## Purpose

Provide a step-by-step checklist that AI agents and human contributors must follow and output in their pull requests or commit logs before any code or documentation is integrated into `main`.

## Verification Checklist

### 1. Pre-Implementation Gates
- [ ] Read and verified alignment with [PROJECT.md](../PROJECT.md).
- [ ] Located and read the authoritative specification under `docs/specifications/`.
- [ ] Identified the stable requirement IDs (e.g., `LYRA-FR-001`) driving the change.
- [ ] Checked for relevant architectural decisions (ADRs) under `docs/decisions/`.

### 2. Design and Schema Compliance
- [ ] Verified that no consumer-specific business logic is introduced.
- [ ] Verified that no system-of-record state storage is added.
- [ ] Updated or validated the corresponding JSON schema files under `schemas/`.
- [ ] Confirmed that all API endpoints conform to naming standards.

### 3. Implementation and Quality Gates
- [ ] Formatted the code using the configured formatting tools (`black`/`ruff`).
- [ ] Ran linting checks (`ruff`/`flake8`) and resolved all errors.
- [ ] Ensured that all public functions, classes, and modules have PEP-257 docstrings.
- [ ] Verified static type hints pass cleanly (`mypy`).

### 4. Post-Implementation Traceability
- [ ] Updated the traceability matrix under `docs/traceability/README.md`.
- [ ] Updated the documentation index under `docs/index.md` if new files were added.
- [ ] Referenced the requirement IDs in commit messages and the pull request description.
