# Hotel Reservation Capabilities

## Maturity Metadata

**Status:** Approved.

**Intended Use:** Reference integration guidance demonstrating capability declarations for the hotel/hospitality domain.

---

### 1. `lyra.examples.hotel.check_rooms`
- **Description:** Search available rooms by check-in/check-out dates and room type.
- **Parameters:**
  - `checkin_date`: String (Format: `YYYY-MM-DD`, required)
  - `checkout_date`: String (Format: `YYYY-MM-DD`, required)
  - `room_type`: String (Enum: `["standard", "double", "suite"]`, required)
- **Returns:**
  - `available`: Boolean
  - `price_per_night`: Number
  - `total_price`: Number

### 2. `lyra.examples.hotel.book_room`
- **Description:** Commits the room reservation.
- **Parameters:**
  - `checkin_date`: String (Format: `YYYY-MM-DD`, required)
  - `checkout_date`: String (Format: `YYYY-MM-DD`, required)
  - `room_type`: String (required)
  - `guest_name`: String (required)
  - `guest_email`: String (required)
- **Returns:**
  - `reservation_id`: String (Format: `HOT-XXXXX`)
  - `status`: String (`confirmed`)
