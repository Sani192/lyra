# Documentation Process and Standards

## Maturity Metadata

**Status:** Approved.

**Intended Use:** Authoritative process guidelines enforcing the documentation-first philosophy, maintenance rules, review expectations, and defect classification for documentation.

## Overview

In Lyra, documentation is a first-class engineering deliverable. We operate under a **documentation-first** philosophy. The system's codebase must reflect its documented agreements, not the other way around. Outdated, missing, or broken documentation is treated as a severe system defect.

---

## Core Documentation Rules

Every contributor (human and AI agent) must adhere to these five core rules:

### 1. Documentation Precedes Implementation
No implementation work may begin until the corresponding requirements, specifications, contracts, and architecture designs are written, reviewed, and approved. A feature is not ready for development if the documentation does not describe its target behavior.

### 2. Implementation Updates Documentation
If during implementation the developer discovers gaps, edge cases, or details that deviate from the approved design, they must stop coding, update the specifications/contracts first, obtain review approval, and only then proceed with code changes. Code must never drift ahead of documentation.

### 3. Deprecated Features Update Documentation
When a feature, API field, configuration, or capability is deprecated or removed:
* All associated documentation, schemas, and specifications must be updated to clearly state the deprecation version, migration path, and removal timeline.
* Document status must be marked as `Deprecated` in its maturity metadata block.

### 4. Broken Documentation is a Defect
Broken links, outdated examples, missing schemas, incorrect code blocks, or spelling and syntax issues are treated as engineering defects.
* **Severity:** Broken links in core architecture or schemas are treated as **High-Priority Defects** and must be resolved before any feature merges.
* **Linter Integration:** All documentation markdown files must pass markdown lint checks and link verification.

### 5. Documentation Review is Mandatory
Every pull request changing documentation must be reviewed.
* Changes to public APIs or integration guides require review by the Tech Writer/Docs Lead (`@Docs_Lead`).
* Changes to architecture design require review by the Architecture Owner (`@Sani192`).
* Changes to requirements require review by the Product Owner (`@Sani192`).

---

## Documentation Categories and Hierarchy

Contributors must write documentation in the appropriate location in the repository hierarchy:

1. **PROJECT.md:** The root repository constitution. (Highest authority).
2. **docs/specifications/:** Product specifications and requirements.
3. **docs/architecture/:** Design components, data flows, and state machines.
4. **docs/decisions/:** Sequentially numbered ADRs.
5. **docs/engineering/:** Coding standards, naming, review processes, versioning.
6. **docs/contracts/ and docs/api/:** Edge protocols and API mappings.
7. **schemas/:** JSON schemas governing interactions.
8. **examples/:** Actual usage scenarios showing expected inputs, outputs, and errors.
9. **.ai/:** Knowledge Center files defining AI workflows and checklists.

---

## Technical Standards for Documentation

* **Format:** Every document must use GitHub Flavored Markdown (GFM).
* **Maturity Metadata:** Major files must declare a status and intended-use block at the top as defined in [PROJECT.md](file:///Users/anonymous/Documents/Java/Workspaces/Python/lyra/PROJECT.md).
* **Link Formats:** All file and symbol links must use the absolute `file://` scheme (e.g., `[naming-standards.md](file:///Users/anonymous/Documents/Java/Workspaces/Python/lyra/docs/engineering/naming-standards.md)`). Backticks must not be used around the link text.
* **Line Lengths:** To avoid wrapping issues, sentences and bullet points should be kept concise, and line lengths should not exceed 100 characters where possible.
