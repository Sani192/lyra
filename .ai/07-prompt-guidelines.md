# 07 Prompt Guidelines for AI Agents

## Maturity Metadata

**Status:** Approved.

**Intended Use:** Authoritative AI-agent operating context; safe for repository navigation, context building, and prompting constraints.

## Purpose

Provide structured guidance, prompt templates, and reasoning constraints for AI agents interacting with the Lyra repository, ensuring compatibility with our documentation-first engineering model.

## Agent System Prompt Recommendations

When initializing an AI coding session for Lyra, prepend or configure the agent's context with these instructions:

1. **Constitutional Alignment:** "You are an AI software engineer working on Lyra. You must adhere to the rules in `PROJECT.md` at all times. Specifically, you must never implement business logic or own business state."
2. **Context Scanning:** "Before proposing any code change, you must locate the relevant specification in `docs/specifications/` and read the associated ADRs in `docs/decisions/`."
3. **No Placeholders:** "Do not output TODOs or placeholder functions. Every function you write must be fully typed and documented."

## Structured Prompt Templates

### Template A: Proposing a Requirement
```
I am planning to implement requirement ID: [ID].
I have read the specification file: [Spec Path].
Here is the proposed update to the specification's acceptance criteria:
[Proposed Criteria]
Please review this specification update before I begin implementation planning.
```

### Template B: Architecture Review
```
I am proposing an architectural change for [Component].
Related Requirement IDs: [IDs].
I have created/updated ADR: [ADR Number] with options and trade-offs.
Here is the proposed component diagram change:
[Mermaid Diagram]
```

## Review Checklist

- [ ] Prompts reference active requirement IDs.
- [ ] Prompts declare that the agent has read `PROJECT.md` and related ADRs.
- [ ] Prompts do not request stateful database logic within the Lyra platform boundaries.
