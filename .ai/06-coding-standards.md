# 06 Coding Standards

## Repository Philosophy

Code should be introduced only after requirements and architecture are documented. Implementation should be small, observable, testable, and aligned with contract boundaries.

## Folder Ownership

Specifications belong in `docs/specifications/`, architecture in `docs/architecture/`, ADRs in `docs/decisions/`, engineering standards in `docs/engineering/`, schemas in `schemas/`, and examples in `examples/`.

## Dependency Rules

Dependencies must have clear ownership, security posture, versioning strategy, and operational justification. Avoid dependencies that embed consumer-specific behavior.

## Naming

Use domain terms from `.ai/03-domain-model.md` and `docs/glossary/README.md`. Names should reveal ownership and lifecycle.

## Testing Philosophy

Tests should prove contract behavior, boundary preservation, compatibility, observability, and failure handling. Tests must reference requirement IDs when they validate requirements.

## Documentation Expectations

Documentation changes accompany requirement, architecture, schema, contract, and behavior changes.

## Versioning and Compatibility

Use semantic versioning where applicable, explicit schema versions, deprecation notices, migration notes, and compatibility checks.

## Refactoring Rules

Refactors must preserve contracts, tests, requirement traceability, and public behavior unless a breaking change is documented and approved.
