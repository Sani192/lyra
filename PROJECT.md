# Lyra Project Constitution

## Mandatory First Read

Every human contributor and AI coding agent must read this document before changing Lyra. This file defines the product vision, architectural boundaries, repository rules, and non-negotiable principles that protect Lyra from becoming a consumer-specific application.

## Product Vision

Lyra is an AI Voice Orchestration Platform that enables reliable, observable, contract-driven conversations between customers and consumer applications. Lyra understands customer intent, selects appropriate capabilities, invokes those capabilities through standardized contracts, and orchestrates a natural conversation while consumer applications remain the systems of record.

## Mission

Lyra's mission is to make voice automation safe for production business workflows by combining conversational intelligence with strict ownership boundaries. Lyra should help organizations automate customer interactions without duplicating or replacing their existing business applications.

## Architecture Principles

1. **Lyra never owns business data.** Orders, customers, inventory, appointments, payments, loyalty state, pricing rules, and business policies live in consumer applications.
2. **Consumer applications own business logic.** Lyra may ask what actions are available, invoke declared capabilities, and report outcomes, but it must not decide consumer-specific business policy.
3. **Lyra is contract driven.** Integrations are described through explicit contracts that define capability names, inputs, outputs, errors, safety rules, and observability expectations.
4. **Capabilities are protocol agnostic.** A capability represents an application action independent of whether it is exposed through REST, OpenAPI, MCP, webhooks, or future protocols.
5. **REST, OpenAPI, and MCP are first-class integration paths.** Lyra must support these protocols without binding the domain model to one transport.
6. **Conversation state is not business state.** Lyra may store transcripts, recordings, context, events, and orchestration metadata, but it must not become the source of truth for external domains.
7. **Observability is a product feature.** Every important decision, capability invocation, error, and handoff must be traceable.
8. **Security and privacy are design constraints.** Least privilege, tenant isolation, data minimization, and auditability apply to all platform areas.
9. **Backward compatibility matters.** Contracts should evolve predictably through versioning, deprecation windows, and compatibility guidance.
10. **Architecture is documented before implementation.** Major changes require specification updates and ADRs before code is written.

## Domain Language

* **Consumer:** An external application or organization that integrates with Lyra.
* **Capability:** A declared business action Lyra can invoke on a consumer application.
* **Contract:** The machine-readable and human-readable agreement describing available capabilities.
* **Conversation:** A customer interaction orchestrated by Lyra.
* **Session:** A bounded runtime instance of a conversation.
* **Workflow:** A structured orchestration path that may coordinate intents, prompts, capabilities, events, and escalation.
* **Playbook:** A scenario-specific strategy for conversations such as ordering, booking, support, or lead qualification.
* **Capability Registry:** The catalog where Lyra discovers and evaluates available capabilities.
* **Capability Intelligence Framework:** The future framework for ranking, validating, selecting, and explaining capability usage.

## Repository Rules

* `PROJECT.md` is authoritative when repository documents conflict.
* Requirement IDs must be referenced by implementation plans, commits, reviews, and tests when applicable.
* New architecture decisions require ADRs under `docs/decisions/`.
* Specifications belong under `docs/specifications/` and should remain numbered for stable navigation.
* Consumer examples must demonstrate boundaries and must not imply Lyra owns business state.
* Backend, frontend, and SDK directories are reserved for future implementation and should remain code-free until implementation is explicitly approved.

## Coding Philosophy

Lyra code, when introduced, must be boring, observable, testable, and contract-aligned. Prefer explicit domain names over clever abstractions. Separate orchestration from protocol adapters. Keep consumer-specific customization in configuration, contracts, playbooks, or external systems rather than platform code.

## Documentation Philosophy

Documentation is a design artifact, not an afterthought. Each specification should communicate purpose, scope, status, owner, revision history, planned sections, future work, and references. Documentation should be readable by humans and structured enough for AI agents to navigate safely.

## Non-Negotiable Rules

* Never introduce consumer-specific business logic into Lyra.
* Never make Lyra the source of truth for orders, customers, inventory, appointments, payments, loyalty, or business rules.
* Always treat capabilities as contract-defined and protocol-agnostic.
* Always support the architectural direction of REST, OpenAPI, and MCP.
* Always reference requirement IDs for requirement-impacting changes.
* Always update documentation before implementation.
* Always create or update ADRs for material architecture decisions.
* Always preserve backward compatibility where possible and document breaking changes clearly.
* Always protect tenant isolation and customer data.

## AI Agent Instructions

AI agents must begin with this file, then read `.ai/README.md` and `.ai/context.md`. Agents should avoid implementation unless explicitly requested. When implementation is requested later, agents must identify relevant requirement IDs, update documentation first, and keep changes within the documented architecture boundaries.
