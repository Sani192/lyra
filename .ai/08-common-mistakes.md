# 08 Common Mistakes

## Maturity Metadata

**Status:** Approved.

**Intended Use:** Anti-pattern reference and code review guidance for Lyra developers and AI agents.

## Purpose

Document common design anti-patterns, implementation mistakes, and boundary violations that contributors must actively avoid.

## anti-Patterns and Mitigations

### 1. Storing Business State in Lyra
* **Mistake:** Creating database tables in `backend/` to hold consumer-specific data (e.g. creating an `orders` or `appointments` table inside Lyra's persistence layer).
* **Mitigation:** Lyra must only persist conversation session logs (transcripts, audio recordings, turn metadata) and capability metadata. Retrieve business state dynamically via capability calls.

### 2. Hardcoding Business Rules
* **Mistake:** Implementing conditional logic for specific domains (e.g., `if domain == 'restaurant' and reservation_time > '21:00': reject()`).
* **Mitigation:** Move this validation rule to the consumer application. Lyra should invoke the registered capability, and let the consumer return a validation error.

### 3. Silently Ignoring Schema Validation
* **Mistake:** Bypassing JSON Schema validation on capability request/response payloads to speed up local testing or handle temporary contract drift.
* **Mitigation:** Schema validation is a non-negotiable gate. If a contract drifts, update the contract schema in `schemas/` and the mock fixtures before changing implementation code.

### 4. Creating Placeholders Instead of Real Specifications
* **Mistake:** Committing new documentation or specification pages that contain only template headers and "Future work" placeholders.
* **Mitigation:** Ensure every documentation page has substantive, clear content before merging. Follow the [Maturity Model](../PROJECT.md#repository-maturity-model) rules.

## Review Checklist

- [ ] Change contains no hardcoded conditional logic for specific consumers or domains.
- [ ] No local business tables or business schemas are added to Lyra databases.
- [ ] Interface boundaries strictly enforce JSON Schema validation.
- [ ] Documentation updates contain actual design specifications rather than empty placeholders.
