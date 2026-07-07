# ERP Order Tracking Conversation Flow

## Maturity Metadata

**Status:** Approved.

**Intended Use:** Reference integration guidance demonstrating ERP order tracking dialogs and capability execution.

---

### Turn-by-Turn Dialog Log

1. **User:** "Hi, I'm calling to check the status of my order ORD-9821."
   - *Lyra Action:* Extracts entities (`order_id="ORD-9821"`). Maps intent `track_order`.
   - *Lyra:* "I can help with that. For security verification, could you tell me the billing zip code for this order?"
   - *User:* "Sure, it is 94105."
   - *Lyra Action:* Extracts entities (`zip_code="94105"`).
   - *Invocation:* Invokes capability `lyra.examples.erp.get_order_details`.
   - *Response:* Consumer returns `{"order_id": "ORD-9821", "status": "shipped", "items": ["Widgets", "Gadgets"], "total_price": 79.99}`.

2. **Lyra:** "Order ORD-9821 containing Widgets and Gadgets has shipped. Would you like me to fetch the shipping tracking details?"
   - *User:* "Yes, please."
   - *Invocation:* Invokes capability `lyra.examples.erp.get_shipment_tracking`.
   - *Response:* Consumer returns `{"tracking_number": "TRK-1234567890", "carrier": "FedEx", "status": "In Transit", "estimated_delivery": "2026-07-10T15:00:00Z"}`.

3. **Lyra:** "Your package is in transit via FedEx, tracking code TRK-1234567890. It is estimated to be delivered on July 10th by 3:00 PM."
