# Restaurant Booking Capabilities

## Maturity Metadata

**Status:** Approved.

**Intended Use:** Reference integration guidance demonstrating capability declarations for the restaurant domain.

---

### 1. `lyra.examples.restaurant.check_availability`
- **Description:** Queries available table slots matching a target date, time, and guest count.
- **Parameters:**
  - `date`: String (Format: `YYYY-MM-DD`, required)
  - `time`: String (Format: `HH:MM`, required)
  - `guests`: Integer (Minimum: 1, required)
- **Returns:**
  - `available`: Boolean
  - `available_times`: Array of strings (alternative slots if requested slot is full)

### 2. `lyra.examples.restaurant.create_booking`
- **Description:** Submits a table reservation to the restaurant's booking system.
- **Parameters:**
  - `date`: String (Format: `YYYY-MM-DD`, required)
  - `time`: String (Format: `HH:MM`, required)
  - `guests`: Integer (required)
  - `customer_name`: String (required)
  - `customer_phone`: String (required)
- **Returns:**
  - `booking_id`: String (format: `RES-XXXXX`)
  - `status`: String (`confirmed`)
