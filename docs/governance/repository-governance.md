# Repository Governance and Ownership Model

## Maturity Metadata

**Status:** Approved.

**Intended Use:** Authoritative specification defining ownership, responsibilities, review structures, and approval authorities for all folders, documents, specifications, and code in the Lyra repository.

## Overview

To maintain the architectural integrity of Lyra, clear boundaries of ownership are established. Every directory, specification, contract schema, and code module has a designated owner who is ultimately responsible for its content, quality, and lifecycle.

---

## 1. Directory and Folder Ownership

Ownership of the repository directory structure is mapped as follows:

| Directory Path | Purpose | Owner / Lead |
| --- | --- | --- |
| `PROJECT.md` | Core Constitution | Architecture Owner (`@Sani192`) |
| `docs/specifications/` | Product requirements | Product Owner (`@Sani192`) |
| `docs/architecture/` | Architecture specs | Architecture Owner (`@Sani192`) |
| `docs/decisions/` | ADRs | Architectural Board (`@Arch_Guild`) |
| `docs/contracts/` & `docs/api/` | Integration contracts | Integration Lead (`@API_Lead`) |
| `schemas/` | JSON schemas | Schema & API Owner (`@Sani192`) |
| `backend/` | Backend orchestration engine | Backend Lead Maintainer |
| `frontend/` | Dashboard interface | Frontend Lead Maintainer |
| `sdk/` | Client SDK libraries | SDK Maintainer |
| `examples/` | Sample configurations | Tech Writer (`@Docs_Lead`) |
| `docs/playbooks/` & `.ai/` | Agent workflows & guides | AI Platform Lead |

---

## 2. Document and Specification Ownership

* **Product Specifications:** Product Owner `@Sani192` owns the requirements definition. Product Manager `@PM_Lyra` manages backlog priorities and drafts specs.
* **Architecture Specifications:** Architecture Owner `@Sani192` owns all files in `docs/architecture/` and component definition maps.
* **API & Contract Specifications:** API Owner `@Sani192` and Integration Lead `@API_Lead` own definitions of request/response structures and edge protocols.
* **Development Standards:** Lead Maintainers own coding, naming, branching, and testing standards under `docs/engineering/`.

---

## 3. Approval and Review Responsibilities

Approval authorities are strictly separated to maintain check-and-balance controls:

* **Specifications Approval:** Changes to requirement files must be approved by `@Sani192` and `@PM_Lyra`.
* **Architecture Approval:** New ADRs or updates to architecture files require sign-off from `@Sani192` and at least one member of `@Arch_Guild`.
* **Schema and Contract Approval:** Changes to files under `schemas/` or `docs/contracts/` require approval from `@Sani192` and `@API_Lead`.
* **Code Implementation Approval:** Merges into `backend/`, `frontend/`, or `sdk/` branches require approvals from the corresponding lead maintainer and the QA lead.
* **Security Approval:** Security-sensitive modifications require a security audit sign-off by `@Sec_Auditor` or `@Sani192`.

---

## 4. Release Responsibilities

* **Release Management:** The Release Manager cut release branches, updates the version metadata, and runs the release checklists.
* **Release Approval:** The final release of any version to production must be approved by the Release Owner (`@Sani192`) and Security Auditor (`@Sec_Auditor`).
* **Emergency Hotfixes:** In the event of a production incident, hotfixes can be deployed with combined approval from `@Sani192` and the Technical Lead, bypass-checking only staging timers while maintaining test verification.
