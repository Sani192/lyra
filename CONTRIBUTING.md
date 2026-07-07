# Contributing to Lyra

## Welcome

Thank you for contributing to Lyra! As an AI-first repository, we maintain a documentation-first, contract-driven engineering culture. 

Every human contributor and AI coding agent must follow the rules and workflows outlined in the product constitution: [PROJECT.md](./PROJECT.md).

---

## How to Contribute

### 1. Find or Propose a Requirement
All implementation work must map to at least one active requirement ID. 
- Look up existing requirements in `docs/specifications/` and [.ai/05-requirements-index.md](.ai/05-requirements-index.md).
- If you are proposing a new feature, you must first update the relevant specification file to define the requirement ID and its acceptance criteria.

### 2. Development Setup
To prepare your local environment for development:
- **Language:** Ensure Python 3.11+ is installed.
- **Dependencies:** Install development dependencies (such as `ruff`, `mypy`, and `pytest`) using your virtual environment package manager:
  ```bash
  python -m venv .venv
  source .venv/bin/activate
  pip install -r requirements-dev.txt  # once created
  ```
- **Code Linters:** All code must pass formatting checks and static typing analysis before being submitted.
  ```bash
  ruff format .
  ruff check .
  mypy .
  ```

### 3. Create a Feature Branch
Create a requirement-scoped feature branch from the latest `main` branch. Follow the naming conventions defined in [Branching Strategy Standards](./docs/engineering/branching-strategy.md):
`feature/LYRA-<CATEGORY>-<NUM>-<short-description>`
(e.g., `feature/LYRA-FR-001-conversation-engine`).

### 4. Commit Message Format
Commit messages must follow Conventional Commits format and reference the matching requirement ID in the footer. Read [Commit Message Standards](./docs/engineering/commit-message-standards.md) for detailed templates:
```
feat(engine): add turn timeout handling

Refs: LYRA-FR-001
```

### 5. Document Architecture Decisions
If your change alters component boundaries, persistence models, or protocols, you must author an Architecture Decision Record (ADR) under `docs/decisions/` using the [ADR Template](./docs/decisions/ADR-template.md) before implementing.

### 6. Write and Run Tests
Every feature must be covered by unit or integration tests under the `tests/` directory. Read the [Testing Strategy](./docs/engineering/testing-strategy.md) to understand how to mock external APIs and validate schemas. Run all automated checks:
```
pytest
```

### 7. Submit a Pull Request
- Create a Pull Request (PR) against `main`.
- Use the pull request template (once registered) and attach validation evidence (test run output, linting logs).
- Request reviews from the appropriate owners listed in the Governance table of [PROJECT.md](./PROJECT.md).

---

## Code of Conduct

We are committed to providing a welcoming, inclusive, and professional environment for all contributors. Please treat others with respect and maintain a highly collaborative engineering environment.
