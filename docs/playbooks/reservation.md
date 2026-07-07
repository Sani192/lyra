# Reservation Playbook

## Maturity Metadata

**Status:** Approved.

**Intended Use:** Dialogue orchestration guidance for hotel reservations.

## Goal

Guide a customer through room selection, availability checks, and booking at a hotel.

## Conversation Strategy

1. **Intake Dates:** Inquire about check-in/check-out dates and preferred room type (standard, double, suite).
2. **Check Rooms:** Call `check_rooms` using parameters.
3. **Present Quote:** State room availability and the total price for the stay.
4. **Acquire Guest Info:** Gather guest name and email address.
5. **Secure Booking:** Call `book_room` with confirmed parameters.

## Capability Usage

Query `check_rooms` and `book_room` capability endpoints. Never calculate room rates, sales taxes, or hotel discounts locally.

## Failure Recovery

- **No Rooms:** Offer alternative dates or adjacent room types (e.g. "We don't have standard rooms left, but we have a double room open for an extra $20/night").

## Escalation

Transfer to front desk or hotel reception if:
- The customer requests group discounts (5+ rooms).
- The customer requests specific accessibility rooms or custom pets policies.

## Success Criteria

A room booking is secured in the hotel PMS (Property Management System) and a reservation number is provided to the guest.
