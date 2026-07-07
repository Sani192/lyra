# Restaurant Consumer Contract

## Maturity Metadata

**Status:** Approved.

**Intended Use:** Reference integration guidance demonstrating a registered consumer contract in the restaurant domain.

---

```json
{
  "id": "contract.restaurant.01",
  "organization_id": "org.gourmet_group",
  "project_id": "project.booking_assistant",
  "version": "1.0.0",
  "capabilities": [
    {
      "id": "lyra.examples.restaurant.check_availability",
      "name": "Check Table Availability",
      "protocol": "REST",
      "endpoint": "https://api.gourmet.example/v1/booking/check",
      "parameters": {
        "type": "object",
        "properties": {
          "date": { "type": "string", "format": "date" },
          "time": { "type": "string" },
          "guests": { "type": "integer", "minimum": 1 }
        },
        "required": ["date", "time", "guests"]
      }
    },
    {
      "id": "lyra.examples.restaurant.create_booking",
      "name": "Create Table Booking",
      "protocol": "REST",
      "endpoint": "https://api.gourmet.example/v1/booking/create",
      "parameters": {
        "type": "object",
        "properties": {
          "date": { "type": "string", "format": "date" },
          "time": { "type": "string" },
          "guests": { "type": "integer", "minimum": 1 },
          "customer_name": { "type": "string" },
          "customer_phone": { "type": "string" }
        },
        "required": ["date", "time", "guests", "customer_name", "customer_phone"]
      }
    }
  ],
  "authentication": {
    "type": "apiKey",
    "config": {
      "header_name": "X-Gourmet-API-Key"
    }
  }
}
```
