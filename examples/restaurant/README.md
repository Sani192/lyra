# Restaurant Example

## Maturity Metadata

**Status:** Approved.

**Intended Use:** Reference integration guidance illustrating the restaurant table booking domain.

---

## Business Context

This example demonstrates how Lyra orchestrates restaurant booking dialogs without assuming control over reservations databases or table policies. The consumer application owns the table inventory and validation rules.

## Scenarios Covered

1. **Table Check:** Searching table availability dynamically (`lyra.examples.restaurant.check_availability`).
2. **Booking finalization:** Committing the reservation (`lyra.examples.restaurant.create_booking`).

## Domain Artifacts

- **Capabilities:** Defined in [capabilities.md](./capabilities.md).
- **Contract:** Defined in [consumer-contract.md](./consumer-contract.md).
- **Conversation Turns:** Logged in [conversation.md](./conversation.md).
- **Expected Outcome JSON:** Conforms to `schemas/conversation.schema.json` and is in [expected.json](./expected.json).
