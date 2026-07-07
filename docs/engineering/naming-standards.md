# Naming Standards

## Maturity Metadata

**Status:** Approved.

**Intended Use:** Standard rules for casing, file structures, schemas, and endpoint names.

## Purpose

Define the naming standards for code symbols, REST endpoints, schemas, and repository files to maintain code readability and system uniformity.

## Casing and Name Formats

1. **REST API Endpoints:** Lowercase with hyphens (kebab-case) (e.g., `/api/v1/capability-registry`). Endpoints should represent resources (nouns), not actions (verbs).
2. **Capability Identifiers:** Standard dotted format (e.g., `lyra.examples.restaurant.book_table`).
3. **JSON Schema Fields:** snake_case (e.g., `conversation_id`, `created_at`).
4. **Environment Variables:** UPPERCASE_SNAKE_CASE (e.g., `LYRA_PORT`, `DATABASE_URL`).
5. **Class Names:** PascalCase (e.g., `CapabilityRegistry`).
6. **Function Names:** snake_case (e.g., `register_capability`).

## Review Checklist

- [ ] REST endpoints use kebab-case nouns.
- [ ] Schema properties use snake_case naming.
- [ ] Capability IDs follow the dotted taxonomy format.
- [ ] Variables and classes conform to casing requirements.
