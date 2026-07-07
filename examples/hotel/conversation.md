# Hotel Room Booking Conversation Flow

## Maturity Metadata

**Status:** Approved.

**Intended Use:** Reference integration guidance demonstrating hotel room booking dialogs and capability execution.

---

### Turn-by-Turn Dialog Log

1. **User:** "Hi, I want to book a double room from July 20th to July 23rd."
   - *Lyra Action:* Extracts entities (`checkin_date="2026-07-20"`, `checkout_date="2026-07-23"`, `room_type="double"`). Maps intent `request_booking`.
   - *Invocation:* Invokes capability `lyra.examples.hotel.check_rooms`.
   - *Response:* Consumer returns `{"available": true, "price_per_night": 150.00, "total_price": 450.00}`.

2. **Lyra:** "A double room is available for those dates. The rate is $150 per night, totaling $450 for the 3 nights. Shall I reserve this for you?"
   - *User:* "Yes, please."
   - *Lyra Action:* Prompts for guest details.
   - *Lyra:* "Could you provide your name and email address to confirm the booking?"
   - *User:* "Sure, my name is Morgan Lee and my email is morgan@example.com."
   - *Lyra Action:* Extracts entities (`guest_name="Morgan Lee"`, `guest_email="morgan@example.com"`).
   - *Invocation:* Invokes capability `lyra.examples.hotel.book_room`.
   - *Response:* Consumer returns `{"reservation_id": "HOT-78810", "status": "confirmed"}`.

3. **Lyra:** "Thank you, Morgan. Your double room is reserved from July 20th to July 23rd. Your reservation number is HOT-78810."
