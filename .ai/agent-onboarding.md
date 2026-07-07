# Agent Onboarding

## Maturity Metadata

**Status:** Approved.

**Intended Use:** Authoritative AI-agent operating context; safe for repository navigation and contribution workflow decisions.


## Purpose

This document gives AI agents concise operating context for Lyra. Agents must preserve the boundary that Lyra owns conversation orchestration while consumer applications own business state and business logic.

## Key Rules

* Read `PROJECT.md` before making changes.
* Do not implement software unless explicitly asked.
* Use requirement IDs from `docs/specifications/06-functional-requirements.md` and `07-non-functional-requirements.md`.
* Keep capabilities contract-driven and protocol-agnostic.
* Do not add consumer-specific logic to Lyra.

## Working Context

Lyra receives conversations, identifies intent, selects declared capabilities, invokes consumer systems through REST, OpenAPI, or MCP, records observable events, and manages transcripts and recordings. Lyra should explain decisions without becoming the source of truth for consumer domains.
