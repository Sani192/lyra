# Clinic Example

## Maturity Metadata

**Status:** Approved.

**Intended Use:** Reference integration guidance illustrating the clinic appointment scheduling domain.

---

## Business Context

This example demonstrates how Lyra orchestrates patient appointment scheduling dialogs. To preserve the project constitution, patient health histories and doctors' actual calendars are managed by the clinic application.

## Scenarios Covered

1. **Slots Lookup:** Searching clinic slots dynamically (`lyra.examples.clinic.lookup_slots`).
2. **Appointment booking:** Committing the scheduling request (`lyra.examples.clinic.book_appointment`).

## Domain Artifacts

- **Capabilities:** Defined in [capabilities.md](./capabilities.md).
- **Contract:** Defined in [consumer-contract.md](./consumer-contract.md).
- **Conversation Turns:** Logged in [conversation.md](./conversation.md).
- **Expected Outcome JSON:** Conforms to `schemas/conversation.schema.json` and is in [expected.json](./expected.json).
