# 02 Core Principles

## Non-Negotiable Rules

* Lyra never owns business state.
* Consumer applications own business logic.
* Lyra is stateless with respect to external business domains.
* Integrations are contract-driven.
* Capabilities are protocol-agnostic.
* REST, OpenAPI, and MCP are first-class supported protocols.
* Never hardcode consumer-specific behavior.
* Documentation precedes implementation.
* Architecture decisions require ADRs.
* Every requirement must have an ID.
* Every feature must trace back to the SRS and related specifications.
* Observability, security, privacy, and tenant isolation are required design properties.

## Practical Interpretation

If a change teaches Lyra a consumer's pricing rule, inventory policy, appointment rule, or eligibility decision, the change belongs outside Lyra or inside a consumer contract/playbook rather than platform code.
