# ERP Order and Tracking Capabilities

## Maturity Metadata

**Status:** Approved.

**Intended Use:** Reference integration guidance demonstrating capability declarations for the ERP/enterprise inventory domain.

---

### 1. `lyra.examples.erp.get_order_details`
- **Description:** Retrieve billing and shipping status for a specific enterprise order ID.
- **Parameters:**
  - `order_id`: String (Pattern: `^ORD-[0-9]+$`, required)
  - `zip_code`: String (for security verification, required)
- **Returns:**
  - `order_id`: String
  - `status`: String (Enum: `["processing", "shipped", "delivered", "cancelled"]`)
  - `items`: Array of strings
  - `total_price`: Number

### 2. `lyra.examples.erp.get_shipment_tracking`
- **Description:** Queries real-time shipping carrier telemetry for a specific order.
- **Parameters:**
  - `order_id`: String (required)
- **Returns:**
  - `tracking_number`: String
  - `carrier`: String (e.g. `FedEx`, `UPS`)
  - `status`: String (e.g. `In Transit`, `Out for Delivery`)
  - `estimated_delivery`: String (Format: `date-time`)
