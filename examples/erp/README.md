# ERP Example

## Maturity Metadata

**Status:** Approved.

**Intended Use:** Reference integration guidance illustrating the ERP supply chain and order management domain.

---

## Business Context

This example demonstrates how Lyra coordinates enterprise order tracking dialogs. Under stateless architectural constraints, order shipping tracking systems, shipping calculations, and inventory databases are managed by the ERP system.

## Scenarios Covered

1. **Order Details Lookup:** Searching order logs dynamically (`lyra.examples.erp.get_order_details`).
2. **Shipment Tracking:** Retrieving carrier telemetry (`lyra.examples.erp.get_shipment_tracking`).

## Domain Artifacts

- **Capabilities:** Defined in [capabilities.md](./capabilities.md).
- **Contract:** Defined in [consumer-contract.md](./consumer-contract.md).
- **Conversation Turns:** Logged in [conversation.md](./conversation.md).
- **Expected Outcome JSON:** Conforms to `schemas/conversation.schema.json` and is in [expected.json](./expected.json).
