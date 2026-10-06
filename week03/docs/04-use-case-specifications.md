# Week 6 – Use Case Specifications

All 11 use cases use one template, created and reviewed by Duy. Business rules are listed in [05-business-rules.md] (week02)

## Contents

- [UC01. Create / Submit BM1 Proposal Form](#uc01-create--submit-bm1-proposal-form)
- [UC02. Track Signing History](#uc02-track-signing-history)
- [UC03. Approve / Reject Proposal](#uc03-approve--reject-proposal)
- [UC04. Record Proposal Defense Result](#uc04-record-proposal-defense-result)
- [UC05. Register Ethics Review](#uc05-register-ethics-review)
- [UC06. Update Ethics Approval Status](#uc06-update-ethics-approval-status)
- [UC07. Update Research Progress](#uc07-update-research-progress)
- [UC08. Record Thesis Defense Result](#uc08-record-thesis-defense-result)
- [UC09. Submit Final Thesis](#uc09-submit-final-thesis)
- [UC10. Issue Receipt Form (BM2)](#uc10-issue-receipt-form-bm2)
- [UC11. Manage Record Archiving & Disposal](#uc11-manage-record-archiving--disposal)


## UC01. Create / Submit BM1 Proposal Form

| Field | Description |
|---|---|
| **ID / Name** | UC01 – Create / Submit BM1 Proposal Form |
| **Actor(s)** | Student |
| **Specified by** | Nam |
| **Description** | The Student creates the topic proposal form (BM1) in the system and submits it to start the signing process. |
| **Pre-condition** | The Student is logged in and has no other topic beyond the Draft or Rejected state. |
| **Post-condition** | BM1 is saved and the record moves to Pending Approval; the Supervisor is notified. |
| **Business rules** | BR02, BR03 |

**Main flow**

1. Student selects “Create topic proposal”.
2. System displays the BM1 form (administrative info, title, objectives, methods, supervisor).
3. Student enters the information and selects “Submit”.
4. System validates the required fields.
5. System saves BM1, sets the status to Pending Approval, logs the history (include UC02) and notifies the Supervisor.

**Alternate / exception flows**

- 3a. Student selects “Save draft”: the system saves it as Draft and the use case ends.
- 4a. A required field is missing: the system shows an error and returns to step 3.
- Record is Rejected: the Student reopens BM1, revises it per feedback and resubmits from step 3 (BR03).

---

## UC02. Track Signing History

| Field | Description |
|---|---|
| **ID / Name** | UC02 – Track Signing History |
| **Actor(s)** | Student, QLDT |
| **Specified by** | Nam |
| **Description** | View BM1 signing progress: who signed, when, rejection comments (if any) and which level is pending. |
| **Pre-condition** | BM1 has been submitted at least once. |
| **Post-condition** | The user knows the current signing status of the record. |
| **Business rules** | BR02 |

**Main flow**

1. User selects the topic record.
2. System shows the signing timeline in the order Supervisor → Head → BoD.
3. Each entry shows the signer, time, decision and comment.

**Alternate / exception flows**

- 2a. No signature yet: the system shows “Waiting for Supervisor”.
- QLDT can filter records by the pending level to follow up.

---

## UC03. Approve / Reject Proposal

| Field | Description |
|---|---|
| **ID / Name** | UC03 – Approve / Reject Proposal |
| **Actor(s)** | Supervisor, Head of Dept./Center, Board of Directors |
| **Specified by** | Nam |
| **Description** | The signer at each level reviews BM1 and approves or rejects it. |
| **Pre-condition** | The record is Pending Approval and waiting for the user's level. |
| **Post-condition** | Approved: moves to the next level (or fully signed if BoD). Rejected: the record becomes Rejected / Returned. |
| **Business rules** | BR01, BR02, BR03 |

**Main flow**

1. Signer opens the list of records waiting for them.
2. Selects a record and reviews BM1 and its history.
3. Selects “Approve” and confirms.
4. System records the signature and time and notifies the next level.
5. If the signer is the BoD: the system marks the form as fully signed and reminds the Student to back up BM1 and submit the original (BR01).

**Alternate / exception flows**

- 3a. Signer selects “Reject”: a reason is required; the record becomes Rejected and the Student is notified (BR03).
- 1a. The user is not the pending level: the action is not allowed.

---

## UC04. Record Proposal Defense Result

| Field | Description |
|---|---|
| **ID / Name** | UC04 – Record Proposal Defense Result |
| **Actor(s)** | Training Institution |
| **Specified by** | Hoàng |
| **Description** | Record the schedule and result of the proposal defense. |
| **Pre-condition** | The record is Received or Proposal Defense. |
| **Post-condition** | Passed: the record moves to Pending Ethics Review. |
| **Business rules** | — |

**Main flow**

1. Training Institution selects the record and enters the defense schedule; status becomes Proposal Defense.
2. After the defense, it enters the date, result and minutes.
3. System saves them, moves the record to Pending Ethics Review and notifies the Student.

**Alternate / exception flows**

- 2a. Not passed: the record stays in Proposal Defense with a note requesting a re-defense.

---

## UC05. Register Ethics Review

| Field | Description |
|---|---|
| **ID / Name** | UC05 – Register Ethics Review |
| **Actor(s)** | Student |
| **Specified by** | Hoàng |
| **Description** | The Student submits an ethics review application to the Hospital Ethics Committee. |
| **Pre-condition** | The record is Pending Ethics Review. |
| **Post-condition** | The application is sent to the Ethics Committee (include UC06). |
| **Business rules** | BR04 |

**Main flow**

1. Student selects “Register ethics review”.
2. System shows the application form and the list of required attachments.
3. Student fills in the form, uploads the documents and submits.
4. System saves the application and notifies the Ethics Committee.

**Alternate / exception flows**

- 3a. A required document is missing: the system shows an error and returns to step 3.

---

## UC06. Update Ethics Approval Status

| Field | Description |
|---|---|
| **ID / Name** | UC06 – Update Ethics Approval Status |
| **Actor(s)** | Hospital Ethics Committee |
| **Specified by** | Hoàng |
| **Description** | The Ethics Committee records the result of its review. |
| **Pre-condition** | An ethics review application exists. |
| **Post-condition** | Approved: the record moves to In Progress. |
| **Business rules** | BR04 |

**Main flow**

1. Committee opens the list of applications awaiting review.
2. Reviews the application and enters the result and approval decision number/date.
3. System moves the record to In Progress and notifies the Student and Supervisor.

**Alternate / exception flows**

- 2a. Revisions required / not approved: the record stays Pending Ethics Review and the request is sent to the Student.

---

## UC07. Update Research Progress

| Field | Description |
|---|---|
| **ID / Name** | UC07 – Update Research Progress |
| **Actor(s)** | Student, Supervisor |
| **Specified by** | Hoàng |
| **Description** | Record research progress against the approved plan. |
| **Pre-condition** | The record is In Progress. |
| **Post-condition** | The new progress entry is saved in the topic log. |
| **Business rules** | BR04 |

**Main flow**

1. Student enters the work done, completion percentage and evidence.
2. System saves it and notifies the Supervisor.
3. Supervisor reviews and confirms or comments.

**Alternate / exception flows**

- 3a. Supervisor requests changes: the Student updates from step 1.

---

## UC08. Record Thesis Defense Result

| Field | Description |
|---|---|
| **ID / Name** | UC08 – Record Thesis Defense Result |
| **Actor(s)** | Training Institution |
| **Specified by** | Hưng |
| **Description** | Record the official thesis/dissertation defense result. |
| **Pre-condition** | The record is In Progress. |
| **Post-condition** | The record moves to Thesis Defended; the Student is reminded to submit final documents. |
| **Business rules** | BR05 |

**Main flow**

1. Training Institution selects the record and enters the defense date, result and committee minutes.
2. System saves them and sets the status to Thesis Defended.
3. System notifies the Student of the final submission requirements (BR05).

**Alternate / exception flows**

- 1a. Not passed: stays In Progress with a note on the re-defense schedule.

---

## UC09. Submit Final Thesis

| Field | Description |
|---|---|
| **ID / Name** | UC09 – Submit Final Thesis |
| **Actor(s)** | Student |
| **Specified by** | Hưng |
| **Description** | The Student uploads the soft copy and confirms submission of 1 revised printed copy. |
| **Pre-condition** | The record is Thesis Defended. |
| **Post-condition** | Final submission is recorded; QLDT issues BM2 (include UC10). |
| **Business rules** | BR05 |

**Main flow**

1. Student selects “Submit final documents”.
2. Uploads the revised thesis soft copy.
3. Confirms that 1 printed copy was handed to QLDT.
4. System saves it and sends a BM2 request to QLDT.

**Alternate / exception flows**

- 2a. Wrong or missing file: error shown, back to step 2.
- 4a. QLDT finds the submission incomplete: it is returned for completion.

---

## UC10. Issue Receipt Form (BM2)

| Field | Description |
|---|---|
| **ID / Name** | UC10 – Issue Receipt Form (BM2) |
| **Actor(s)** | Training Mgmt. Office (QLDT) |
| **Specified by** | Hưng |
| **Description** | QLDT checks the final submission and issues the Document Receipt Form (BM2). |
| **Pre-condition** | The Student has submitted the final documents (UC09). |
| **Post-condition** | BM2 is issued; the record is Closed / Archived; the retention expiry date is set. |
| **Business rules** | BR05, BR06 |

**Main flow**

1. QLDT officer opens the submission awaiting receipt.
2. Checks the soft copy against the printed copy.
3. Selects “Issue BM2”; the system generates the form with a number and receipt date.
4. System closes the record, sets expiry = closing date + 5 years (BR06) and sends BM2 to the Student.

**Alternate / exception flows**

- 2a. Submission incomplete: the officer records the reason and returns it to the Student.

---

## UC11. Manage Record Archiving & Disposal

| Field | Description |
|---|---|
| **ID / Name** | UC11 – Manage Record Archiving & Disposal |
| **Actor(s)** | Training Mgmt. Office (QLDT) |
| **Specified by** | Hưng |
| **Description** | Manage the paper archive location, track retention periods and record disposal. |
| **Pre-condition** | The record is Closed / Archived. |
| **Post-condition** | Archive information is updated; expired records are logged as destroyed. |
| **Business rules** | BR06 |

**Main flow**

1. QLDT officer enters the archive location (room, shelf, box).
2. System lists records past the 5-year period and flags them “Eligible for disposal”.
3. Officer prepares the disposal list and confirms shredding.
4. System records the disposal date and officer, ending the record lifecycle.

**Alternate / exception flows**

- 2a. No expired records: an empty list is shown.
- 3a. A record must be kept longer: the officer extends it and records the reason.
