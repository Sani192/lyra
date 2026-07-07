# Schema Catalog

## Maturity Metadata

**Status:** Draft.

**Intended Use:** Schema catalog and lifecycle planning; not safe as standalone implementation authority until underlying schemas are promoted.


## Purpose

Schemas define machine-readable contracts for Lyra concepts such as capabilities, conversations, events, organizations, consumer contracts, and workflows.

## Versioning

Every schema must declare or document its version. Breaking changes require a new version, migration guidance, compatibility notes, and related requirement IDs.

## Ownership

Lyra owns schema structure and validation rules. Consumer applications own the business meaning and correctness of data they expose through contracts.

## Lifecycle

Schemas are drafted, reviewed, validated against examples, released, monitored for compatibility, deprecated with notice, and retired only after migration.

## Validation

Schema changes must be validated against examples in `examples/` and linked to requirements in `docs/specifications/`.

## Examples

Each schema should have at least one representative example or be referenced by a domain example that exercises successful and failure paths.

## Breaking Changes

Breaking changes include removing fields, changing field meanings, narrowing accepted values, changing required fields, or altering error semantics.

## Backward Compatibility

Prefer additive changes. When breaking changes are unavoidable, publish a new schema version and document migration expectations in `docs/engineering/versioning.md`.
