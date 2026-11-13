# Data Access Decision Forms

**Organisation:** EduConnect Rwanda (50,000+ students)

**Role:** DevOps Engineer

**Applicable law:** Law No. 058/2021 relating to the Protection of Personal Data and Privacy (Rwanda)

---

## Form 1 – Marketing Campaign (Sarah Owusu, Marketing Manager)

### Decision: CONDITIONAL APPROVAL

The full student database is denied. Sarah may run the campaign through EduConnect's email platform, without receiving the data herself.

### Lifecycle Stage: USE

Student contact data collected for course delivery would be used for a new purpose, marketing.

### Justification

- **Classification policy:** Email addresses are CONFIDENTIAL, and phone numbers are student PII (CONFIDENTIAL). Sarah only has INTERNAL access, so she cannot receive them.
- **Least privilege:** The campaign needs to *reach* students, not for Marketing to *hold* 50,000 records. Only first names and emails are needed. Phone numbers are not, and enrolments are only needed as aggregated segments (INTERNAL).
- **Compliance:** Data must not be used for a purpose incompatible with the one it was collected for (Art. 37), so marketing needs a lawful basis such as consent (Art. 46). Students can object to direct marketing at any time (Art. 19).
- **Urgency:** A Friday deadline does not justify access above Sarah's clearance.

### Action Steps

1. **Consult** the Data Protection Officer (consent and marketing rules) and the student data owner before final approval.
2. Build a recipient list inside the email platform: **first name and email only**, students who consented to marketing, excluding anyone who has objected.
3. Give Sarah **send-only permission, with no export**, expiring when the campaign ends.
4. **Safeguards:** an unsubscribe link in every message, logging of all access and sends (Art. 16), and no CSV or file exports.
5. Reply to Sarah explaining the decision and the alternative, so the Friday launch goes ahead.
6. Remove her permission after the campaign.

---

## Form 2 – Analytics Partnership (David Mensah, Head of Product)

### Decision: DENY (as submitted)

DataInsights Inc. will not get access to the AWS database. The partnership may be resubmitted once the controls and documents below are in place.

### Lifecycle Stage: SHARE

Student data would be disclosed to an external company outside Rwanda.

### Justification

- **Classification policy:** Student profiles are CONFIDENTIAL. Direct database access would expose them to an outside company.
- **Least privilege:** Analysing learning patterns needs only activity logs, not full database access to every record.
- **Legal / compliance red flags:**
  - **Login credentials attached to the ticket:** they must be treated as compromised. If anyone used them without authorisation, that is a breach to report to the NCSA within 48 hours (Art. 43).
  - **Transfer outside Rwanda without authorisation:** this needs NCSA authorisation with proof of safeguards, or student consent (Art. 48).
  - **No written contract** setting out each party's data protection roles (Art. 49).
  - **Storage outside Rwanda:** personal data must be stored in Rwanda unless EduConnect holds an NCSA certificate allowing storage abroad (Art. 50). The AWS region must be checked.
  - **New purpose:** students were not told their data would go to an analytics company (Art. 37).
  - **No impact assessment** for this high-risk, algorithm-based processing (Art. 38).

### Action Steps

1. **Rotate the shared credentials immediately**, review the access logs, and report to the NCSA within 48 hours if there was unauthorised access.
2. Reply to David with the decision and escalate the signed partnership to Legal and the Data Protection Officer.
3. **Documentation required before resubmission:** a written data transfer contract (Art. 49), NCSA transfer authorisation or student consent (Art. 48), and a data protection impact assessment (Art. 38).
4. **Controls if data is shared:**
   - No direct database access. Provide an **anonymised extract** of activity logs only, with no CONFIDENTIAL profile data.
   - Encrypted transfer and individual, time-limited accounts.
   - Logging of all access (Art. 16).
   - Deletion of the data when the contract ends.

---

## Form 3 – Deletion Request (Comfort Asante for James Boateng)

### Decision: APPROVE

James's request can be fulfilled. His account is inactive, he has no outstanding obligations, and his data is no longer needed for the purpose it was collected for (Art. 23).

### Lifecycle Stage: DESTROY

His data is permanently deleted. Records the law requires EduConnect to keep are moved to **Archive** until their retention period ends.

### Justification

- **Classification policy:** All of James's data is CONFIDENTIAL, so it must be deleted securely and only by authorised staff.
- **Legal obligations (Law No. 058/2021):**
  - **Right to erasure (Art. 23):** James can request it where the data is no longer necessary.
  - **Deadline (Art. 23):** EduConnect must inform him of the erasure **within 30 days**. He may appeal to the NCSA if unsatisfied.
  - **Third parties (Art. 23):** any third parties his data was shared with must be told of the request.
  - **Retention (Art. 52):** data is kept only until its purpose is fulfilled, unless the law requires longer.
- **Data that can be retained:**
  - **Payment records:** required by tax and accounting law (Art. 52), kept with restricted access until the legal period ends.
  - **A minimal record of the request** (date and action taken): to prove compliance.
  - **Everything else is deleted:** profile, contact details, course activity and grades.

### Action Steps (Customer Support process)

1. **Verify James's identity** before acting.
2. **Log the request** and its date (the 30-day deadline starts here).
3. **Confirm with Finance** that there are no payments or disputes outstanding.
4. **Ask DevOps** to delete his data from all systems and archive the payment records.
5. **Notify third parties** holding his data (e.g. email or payment providers).
6. **Confirm in writing to James within 30 days** what was deleted, what was kept and why.
