# 02 Core Principles

## Maturity Metadata

**Status:** Approved.

**Intended Use:** Authoritative AI-agent operating context; safe for repository navigation and contribution workflow decisions.

## Purpose

Define the non-negotiable architectural principles that govern Lyra, explaining the engineering rationale behind the stateless boundary between Lyra and consumer systems.

## The Core Principles

### 1. Stateless Orchestration
Lyra does not store business transaction data. It acts as an active router and coordinator, maintaining conversation state (e.g., turns, session ID, active prompt context) only for the duration of the conversation, while delegating persistent domain records (e.g., patient charts, booking lists) to consumer APIs.
- *Rationale:* Keeping Lyra stateless ensures it scales horizontally without database synchronization bottlenecks and isolates it from complex compliance scopes (like HIPAA or PCI-DSS) that govern consumer systems of record.

### 2. Consumer Business Logic Ownership
Lyra never makes business policy decisions. Decisions like "is this user eligible for a discount?" or "is this reservation slot available?" must be resolved by invoking a capability registered by the consumer application.
- *Rationale:* If business logic was embedded in Lyra, every change to a consumer's business rules would require modifying and redeploying Lyra components. By delegating rules, Lyra remains a domain-agnostic platform.

### 3. Contract-Driven Integrations
All communications between Lyra and external applications must conform to strict schemas registered in the Capability Registry. Lyra validates all inputs and outputs at the interface boundary.

## Correct Design Example

```
Correct:
User: "Can I book a table at 7 PM?"
Lyra -> Check capability contract -> Invoke restaurant.check_availability(time="19:00")
Restaurant API -> Return {"available": true}
Lyra -> User: "Yes, that slot is open."

Incorrect:
User: "Can I book a table at 7 PM?"
Lyra -> Query local restaurant_slots database -> Find 7 PM slot
Lyra -> Calculate booking eligibility using internal rules
Lyra -> User: "Yes, booked."
```

## Review Checklist

- [ ] Proposed changes keep data persistence within the consumer system of record.
- [ ] No local business rule evaluation is added to the Conversation Engine.
- [ ] Capabilities are registered with strict validation schemas.
