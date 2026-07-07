# Repository Conventions

## Maturity Metadata

**Status:** Approved.

**Intended Use:** Authoritative conventions for directory layouts, file naming, and markdown documentation styling.

## Purpose

Define the structure, file naming patterns, and documentation styling conventions that keep the repository predictable, clean, and highly indexable by both humans and AI agents.

## Scope

Applies to all files and folders in the repository.

## Directory Structure and Naming

1. **Directories:** Lowercase with hyphens or underscores (e.g., `docs/specifications/`, `docs/decisions/`).
2. **Markdown Files:** Lowercase and kebab-case (e.g., `docs/engineering/testing-strategy.md`). Numerical prefixes should be used where a logical sequence exists (e.g., `.ai/00-start-here.md`).
3. **JSON Schemas:** Named after their core entity using `.schema.json` suffix (e.g., `schemas/capability.schema.json`).
4. **Implementation Files:** Standard naming according to language norms (snake_case for Python).

## Markdown Styling Conventions

* **Headings:** Use standard ATX headings (`#`, `##`, `###`) rather than Setext underlines.
* **Alerts:** Use standard GitHub alertsstrategic format (`> [!NOTE]`, `> [!IMPORTANT]`, `> [!WARNING]`, `> [!CAUTION]`) to call out metadata and constraints.
* **Maturity Metadata:** Must occupy lines 3-7 in all major documentation files.
* **Cross-References:** Use standard Markdown links. Always use relative paths with forward slashes (e.g., `[Branching Strategy](../engineering/branching-strategy.md)`). Do not use absolute paths.

## Review Checklist

- [ ] File and directory names conform to casing standards.
- [ ] Maturity metadata section is included near the top of the file.
- [ ] No broken relative links are introduced.
- [ ] All cross-references use relative paths.
