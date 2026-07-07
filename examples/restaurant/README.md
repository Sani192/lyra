# Restaurant Example

## Business Context

This example shows how Lyra can orchestrate a restaurant conversation without becoming the system of record. The consumer application owns domain data, policies, and final business decisions.

## Conversation

See [`conversation.md`](./conversation.md) for a representative customer interaction and turn-by-turn context.

## Consumer Contract

See [`consumer-contract.md`](./consumer-contract.md). The contract describes the capabilities Lyra may invoke, required inputs, expected outputs, and error behavior.

## Capabilities

See [`capabilities.md`](./capabilities.md). Capabilities are declared actions owned by the consumer application and discovered by Lyra through contract metadata.

## Expected Tool Invocations

Lyra should invoke only declared capabilities, pass confirmed entities as inputs, record invocation metadata, and use the consumer response as authoritative.

## Expected JSON

See [`expected.json`](./expected.json) for the expected structured outcome. The JSON is illustrative test evidence, not consumer business state owned by Lyra.

## Failure Scenarios

* Required customer information is missing or ambiguous.
* A capability returns validation, authorization, unavailable, timeout, or conflict errors.
* The consumer contract version is incompatible with the configured environment.
* The customer requests a business decision that must be made by the consumer application or a human.

## Edge Cases

* Customer changes intent mid-conversation.
* Customer provides conflicting entity values.
* Capability succeeds but webhook delivery is delayed.
* Escalation is required because confidence or contract validation is insufficient.
