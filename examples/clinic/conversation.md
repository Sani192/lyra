# Clinic Appointment Conversation Flow

## Maturity Metadata

**Status:** Approved.

**Intended Use:** Reference integration guidance demonstrating clinic scheduling dialogs and capability execution.

---

### Turn-by-Turn Dialog Log

1. **User:** "I'd like to book a dental checkup next Tuesday, July 14th."
   - *Lyra Action:* Extracts entities (`department="dental"`, `start_date="2026-07-14"`, `end_date="2026-07-14"`). Maps intent `request_appointment`.
   - *Invocation:* Invokes capability `lyra.examples.clinic.lookup_slots`.
   - *Response:* Consumer returns `{"slots": [{"slot_id": "SLOT-998", "time": "10:00 AM", "doctor": "Dr. Miller"}]}`.

2. **Lyra:** "I found an open dental checkup slot next Tuesday at 10:00 AM with Dr. Miller. Would you like to schedule that?"
   - *User:* "Yes, please."
   - *Lyra Action:* Prompts for patient confirmation data.
   - *Lyra:* "To complete this booking, could I get your full name and health insurance identifier?"
   - *User:* "Sure, my name is Robin Doe and my insurance ID is INS-12345."
   - *Lyra Action:* Extracts entities (`patient_name="Robin Doe"`, `insurance_id="INS-12345"`).
   - *Invocation:* Invokes capability `lyra.examples.clinic.book_appointment`.
   - *Response:* Consumer returns `{"appointment_id": "APT-55201", "status": "scheduled"}`.

3. **Lyra:** "Great. Your dental appointment is confirmed for Tuesday, July 14th at 10:00 AM with Dr. Miller. Your booking code is APT-55201."
