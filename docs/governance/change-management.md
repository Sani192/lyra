# Change Management Process

## Maturity Metadata

**Status:** Approved.

**Intended Use:** Authoritative standard governing how modifications to requirements, architecture, schemas, public contracts, APIs, and versions are managed, reviewed, and executed.

## Overview

Change Management ensures that the Lyra codebase, API surfaces, and contracts evolve in a predictable, stable, and backward-compatible manner. Uncontrolled changes, sudden breakages, and undocumented modifications are not permitted.

---

## 1. Requirement Changes

When a requirement must be added, modified, or retired:
* **Impact Analysis:** The Product Manager and Technical Lead assess which architectural components, code paths, and tests are affected.
* **Specification Update:** The specification markdown file in `docs/specifications/` is edited. The requirement's status is updated to `Review` or `Draft`.
* **Approvals:** The change must be approved by the Product Owner (`@Sani192`).
* **Traceability Updates:** The central traceability matrix in `docs/traceability/README.md` is updated.

---

## 2. Architecture Changes

When system boundaries, component relationships, or data flows change:
* **ADR Requirement:** An ADR must be written following the [adr-process.md](file:///Users/anonymous/Documents/Java/Workspaces/Python/lyra/docs/governance/adr-process.md).
* **Alternatives & Trade-offs:** The ADR must detail alternatives and trade-offs.
* **Approvals:** Must obtain unanimous approval from the Architecture Owner (`@Sani192`) and the Architectural Board (`@Arch_Guild`).
* **Validation:** Architecture diagrams under `docs/diagrams/` must be updated.

---

## 3. Schema Changes

When JSON schemas in `schemas/` are updated:
* **Compatibility Check:** Schema edits must be backward compatible unless a major version bump is planned.
* **Linter Validation:** The schema must pass all automated validation tools under `tools/`.
* **Examples Update:** Matching JSON fixtures and examples under `examples/` must be updated concurrently.
* **Approvals:** Requires approval from the Schema & API Owner (`@Sani192`) and API Lead (`@API_Lead`).

---

## 4. Breaking Changes

Breaking changes are defined as modifications that prevent existing consumers from communicating with Lyra or break existing deployments (e.g., removing API fields, changing event schemas, altering routing behaviors).
* **Avoidance:** Breaking changes must be avoided.
* **Structured Rollout:** If unavoidable, they must be rolled out via the **Expand/Contract** design pattern:
  1. *Phase 1:* Deploy new fields (optional).
  2. *Phase 2:* Support both old and new patterns.
  3. *Phase 3:* Mandate migrations.
  4. *Phase 4:* Deprecate and remove old patterns.
* **Approvals:** Requires explicit sign-off from the Architecture Owner (`@Sani192`) and a major version bump planning ticket.

---

## 5. Protocol changes

When protocol adapters (e.g., REST, OpenAPI, MCP) are added or changed:
* **Agnostic Core:** The change must not affect the protocol-agnostic domain core of Lyra. Only the adapter edge layer should be modified.
* **Specification Update:** The protocol specification in `docs/specifications/15-protocol-layer.md` must be updated.
* **Integration Tests:** The change must be validated by dedicated protocol adapter integration tests.

---

## 6. Consumer Contract Changes

When contracts governing how consumer systems are called change:
* **Contract Specification:** The contract model in `docs/specifications/09-consumer-contract.md` or `docs/contracts/` must be updated.
* **Example Verifications:** New capability calling examples must be checked in under `examples/`.
* **Approvals:** Requires sign-off from the Integration Lead (`@API_Lead`).

---

## 7. Version Changes

All version changes must comply with Semantic Versioning (SemVer) rules.
* **Patch Release:** Backward-compatible bug fixes and docs (v1.0.0 → v1.0.1).
* **Minor Release:** Backward-compatible new features (v1.0.0 → v1.1.0).
* **Major Release:** Breaking changes (v1.0.0 → v2.0.0).
* **Metadata Update:** Version metadata in `PROJECT.md`, `pyproject.toml`, and SDK package manifests must be updated together.

---

## 8. Deprecation Path

When a feature, endpoint, or schema property is slated for removal:
* **Step 1: Marking:** The feature must be marked with `@deprecated` in code comments and decorated in schema documentation, citing the target removal version.
* **Step 2: Documentation:** Add warning blocks to the affected specifications.
* **Step 3: Monitoring:** Monitor logs to ensure zero active consumer calls hit the deprecated feature before physical deletion.
* **Step 4: Deletion:** Physically remove the code in a major version release.
