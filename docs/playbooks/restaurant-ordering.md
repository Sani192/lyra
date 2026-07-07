# Restaurant Ordering Playbook

## Goal

Guide a customer through a restaurant ordering conversation while invoking only consumer-declared capabilities.

## Conversation Strategy

Confirm intent, gather required entities, validate through consumer capabilities, summarize outcomes, and capture transcript events.

## Capability Usage

Use the capability registry to discover eligible actions. Lyra must not infer business eligibility beyond contract responses.

## Failure Recovery

If a capability is unavailable, explain the limitation, retry when safe, offer alternatives declared by the consumer, or escalate.

## Escalation

Escalate when identity, safety, payment, policy ambiguity, or repeated capability failure prevents reliable completion.

## Success Criteria

The customer receives a clear outcome, the consumer application remains the source of truth, and Lyra records observable conversation and invocation events.
