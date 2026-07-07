# Clinic Appointment Capabilities

## Maturity Metadata

**Status:** Approved.

**Intended Use:** Reference integration guidance demonstrating capability declarations for the clinic/healthcare domain.

---

### 1. `lyra.examples.clinic.lookup_slots`
- **Description:** Search available medical/dental slots by doctor department and target date range.
- **Parameters:**
  - `department`: String (Enum: `["general", "dental", "pediatric"]`, required)
  - `start_date`: String (Format: `YYYY-MM-DD`, required)
  - `end_date`: String (Format: `YYYY-MM-DD`, required)
- **Returns:**
  - `slots`: Array of slot objects containing `slot_id` (string), `time` (string), `doctor` (string).

### 2. `lyra.examples.clinic.book_appointment`
- **Description:** Commits the appointment for the patient.
- **Parameters:**
  - `slot_id`: String (required)
  - `patient_name`: String (required)
  - `insurance_id`: String (required)
- **Returns:**
  - `appointment_id`: String (Format: `APT-XXXXX`)
  - `status`: String (`scheduled`)
