# Restaurant Conversation Flow

## Maturity Metadata

**Status:** Approved.

**Intended Use:** Reference integration guidance demonstrating turn-taking dialogue and capability invocation loops for the restaurant domain.

---

### Turn-by-Turn Dialog Log

1. **User:** "Hi, I'd like to book a table for 4 people tonight at 7 PM."
   - *Lyra Action:* Extracts entities (`date="2026-07-07"`, `guests=4`, `time="19:00"`). Maps intent `request_booking`.
   - *Invocation:* Invokes capability `lyra.examples.restaurant.check_availability`.
   - *Response:* Consumer returns `{"available": true}`.

2. **Lyra:** "Great news, we have availability at 7 PM. Can I get your name and phone number to finalize the reservation?"
   - *User:* "Sure, it's Alex Smith and my number is 555-0199."
   - *Lyra Action:* Extracts entities (`customer_name="Alex Smith"`, `customer_phone="555-0199"`).
   - *Invocation:* Invokes capability `lyra.examples.restaurant.create_booking`.
   - *Response:* Consumer returns `{"booking_id": "RES-82910", "status": "confirmed"}`.

3. **Lyra:** "Perfect. Your table for 4 is booked tonight at 7 PM. Your reservation code is RES-82910. We look forward to seeing you!"
