# Payment Followup Playbook

## Maturity Metadata

**Status:** Approved.

**Intended Use:** Dialogue orchestration guidance for payment reminder and tracking flows.

## Goal

Notify a customer of an overdue invoice, confirm payment details, and record the payment follow-up status in the ERP billing system.

## Conversation Strategy

1. **Verify Identity:** Authenticate the user by verifying their customer ID and invoice number.
2. **State Balance:** Detail the outstanding invoice amounts and dates.
3. **Collect Status:** Inquire if the invoice has been paid or if they want to pay now.
4. **Log Resolution:** Call `update_invoice_status` to log their response.

## Capability Usage

Never store credit card or bank details in Lyra. Direct customers to secure PCI-compliant gateways via external links or protocol-isolated IVR transfers.

## Failure Recovery

- **Invoice Dispute:** If the customer disagrees with the balance, mark the invoice as "disputed" in the ERP capability call and log their feedback in notes.

## Escalation

Transfer to the collections or billing department if:
- The customer requests payment extensions or budget arrangements.
- The customer refuses to pay or threatens legal action.

## Success Criteria

The invoice record is updated in the ERP system with follow-up metadata (e.g. "promised to pay by July 15th").
