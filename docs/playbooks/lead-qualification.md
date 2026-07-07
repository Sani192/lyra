# Lead Qualification Playbook

## Maturity Metadata

**Status:** Approved.

**Intended Use:** Dialogue orchestration guidance for lead intake and qualification.

## Goal

Gather business context from a prospect, determine their project budget, and record a qualified sales opportunity in the CRM.

## Conversation Strategy

1. **Intake Context:** Ask for name, company name, and email.
2. **Qualify Needs:** Gather project details (scope, timeline, estimated budget).
3. **Trigger Search:** Call `search_leads` to verify if a lead already exists.
4. **Log Opportunity:** Call `update_lead_status` or `create_lead` to record details.

## Capability Usage

Ensure all gathered parameters are validated against CRM lead insertion schemas before invoking.

## Failure Recovery

- **Duplicated Lead:** If `search_leads` returns an active contact, state: "It looks like we already have a record for your company. I've updated John Doe to contact you."

## Escalation

Transfer to a live sales representative if:
- The prospect's budget exceeds the high-enterprise threshold.
- The prospect requests specific pricing quotes or custom contracts.

## Success Criteria

A validated lead is registered in the CRM system with complete qualification tags.
