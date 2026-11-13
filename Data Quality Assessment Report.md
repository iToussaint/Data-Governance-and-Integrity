# Data Quality Assessment Report

**Organisation:** MedTrack Rwanda

**Dataset:** Patient appointment records (PatientID, PatientName, Phone, Doctor, AppointmentDate, PaymentStatus)

**Applicable law:** Law No. 058/2021 relating to the Protection of Personal Data and Privacy (Rwanda)

Patient records include medical information, which is **sensitive personal data** under the law (Art. 3). Article 15 requires MedTrack to keep personal data **complete, accurate, up to date and not misleading**. Every issue below is therefore a compliance risk as well as a technical one.

---

## 1. Data Quality Findings (by Dimension)

| Dimension | Issue Found | Evidence | Impact |
|-----------|-------------|----------|--------|
| **Accuracy** | One patient has two conflicting phone numbers | P002: `244789012` and `0244789012` | MedTrack cannot tell which number is correct, so reminders may go to the wrong number. Breaks the accuracy duty (Arts. 15, 37). |
| **Completeness** | A required field is empty | P004: `PatientName` is blank | The patient cannot be identified for treatment or billing. Breaks the completeness duty (Art. 15). |
| **Consistency** | The same value is written in different ways | `Dr. Osei` vs `dr. osei`; `Paid` vs `paid` | Reports count one doctor or one status as two, so totals are wrong. |
| **Timeliness** | Appointment dates are stored in mixed formats, so the system cannot reliably tell *when* an appointment is | `2025-10-15` vs `10/16/2025` | Reminders can be sent on the wrong day (month and day may be swapped), or after the appointment has passed. |
| **Validity** | Phone numbers do not follow the Rwandan format (10 digits starting with `07`, or `+250` followed by 9 digits) | `244789012` has 9 digits and no leading `0`; `0244789012` is not a Rwandan mobile prefix | The SMS gateway rejects these numbers, so the patient gets no reminders. |
| **Uniqueness** | Patient records are duplicated | P001 and P002 appear more than once | Patients are counted twice and may be billed twice. |

---

## 2. Business Impact Analysis

- **Patient care:** A missing name (P004) and duplicated records make it hard for doctors to find the right patient history. This risks treatment errors.
- **Operations:** Invalid phone numbers and ambiguous dates cause failed or mistimed SMS reminders, which leads to missed appointments.
- **Finance:** Duplicate records and inconsistent payment statuses cause double billing and reports that don't reconcile.
- **Compliance:** Inaccurate or incomplete health data breaches Art. 15. Patients can also ask for corrections (Art. 24), and MedTrack must respond **within 30 days**.

---

## 3. Recommended Solutions (Top 3 Critical Issues)

| Critical Issue | Technical Solution | Responsibility | Verification |
|----------------|-------------------|----------------|--------------|
| **Uniqueness:** duplicate patient records | Merge the duplicates, then add a **unique constraint** on `PatientID` in the database so duplicates can't be created again | Database Administrator | A query showing the number of distinct `PatientID` values equals the total number of rows |
| **Validity / Accuracy:** invalid and conflicting phone numbers | Confirm the correct number with each affected patient. Add **input validation** that only accepts the Rwandan format (`07XXXXXXXX` or `+2507XXXXXXXX`) and stores one standard format | Backend Developer | A validation query returns no invalid numbers, and SMS gateway logs show no "invalid number" errors |
| **Consistency / Timeliness:** mixed date and text formats | Convert all dates to **ISO 8601 (`YYYY-MM-DD`)**. Use date pickers and dropdowns (doctor, payment status) instead of free text | Backend Developer / Data Engineer | A query finds no dates outside the ISO format and one spelling per doctor and status. Reminders go out on the correct day. |

---

## 4. Biggest Risk of Poor Data Consistency

The biggest risk is that **automated systems fail without anyone noticing**. Reminders, billing and reports all depend on data being in one predictable format. When the same date or name is stored in different ways, these systems send reminders on the wrong day, count patients twice, or skip records entirely, often without raising an error. Wrong decisions are then made from data that looks correct. For a health platform, that means missed appointments, billing mistakes and breaches of the accuracy duty under Art. 15.

---

## 5. Conclusion

The MedTrack dataset has problems in all six data quality dimensions. Adding database constraints, input validation and standard formats will fix the current errors and stop new ones from entering. This will keep patient data reliable and compliant with Rwanda's data protection law.
