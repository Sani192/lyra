# Hotel Consumer Contract

## Maturity Metadata

**Status:** Approved.

**Intended Use:** Reference integration guidance demonstrating a registered consumer contract in the hospitality domain.

---

```json
{
  "id": "contract.hotel.01",
  "organization_id": "org.luxury_stays",
  "project_id": "project.booking_assistant",
  "version": "1.0.0",
  "capabilities": [
    {
      "id": "lyra.examples.hotel.check_rooms",
      "name": "Check Room Availability",
      "protocol": "REST",
      "endpoint": "https://api.luxurystays.example/v1/rooms/check",
      "parameters": {
        "type": "object",
        "properties": {
          "checkin_date": { "type": "string", "format": "date" },
          "checkout_date": { "type": "string", "format": "date" },
          "room_type": { "type": "string", "enum": ["standard", "double", "suite"] }
        },
        "required": ["checkin_date", "checkout_date", "room_type"]
      }
    },
    {
      "id": "lyra.examples.hotel.book_room",
      "name": "Reserve Room",
      "protocol": "REST",
      "endpoint": "https://api.luxurystays.example/v1/rooms/book",
      "parameters": {
        "type": "object",
        "properties": {
          "checkin_date": { "type": "string", "format": "date" },
          "checkout_date": { "type": "string", "format": "date" },
          "room_type": { "type": "string" },
          "guest_name": { "type": "string" },
          "guest_email": { "type": "string" }
        },
        "required": ["checkin_date", "checkout_date", "room_type", "guest_name", "guest_email"]
      }
    }
  ],
  "authentication": {
    "type": "apiKey",
    "config": {
      "header_name": "X-Hotel-Auth"
    }
  }
}
```
