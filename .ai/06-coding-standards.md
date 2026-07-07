# 06 Coding Standards

## Maturity Metadata

**Status:** Approved.

**Intended Use:** Authoritative AI-agent operating context; safe for repository navigation and code contribution decisions.

## Repository Philosophy

Code should be introduced only after requirements and architecture are documented. Implementation should be small, observable, testable, and aligned with contract boundaries.

## Language and Formatting Specifications

1. **Python 3.11+ Standards:**
   - Static typing is mandatory. All functions must use standard PEP 484 type hints.
   - Use `ruff` or `black` for auto-formatting. Line limit is 100 characters.
   - Use `ruff` or `flake8` for linting. Bypassing linting errors with `# noqa` requires inline reviewer comments explaining the exception.

2. **NLU & AI Integration Boundaries:**
   - Never write logic that relies on LLM prompt outputs without explicit schema validation.
   - All AI response parsing must be wrapped in `Pydantic` validation or standard JSON Schema validators.

## Dependency Rules

* **Explicit Locks:** All production dependencies must be locked using exact versions in dependency tracking files.
* **Separation of Concerns:** Do not add libraries that bundle external business rules or domain policies.

## Testing Expectations

* **Pytest Framework:** Write all backend verification suites using `pytest`.
* **Traceable Assertions:** Test function names or metadata tags must cite the requirement ID being tested (e.g. `def test_session_lifecycle_compliance_LYRA_FR_001()`).
* **Clean Mocking:** Do not perform network calls in unit tests. Use mock servers or integration adapters for testing capability endpoints.

## Related Standards

- Complete Python style rules: [Coding Standards](../docs/engineering/coding-standards.md)
- Branching and Git guidelines: [Branching Strategy](../docs/engineering/branching-strategy.md)
