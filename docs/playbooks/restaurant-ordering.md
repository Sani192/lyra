# Restaurant Ordering Playbook

## Maturity Metadata

**Status:** Approved.

**Intended Use:** Dialogue orchestration guidance for restaurant table bookings and food orders.

## Goal

Guide a customer through booking a table or ordering menu items at a restaurant.

## Conversation Strategy

1. **Detect Intent:** Parse whether the user wants to reserve a table or order food.
2. **Table Booking path:**
   - Inquire about guest count, date, and time.
   - Invoke `check_availability`.
   - Collect name/phone and invoke `create_booking`.
3. **Food Ordering path:**
   - Inquire about dishes and quantities.
   - Invoke `check_menu` or `verify_dishes`.
   - Collect pickup/delivery coordinates and invoke `submit_order`.

## Capability Usage

Invoke only registered capability endpoints. Never validate menu availability or table reservation states locally.

## Failure Recovery

- **Capability Failure:** If checking availability fails, apologize and offer to transfer to the host stand.

## Escalation

Transfer to the restaurant manager if:
- The customer reports severe food allergies.
- The customer requests custom substitutions not listed in the menu capability response.

## Success Criteria

A reservation code or food order ID is returned from the restaurant system and stated to the customer.
