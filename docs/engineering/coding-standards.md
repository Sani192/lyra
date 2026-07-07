# Coding Standards

## Maturity Metadata

**Status:** Approved.

**Intended Use:** Authoritative coding conventions, technology stack constraints, style guidelines, and language-specific rules for Lyra implementation.

## Purpose

Establish clear, measurable, and enforceable standards for Lyra source code, ensuring that all implementation remains stateless, highly observable, and decoupled from consumer domain details.

## Scope

Applies to all source code written for the backend, frontend, and SDKs.

## Language and Tooling Standards

1. **Backend Development:**
   - **Language:** Python 3.11+ is the primary platform language.
   - **Type Hints:** Static typing is mandatory. All function signatures must include fully specified type hints. Run `mypy` for static type verification.
   - **Code Formatting:** Use `ruff` or `black` for formatting and `ruff` / `flake8` for linting.
   - **Docstrings:** Follow PEP 257 (Google style preferred). Write clear docstrings for all public modules, classes, and methods, explicitly referencing any associated requirement IDs.

2. **Platform & Safety Rules:**
   - **No Shared State:** Lyra services must be stateless. Never store in-memory session pools, local file state, or uncoordinated caches that block horizontal scaling.
   - **Contract Validation:** All inputs received from consumer applications or client devices must be validated against their registered JSON Schemas before processing.
   - **Observability Hooks:** Every external call, capability invocation, state transition, and error must emit structured logs and observability events.

## Code Styling Conventions

1. **Python Styling (PEP 8):**
   - Follow PEP 8 guidelines.
   - Max line length is 100 characters.
   - Use 4 spaces for indentation. Never use tabs.
2. **Naming Conventions:**
   - **Classes:** PascalCase (e.g., `ConversationEngine`).
   - **Functions & Variables:** snake_case (e.g., `invoke_capability`).
   - **Constants:** UPPERCASE_SNAKE_CASE (e.g., `MAX_SESSION_DURATION_SECONDS`).
3. **Import Ordering:**
   - Group imports in this order:
     1. Standard library imports.
     2. Third-party library imports.
     3. Local application imports.
   - Alphabetize imports within each group.
4. **Comments and Documentation:**
   - Write comments to explain *why* code is written a certain way, not *what* it does.
   - Keep comments current. Obsolete comments are worse than no comments.

## Review Checklist

- [ ] Static typing checks pass without errors (`mypy`).
- [ ] Code formatting and linting pass (`ruff` or `black` / `flake8`).
- [ ] No local/in-memory session state is introduced.
- [ ] All inputs are validated against schema boundaries.
- [ ] Variable and function names follow PascalCase / snake_case rules.
- [ ] Line lengths do not exceed 100 characters.
- [ ] Imports are sorted and grouped correctly.
- [ ] Comments are up to date and describe implementation rationale.
- [ ] All functions and modules have docstrings.
- [ ] All code changes trace directly back to requirement IDs.
