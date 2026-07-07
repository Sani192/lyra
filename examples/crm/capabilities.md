# CRM Lead Management Capabilities

## Maturity Metadata

**Status:** Approved.

**Intended Use:** Reference integration guidance demonstrating capability declarations for the CRM/customer management domain.

---

### 1. `lyra.examples.crm.search_leads`
- **Description:** Search customer leads by company name or customer email.
- **Parameters:**
  - `company_name`: String (optional)
  - `customer_email`: String (optional)
- **Returns:**
  - `leads`: Array of lead objects containing `lead_id` (string), `name` (string), `status` (string), `assigned_agent` (string).

### 2. `lyra.examples.crm.update_lead_status`
- **Description:** Updates the status stage of a specific CRM lead.
- **Parameters:**
  - `lead_id`: String (required)
  - `new_status`: String (Enum: `["contacted", "qualified", "lost", "won"]`, required)
  - `notes`: String (optional)
- **Returns:**
  - `lead_id`: String
  - `updated_status`: String
  - `status`: String (`updated`)
