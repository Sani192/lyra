# CRM Lead Status Conversation Flow

## Maturity Metadata

**Status:** Approved.

**Intended Use:** Reference integration guidance demonstrating CRM lead qualification dialogs and capability execution.

---

### Turn-by-Turn Dialog Log

1. **User:** "Hi, I need to check the status of our sales lead at 'Apex Tech'."
   - *Lyra Action:* Extracts entities (`company_name="Apex Tech"`). Maps intent `search_leads`.
   - *Invocation:* Invokes capability `lyra.examples.crm.search_leads`.
   - *Response:* Consumer returns `{"leads": [{"lead_id": "LEAD-8871", "name": "Apex Tech Sales Opportunity", "status": "contacted", "assigned_agent": "John Doe"}]}`.

2. **Lyra:** "I found a lead for 'Apex Tech' with ID LEAD-8871. The status is currently 'contacted' and it is assigned to John Doe. Would you like to update this stage?"
   - *User:** "Yes, we just completed the call. Let's mark it as 'qualified'."
   - *Lyra Action:* Extracts entities (`new_status="qualified"`).
   - *Invocation:* Invokes capability `lyra.examples.crm.update_lead_status`.
   - *Response:* Consumer returns `{"lead_id": "LEAD-8871", "updated_status": "qualified", "status": "updated"}`.

3. **Lyra:** "Perfect. The lead status for Apex Tech (LEAD-8871) has been updated to 'qualified'."
