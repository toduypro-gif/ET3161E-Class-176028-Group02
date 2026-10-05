# Actors (Users) and Their Roles

- **Version:** 1.0 (Week 2) | **Owner:** Hoàng Nam

## 1. Actor List
| Actor | Description | Type | Primary Goal |
|---|---|---|---|
| Student (HV) | A Master's, PhD, or undergraduate student conducting the research. | Primary | To successfully manage their research topic from the initial proposal (BM1) to the final submission (BM2). |
| Supervisor (GVHD) | The academic advisor guiding the student. | Primary | To review, approve, and monitor the student's research progress. |
| Head of Department/Center | The head of the unit where the research takes place. | Primary | To grant permission for the research to be conducted within their unit. |
| Training Management Office (QLDT) | Administrative staff handling training affairs. | Primary | To process paperwork, track statuses, issue BM2 receipts, and manage long-term archiving. |
| Board of Directors (BGD) | The hospital's executive leadership. | Primary | To provide the final executive approval for the research proposal. |
| Ethics Committee (HDDD) | The council responsible for ethical oversight. | Primary | To evaluate and decide on the ethical compliance of the research. |
| Training Institution (CSDT) | The university where the student is enrolled. | External | To host the proposal and thesis defenses (the results are then recorded in our system). |
| Administrator | The IT system administrator. | Support | To manage user accounts, permissions, and system settings. |

## 2. Actor - Function Matrix
*(Note: C = Create, R = Read, U = Update, A = Approve/Reject)*

| Core Function | Student | Supervisor | Head | QLDT | BGD | Ethics | Admin |
|---|---|---|---|---|---|---|---|
| Create/edit BM1 (FR-01) | C, R, U | R | R | R | R | - | - |
| Submit BM1 for signing (FR-02) | U | - | - | - | - | - | - |
| Approve/reject BM1 (FR-03) | - | A | A | A | A | - | - |
| View signing history (FR-04) | R | R | R | R | R | - | - |
| Upload signed BM1 scan (FR-05) | C | - | - | R | - | - | - |
| Confirm receipt of original BM1 (FR-06)| R | - | - | U | - | - | - |
| Record proposal defense (FR-07) | C | - | - | C | - | - | - |
| Register/decide ethics review (FR-08) | C | - | - | R | - | A | - |
| Update progress (FR-09) | - | U | - | R | - | - | - |
| Record thesis defense (FR-10) | C | - | - | C | - | - | - |
| Submit thesis / confirm receipt (FR-11)| C | - | - | U | - | - | - |
| Issue BM2 receipt (FR-12) | R | - | - | C | - | - | - |
| Archive record (FR-13) | - | - | - | C, U | - | - | - |
| Search / view dashboard (FR-14) | R | R | R | R | R | R | R |
| Manage accounts (FR-15) | - | - | - | - | - | - | C, U |

## 3. Actor Descriptions

**Student:** As the initiator of the process, the student fills out the BM1 form. They are responsible for keeping a signed backup copy (BR-01), registering for ethics reviews, tracking their overall progress, and ultimately submitting both the soft copy and printed versions of their thesis.

**Supervisor:** Acting as the first reviewer, the supervisor signs off on the BM1 form (or rejects it with feedback). Once the research is underway, they are also responsible for updating the student's progress in the system.

**Head of Department/Center:** This role acts as the second level of approval, officially confirming that the student is permitted to conduct their research at the specified unit.

**QLDT:** A crucial administrative hub, the QLDT receives the original signed BM1, participates in the signing workflow, and logs defense results. At the end of the process, they receive the final thesis, issue the BM2 receipt, and handle the 5-year physical archive.

**BGD:** The highest level of approval. Once the Board approves the proposal, the student can proceed to submit the original physical document to the QLDT.

**Ethics Committee:** This committee strictly handles the ethics registration, reviewing the application and officially recording their approval or rejection.

**Training Institution:** While this is an external entity (the system doesn't manage their internal processes), the system relies on them for holding the defense sessions. We just store the final defense dates and results.

**Administrator:** The technical backbone, responsible for creating user accounts, assigning appropriate roles, and disabling accounts when necessary.