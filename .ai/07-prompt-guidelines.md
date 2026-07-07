# 07 Prompt Guidelines for AI Agents

## Before Changing Code

1. Read `PROJECT.md`.
2. Read relevant specifications.
3. Read related ADRs.
4. Identify requirement IDs.
5. Review contracts, schemas, examples, and standards.
6. Update documentation first.
7. State assumptions in commit or PR notes.

## Contribution Rules

Avoid assumptions, never bypass architecture, do not invent hidden requirements, do not add consumer-specific shortcuts, and always reference requirement IDs for requirement-impacting work.

## Safe Prompt Pattern

"I will update documentation and traceability for requirement `LYRA-...`, preserve Lyra's stateless contract-driven boundary, and avoid implementing consumer business logic."
