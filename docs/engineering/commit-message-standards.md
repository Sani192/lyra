# Commit Message Standards

## Maturity Metadata

**Status:** Approved.

**Intended Use:** Commit logging conventions and requirement tracking in git history.

## Purpose

Define the format and structure of commit messages to ensure traceability, clear history tracking, and automated release notes generation.

## Commit Message Format

Commit messages must follow the **Conventional Commits 1.0.0** specification.

```
<type>(<scope>): <description>

[optional body]

[optional footer(s)]
```

### 1. Types

- `feat`: A new user-facing capability or system feature.
- `fix`: A bug fix.
- `docs`: Documentation-only changes.
- `style`: Changes that do not affect the meaning of the code (formatting, linting).
- `refactor`: A code change that neither fixes a bug nor adds a feature.
- `test`: Adding missing tests or correcting existing tests.
- `chore`: Changes to the build process, tooling, or helper scripts.

### 2. Scope

The scope should represent the subsystem or directory being changed (e.g., `engine`, `registry`, `schemas`, `docs`, `restaurant-example`).

### 3. Footer and Requirement IDs

Commits affecting platform behavior must reference the matching requirement ID in the footer:

```
feat(engine): add turn timeout handling

Implemented automatic conversation session suspension when turn duration
exceeds the SLA limit.

Refs: LYRA-FR-001, LYRA-NFR-002
```

## Review Checklist

- [ ] Commit subject uses Conventional Commit prefixes (e.g. `feat:`, `fix:`).
- [ ] Description is in the imperative mood (e.g. "add feature" not "added feature").
- [ ] Footer references appropriate requirement IDs (e.g. `Refs: LYRA-FR-001`).
