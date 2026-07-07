# 03 Domain Model

Each concept below is defined by purpose, owner, relationships, and lifecycle.

## Organization
Purpose: tenant boundary for configuration and observability. Owner: Lyra for metadata; consumer for business identity. Relationships: owns projects and environments. Lifecycle: created, configured, audited, archived.

## Project
Purpose: groups a product integration or deployment initiative. Owner: Lyra. Relationships: belongs to an organization and contains environments, contracts, workflows, and examples. Lifecycle: proposed, active, deprecated, archived.

## Environment
Purpose: isolates development, staging, and production settings. Owner: Lyra. Relationships: scopes contracts, credentials, callbacks, and observability. Lifecycle: provisioned, validated, promoted, retired.

## Conversation
Purpose: customer interaction managed by Lyra. Owner: Lyra for transcript and orchestration metadata. Relationships: may contain sessions, intents, entities, events, recordings, and invocations. Lifecycle: started, active, completed, escalated, retained, deleted under policy.

## Session
Purpose: bounded runtime execution of a conversation. Owner: Lyra. Relationships: belongs to a conversation and uses contracts, agents, workflows, and capabilities. Lifecycle: opened, active, paused, closed, summarized.

## Agent
Purpose: AI runtime persona or orchestration participant. Owner: Lyra. Relationships: uses prompts, workflows, capabilities, and knowledge bases. Lifecycle: configured, evaluated, deployed, versioned, retired.

## Capability
Purpose: contract-declared action available in a consumer application. Owner: consumer owns behavior; Lyra owns discovery and invocation metadata. Relationships: registered in capability registry and exposed through protocols. Lifecycle: declared, validated, invoked, observed, deprecated.

## Capability Registry
Purpose: catalog capabilities and their metadata. Owner: Lyra. Relationships: indexes consumer contracts, schemas, versions, safety constraints, and protocol adapters. Lifecycle: synchronized, validated, queried, updated.

## Consumer Contract
Purpose: agreement describing capabilities, inputs, outputs, errors, security, and observability. Owner: consumer and Lyra jointly. Relationships: references schemas, protocols, capabilities, and webhooks. Lifecycle: drafted, validated, versioned, deployed, deprecated.

## Workflow
Purpose: orchestration path for intents, prompts, decisions, invocations, and escalation. Owner: Lyra for orchestration; consumer owns business outcomes. Relationships: uses agents, capabilities, playbooks, events, and contracts. Lifecycle: designed, tested, versioned, monitored, retired.

## Knowledge Base
Purpose: approved informational source for responses. Owner: consumer for content accuracy; Lyra for indexing/orchestration metadata. Relationships: used by agents and workflows. Lifecycle: ingested, validated, refreshed, expired.

## Transcript
Purpose: textual record of a conversation. Owner: Lyra under retention policy. Relationships: linked to conversation, session, events, and recording. Lifecycle: captured, redacted, retained, exported, deleted.

## Recording
Purpose: audio evidence for a conversation. Owner: Lyra under retention and privacy policy. Relationships: linked to transcript and conversation. Lifecycle: captured, stored, accessed, expired, deleted.

## Business Event
Purpose: observable fact emitted by Lyra or consumer systems. Owner: source system. Relationships: linked to sessions, capabilities, webhooks, and audit trails. Lifecycle: emitted, delivered, acknowledged, retried, archived.

## Playbook
Purpose: scenario guidance such as booking, support, ordering, or lead qualification. Owner: Lyra for structure; consumer for domain content. Relationships: informs workflows and examples. Lifecycle: authored, reviewed, versioned, applied.

## Protocol
Purpose: transport or integration mechanism. Owner: protocol adapter. Relationships: REST, OpenAPI, MCP, and webhooks expose capabilities without changing domain semantics. Lifecycle: supported, versioned, deprecated.

## Intent
Purpose: inferred customer goal. Owner: Lyra. Relationships: extracted from conversation and used to choose workflow/capability. Lifecycle: detected, confirmed, fulfilled, corrected.

## Entity
Purpose: structured value extracted from conversation. Owner: Lyra for extraction metadata; consumer validates business meaning. Relationships: used as capability input. Lifecycle: detected, confirmed, validated, discarded.

## MCP
Purpose: model-context protocol integration path. Owner: protocol ecosystem and Lyra adapter. Relationships: exposes tools/capabilities. Lifecycle: configured, invoked, monitored, versioned.

## OpenAPI
Purpose: machine-readable HTTP API description. Owner: consumer for API surface; Lyra for import/validation metadata. Relationships: maps operations to capabilities. Lifecycle: imported, validated, versioned, deprecated.

## REST
Purpose: HTTP integration style. Owner: consumer API and Lyra adapter. Relationships: executes capabilities through endpoints. Lifecycle: configured, invoked, monitored, versioned.

## Webhook
Purpose: asynchronous callback or event delivery. Owner: source system and receiver. Relationships: carries business events, status changes, or notifications. Lifecycle: subscribed, emitted, retried, acknowledged, disabled.
