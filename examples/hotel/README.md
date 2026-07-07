# Hotel Example

## Maturity Metadata

**Status:** Approved.

**Intended Use:** Reference integration guidance illustrating the hotel room booking domain.

---

## Business Context

This example demonstrates how Lyra coordinates hotel room reservations. Under the stateless project rules, room inventories, room pricing changes, and credit card verification logic remain within the hotel application.

## Scenarios Covered

1. **Room Lookup:** Searching room lists dynamically (`lyra.examples.hotel.check_rooms`).
2. **Room Booking:** Submitting booking requests (`lyra.examples.hotel.book_room`).

## Domain Artifacts

- **Capabilities:** Defined in [capabilities.md](./capabilities.md).
- **Contract:** Defined in [consumer-contract.md](./consumer-contract.md).
- **Conversation Turns:** Logged in [conversation.md](./conversation.md).
- **Expected Outcome JSON:** Conforms to `schemas/conversation.schema.json` and is in [expected.json](./expected.json).
