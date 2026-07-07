# Requirement Traceability

## Maturity Metadata

**Status:** Approved.

**Intended Use:** Authoritative standards for tracking requirements from specification through implementation, testing, and documentation.

## Purpose

Ensure every platform feature is fully justified by and mapped back to approved requirement IDs, enabling comprehensive auditing and verification.

## Scope

Applies to all pull requests, implementation code, tests, schemas, and specifications.

## Traceability Chain Rules

All changes impacting platform behavior must trace through the following chain:

```
Requirement (docs/specifications/)
    ↓
Architecture (docs/architecture/ & docs/decisions/)
    ↓
API / Contract (docs/contracts/ & schemas/)
    ↓
Implementation (backend/, frontend/, sdk/)
    ↓
Tests (test code & verification records)
    ↓
Documentation (docs/index.md & changelog)
```

## Traceability Standards

1. **Requirement IDs:** Every functional, non-functional, security, or observability requirement must be assigned a unique ID conforming to `.ai/05-requirements-index.md`.
2. **Pull Requests:** Every pull request description must list the targeted requirement IDs.
3. **Commit Messages:** Commits affecting behavior must cite the associated requirement ID in the commit body or footer.
4. **Traceability Matrix:** The master traceability matrix in `docs/traceability/README.md` must be updated whenever a requirement is added, modified, or implemented.
5. **Test Cases:** Code tests (unit, integration, and contract tests) must include the requirement ID in their names or annotations.

## Review Checklist

- [ ] All code changes map to at least one active requirement ID.
- [ ] Pull request description explicitly lists the targeted requirement IDs.
- [ ] Traceability matrix in `docs/traceability/README.md` is updated.
- [ ] Verification tests refer to the matching requirement IDs.
