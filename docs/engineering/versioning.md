# Versioning Standards

## Maturity Metadata

**Status:** Approved.

**Intended Use:** Authoritative versioning conventions, git tagging rules, changelog maintenance, and API/schema compatibility guidelines for Lyra contributors and AI agents.

## Purpose

Define how Lyra platforms, schemas, SDKs, and consumer contracts are versioned and tagged, ensuring clear upgrade paths, deprecation notices, and backward compatibility.

## Scope

Applies to platform releases, public APIs, schemas, SDKs, git tagging, and contract validation rules.

## Release Versioning Standards

1. **Semantic Versioning (SemVer):**
   - Follow **Semantic Versioning 2.0.0 (SemVer)**: `MAJOR.MINOR.PATCH` format.
     - `MAJOR` version increments for incompatible API changes.
     - `MINOR` version increments for backward-compatible functionality additions.
     - `PATCH` version increments for backward-compatible bug fixes.
2. **Git Tagging:**
   - Releases must be tagged in git using the `v` prefix followed by the SemVer string (e.g., `v1.2.0`). Tags must be pushed to the origin repository.
3. **Changelog Maintenance:**
   - Every release must have a corresponding entry in `CHANGELOG.md` detailing the version, release date, and categories: Added, Changed, Deprecated, Removed, Fixed, Security.
4. **Version Pinning:**
   - External dependencies and library imports must be pinned to specific versions (or tight version ranges) in configuration files like `pyproject.toml` to prevent runtime drift.

## Schema Versioning

- Schemas in `schemas/` must declare their version in their filename or path if breaking changes occur, or use the `x-schemaVersion` field.
- Prefer additive modifications (adding optional fields) to preserve backward compatibility.
- Breaking schema changes (removing fields, changing type constraints, making optional fields required) require a major schema version bump.

## Public API Versioning

- Public APIs must include the major version in the URL path (e.g., `/api/v1/...`).
- Old API versions must remain supported for a defined deprecation window.

## Deprecation Policy

- Deprecating an API, schema, or configuration parameter requires documenting it in the release notes and marking the associated code/docs as `Deprecated`.
- The deprecation notice must specify the migration path and the target removal version (at least one major release ahead).

## Review Checklist

- [ ] Version bump conforms to SemVer rules based on changes made.
- [ ] Release tag is formatted correctly (e.g., `v1.2.0`) and tagged in Git.
- [ ] `CHANGELOG.md` is updated with a summary of changes.
- [ ] Dependencies are pinned in `pyproject.toml`.
- [ ] Schema changes are backward-compatible, or a new schema version is registered.
- [ ] Deprecation notices are added to all affected code and documentation.
- [ ] Migration guidelines are provided for any breaking change.
