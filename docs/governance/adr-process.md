# Architecture Decision Record (ADR) Process

## Maturity Metadata

**Status:** Approved.

**Intended Use:** Authoritative standard governing the lifecycle, numbering, format, review, approval, superseding, and retirement of ADRs.

## Overview

Architecture Decision Records (ADRs) document key design decisions, including the context, options considered, selected decision, and consequences. They provide a historical record of architectural evolution and ensure all engineering contributors understand the "why" behind system designs.

---

## 1. When an ADR is Required

An ADR is mandatory for any change that fits the **Architecture-changing** classification. Specifically, an ADR must be created or updated when a change:
* Alters boundaries between Lyra and consumer systems (e.g., capability registry changes, integration layer revisions).
* Introduces, removes, or changes persistent storage, caching mechanisms, or databases.
* Modifies core runtime structures, conversation state machines, or voice orchestration pipelines.
* Changes security models, authentication, authorization, tenant isolation, or encryption protocols.
* Introduces new protocol adapters or public API specifications.
* Adds major third-party library dependencies or frameworks.
* Modifies structural project code organization (e.g., splitting directories or backend modules).

---

## 2. ADR Numbering and Format

* **File Location:** All ADRs must be stored in `docs/decisions/`.
* **Naming Convention:** Files must be named `ADR-####.md` with a zero-padded, four-digit sequence number (e.g., `ADR-0007.md`).
* **Template:** Every ADR must use the structure defined in [ADR-template.md](file:///Users/anonymous/Documents/Java/Workspaces/Python/lyra/docs/decisions/ADR-template.md), which includes:
  * Maturity Metadata block
  * Status (Proposed / Accepted / Superseded / Rejected / Retired)
  * Context
  * Problem Statement
  * Options Considered (with detailed tradeoffs)
  * Decision
  * Consequences (Positive, Negative, Operational)
  * Future Considerations
  * Related Requirements
  * Affected Documents

---

## 3. Review and Approval Process

1. **Drafting:** The author creates a new branch, files a draft ADR with status `Proposed`, and links the related Requirement IDs.
2. **Review:** The pull request is shared with the Architectural Board (`@Arch_Guild`), the Architecture Owner (`@Sani192`), and impacted component maintainers. Feedback is gathered in the PR comments.
3. **Refinement:** The author updates the ADR based on feedback.
4. **Approval:** The Architecture Owner (`@Sani192`) approves the PR.
5. **Merging:** Once approved, the ADR status field in the document is updated to `Accepted` (or `Implementation Ready` if it includes complete implementation specs), and the PR is merged into `main`.

---

## 4. Superseding and Retiring ADRs

### Superseding an ADR
When a previous architectural decision is modified, replaced, or updated:
* A new ADR is created describing the new context and decision.
* The new ADR must include a section: **"Supersedes: [ADR-XXXX](file:///Users/anonymous/Documents/Java/Workspaces/Python/lyra/docs/decisions/ADR-XXXX.md)"** and explain the reasons for the change.
* The old ADR's status is updated to `Superseded`.
* The old ADR must include a warning notice at the top:
  > [!WARNING]
  > This ADR has been superseded by [ADR-YYYY](file:///Users/anonymous/Documents/Java/Workspaces/Python/lyra/docs/decisions/ADR-YYYY.md). Do not use this file as an implementation authority.

### Retiring an ADR
When a component or capability is completely removed from the system without a replacement:
* The corresponding ADR's status is updated to `Retired`.
* The retired ADR must include a notice at the top:
  > [!NOTE]
  > This architectural decision was retired on 2026-XX-XX as the associated component was removed.

---

## 5. Cross-References and Maintenance

* **Traceability Linking:** Every ADR must explicitly reference the Requirement IDs it supports in the `Related Requirements` section.
* **Document Linking:** Every ADR must list and link to all affected specifications, schemas, contracts, or standards in the `Affected Documents` section.
* **Index Updates:** The global index in [docs/index.md](file:///Users/anonymous/Documents/Java/Workspaces/Python/lyra/docs/index.md) must be updated in the same PR to reflect the new ADR and its status.
