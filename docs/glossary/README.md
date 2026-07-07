# Lyra Glossary

## Maturity Metadata

**Status:** Approved.

**Intended Use:** Authoritative glossary defining key domain terms for Lyra contributors and AI agents.

---

* **Orchestration:** The coordination of conversation routing, intent detection, slot-filling, playbook execution, capability validation, and error recovery across a conversation session.
* **Stateless:** A design property of Lyra where the platform never persists or manages business-of-record state (e.g. user accounts, catalog inventories, payment records). Lyra only maintains conversation session state (e.g. active turn, conversation history, audio metadata).
* **Tenant:** An isolated project or environment owned by an organization, ensuring that credentials, data logs, playbooks, and session state are isolated from other organizations.
* **Turn:** A single pair of conversational steps consisting of a customer input (audio/text) and Lyra's corresponding system response.
* **Business State vs. Orchestration State:**
  - *Business State:* Domain data owned exclusively by the consumer application (e.g., patient records, table reservations, credit balances).
  - *Orchestration State:* Runtime session metadata owned by Lyra to coordinate dialogue (e.g., entity slots filled, intent detected, last active step).
* **Consumer:** An external application, organization, or third-party system integrating with Lyra to provide domain capabilities and business logic.
* **Capability:** A specific action or API endpoint exposed by the consumer application (e.g., `book_table`) that Lyra can discover and invoke dynamically.
* **Contract:** The formal, machine-readable declaration (`consumer-contract`) specifying the capabilities, schemas, endpoints, and authentication required by a consumer application.
* **Conversation:** An end-to-end dialog session between a customer and Lyra.
* **Session:** The runtime container for a conversation, tracked via a unique session ID and isolated by tenant boundaries.
* **Workflow:** A sequential execution path coordinates prompts, intent checks, capability calls, and fallback escalations.
* **Knowledge Base:** An external repository of documents or data used for Retrieval-Augmented Generation (RAG) during a conversation.
* **Agent:** An NLU model or LLM agent configuration within Lyra that extracts intents/entities and plans responses.
* **Intent:** The customer's inferred goal derived from natural language input (e.g., `request_booking`).
* **Entity:** A specific structured parameter extracted from user input (e.g., `time="19:00"`, `guests=4`).
* **Business Event:** A structured notification emitted by Lyra or a consumer system when a significant milestone occurs.
* **Transcript:** The textual representation of a conversation, generated from audio input and system responses.
* **Recording:** The raw audio file of a conversation turn or session.
* **Playbook:** The scenario-specific orchestration script guiding the Conversation Engine.
* **Capability Registry:** The directory within Lyra holding all registered capability schemas and contracts.
* **Capability Intelligence Framework:** The component that scores capability match confidence and recommends routing options to the AI Agent Layer.
* **MCP:** Model Context Protocol; a standardized open-source protocol for exposing capabilities as tools to LLM models.
* **OpenAPI:** A standard, language-agnostic interface description for REST APIs.
* **REST:** Representational State Transfer; an architectural style for network APIs.
* **Webhook:** An HTTP POST callback mechanism for asynchronous event notification.
* **Organization:** The highest tenant boundary in Lyra, containing multiple projects and environments.
* **Project:** A specific workspace under an organization containing associated agents, playbooks, and contracts.
* **Environment:** A deployment instance of a project (e.g., dev, staging, production).
* **Protocol Adapter:** An edge translation module converting transport-specific requests (REST, WebSockets) into internal Lyra events.
* **STT (Speech-to-Text):** The speech processing adapter module that converts incoming audio stream packets or binary audio blocks into textual dialogue tokens.
* **TTS (Text-to-Speech):** The speech synthesis adapter module that translates textual dialogue system turns into synthesized voice audio streams.
* **PII Redaction:** The automated privacy screening layer that identifies and redacts personally identifiable information (e.g., patient name, social security numbers, credentials) from transcripts before long-term storage.
* **Linear History:** The development workflow style requiring feature branches to be rebased against main and squash-merged to preserve a clear, linear progression of commits.
* **Maturity Status:** The metadata classification representing the implementation authority level of a document (e.g., Placeholder, Draft, Approved, Implementation Ready).
* **Schema Validation Error:** A runtime validation failure raised by the Contract Layer when capability arguments or returned structures violate registered JSON schema models.

