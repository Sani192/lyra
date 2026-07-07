# ERP Consumer Contract

## Maturity Metadata

**Status:** Approved.

**Intended Use:** Reference integration guidance demonstrating a registered consumer contract in the enterprise resource planning domain.

---

```json
{
  "id": "contract.erp.01",
  "organization_id": "org.supply_chain_corp",
  "project_id": "project.tracking_assistant",
  "version": "1.0.0",
  "capabilities": [
    {
      "id": "lyra.examples.erp.get_order_details",
      "name": "Get Order Details",
      "protocol": "REST",
      "endpoint": "https://api.supplychain.example/v1/orders/details",
      "parameters": {
        "type": "object",
        "properties": {
          "order_id": { "type": "string", "pattern": "^ORD-[0-9]+$" },
          "zip_code": { "type": "string" }
        },
        "required": ["order_id", "zip_code"]
      }
    },
    {
      "id": "lyra.examples.erp.get_shipment_tracking",
      "name": "Get Shipment Tracking",
      "protocol": "REST",
      "endpoint": "https://api.supplychain.example/v1/orders/tracking",
      "parameters": {
        "type": "object",
        "properties": {
          "order_id": { "type": "string" }
        },
        "required": ["order_id"]
      }
    }
  ],
  "authentication": {
    "type": "apiKey",
    "config": {
      "header_name": "X-ERP-Token"
    }
  }
}
```
