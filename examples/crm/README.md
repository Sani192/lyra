# CRM Example

## Maturity Metadata

**Status:** Approved.

**Intended Use:** Reference integration guidance illustrating the CRM customer and lead management domain.

---

## Business Context

This example demonstrates how Lyra coordinates CRM sales lead updates. To prevent state ownership violations, customer logs, contact database schemas, and lead conversion business rules are managed by the CRM application.

## Scenarios Covered

1. **Lead Lookup:** Searching customer logs dynamically (`lyra.examples.crm.search_leads`).
2. **Status updates:** Advancing opportunity stages (`lyra.examples.crm.update_lead_status`).

## Domain Artifacts

- **Capabilities:** Defined in [capabilities.md](./capabilities.md).
- **Contract:** Defined in [consumer-contract.md](./consumer-contract.md).
- **Conversation Turns:** Logged in [conversation.md](./conversation.md).
- **Expected Outcome JSON:** Conforms to `schemas/conversation.schema.json` and is in [expected.json](./expected.json).
