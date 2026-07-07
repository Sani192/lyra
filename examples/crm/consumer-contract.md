# CRM Consumer Contract

## Maturity Metadata

**Status:** Approved.

**Intended Use:** Reference integration guidance demonstrating a registered consumer contract in the customer relationship management domain.

---

```json
{
  "id": "contract.crm.01",
  "organization_id": "org.sales_force_network",
  "project_id": "project.crm_assistant",
  "version": "1.0.0",
  "capabilities": [
    {
      "id": "lyra.examples.crm.search_leads",
      "name": "Search Leads",
      "protocol": "REST",
      "endpoint": "https://api.crm.example/v1/leads/search",
      "parameters": {
        "type": "object",
        "properties": {
          "company_name": { "type": "string" },
          "customer_email": { "type": "string" }
        }
      }
    },
    {
      "id": "lyra.examples.crm.update_lead_status",
      "name": "Update Lead Status",
      "protocol": "REST",
      "endpoint": "https://api.crm.example/v1/leads/status",
      "parameters": {
        "type": "object",
        "properties": {
          "lead_id": { "type": "string" },
          "new_status": { "type": "string", "enum": ["contacted", "qualified", "lost", "won"] },
          "notes": { "type": "string" }
        },
        "required": ["lead_id", "new_status"]
      }
    }
  ],
  "authentication": {
    "type": "apiKey",
    "config": {
      "header_name": "X-CRM-Key"
    }
  }
}
```
