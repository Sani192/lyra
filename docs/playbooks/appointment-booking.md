# Appointment Booking Playbook

## Maturity Metadata

**Status:** Approved.

**Intended Use:** Dialogue orchestration guidance for AI agents and Conversation Engines coordinating appointment bookings.

## Goal

Guide a customer through identifying open scheduling slots and securing a medical or dental appointment.

## Conversation Strategy

1. **Gathers Intent:** Inquire about the requested department or doctor and target date range.
2. **Retrieve Slots:** Call `lookup_slots` using dates and department.
3. **Select Slot:** Present available slot options clearly to the user.
4. **Collect Demographics:** Ask for patient's full name and insurance identifier once a slot is chosen.
5. **Secure Booking:** Call `book_appointment` with confirmed parameters.
6. **Confirm Booking:** State the appointment confirmation ID, date, time, and doctor.

## Capability Usage

Only invoke `lookup_slots` and `book_appointment` registered capabilities. Never declare slot availability or pricing details locally.

## Failure Recovery

- **No Slots Available:** If the query returns no slots, offer adjacent dates (e.g. "I don't see openings next Tuesday, but we have slots on Wednesday").
- **Auth or Timeout Error:** State: "I'm having trouble reaching our scheduling system right now. Let me try again in a moment."

## Escalation

Immediately escalate to a human clinic staff member if:
- The customer describes an active medical emergency.
- The insurance validation fails repeatedly.
- The customer requests scheduling rules or doctor policies not declared in the capability returns.

## Success Criteria

The patient's appointment is successfully logged in the clinic system of record, and the patient receives a confirmed booking ID.
