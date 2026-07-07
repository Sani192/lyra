# Clinic Consumer Contract

## Maturity Metadata

**Status:** Approved.

**Intended Use:** Reference integration guidance demonstrating a registered consumer contract in the healthcare domain.

---

```json
{
  "id": "contract.clinic.01",
  "organization_id": "org.health_care_network",
  "project_id": "project.scheduling_assistant",
  "version": "1.0.0",
  "capabilities": [
    {
      "id": "lyra.examples.clinic.lookup_slots",
      "name": "Lookup Appointment Slots",
      "protocol": "REST",
      "endpoint": "https://api.healthcare.example/v1/appointments/slots",
      "parameters": {
        "type": "object",
        "properties": {
          "department": { "type": "string", "enum": ["general", "dental", "pediatric"] },
          "start_date": { "type": "string", "format": "date" },
          "end_date": { "type": "string", "format": "date" }
        },
        "required": ["department", "start_date", "end_date"]
      }
    },
    {
      "id": "lyra.examples.clinic.book_appointment",
      "name": "Book Appointment",
      "protocol": "REST",
      "endpoint": "https://api.healthcare.example/v1/appointments/book",
      "parameters": {
        "type": "object",
        "properties": {
          "slot_id": { "type": "string" },
          "patient_name": { "type": "string" },
          "insurance_id": { "type": "string" }
        },
        "required": ["slot_id", "patient_name", "insurance_id"]
      }
    }
  ],
  "authentication": {
    "type": "apiKey",
    "config": {
      "header_name": "X-Clinic-Auth"
    }
  }
}
```
