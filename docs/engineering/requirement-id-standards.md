# Requirement Id Standards

## Maturity Metadata

**Status:** Approved.

**Intended Use:** Standard conventions for generating, tracking, and allocating requirement IDs.

## Purpose

Define the format, categories, and numbering conventions for requirement IDs to ensure a standardized traceability path across specifications, PRs, and code tests.

## Requirement ID Format

Requirement IDs must use the following pattern:

```
LYRA-<CATEGORY>-<NUMBER>
```

### 1. Categories

- `FR`: Functional Requirements (e.g., `LYRA-FR-001`).
- `NFR`: Non-Functional Requirements (e.g., `LYRA-NFR-001`).
- `SEC`: Security and Privacy Isolation Requirements (e.g., `LYRA-SEC-001`).
- `CIF`: Capability Intelligence Framework Requirements (e.g., `LYRA-CIF-001`).
- `API`: API and Integration Protocol Requirements (e.g., `LYRA-API-001`).
- `UI`: Front-end Dashboard and Interface Requirements (e.g., `LYRA-UI-001`).
- `OBS`: Logging, Tracing, and Audit Observability Requirements (e.g., `LYRA-OBS-001`).
- `DEP`: Platform Deployment and CI/CD Requirements (e.g., `LYRA-DEP-001`).

### 2. Numbering

Numbers must be three digits, starting from `001` within each category. Once assigned, a requirement ID is stable and must never be changed, recycled, or reassigned, even if the requirement is deprecated.

## Review Checklist

- [ ] New requirements use the standard `LYRA-<CATEGORY>-<NUMBER>` format.
- [ ] IDs are sequential within each category.
- [ ] No requirement IDs are reused or reassigned from deprecated requirements.
