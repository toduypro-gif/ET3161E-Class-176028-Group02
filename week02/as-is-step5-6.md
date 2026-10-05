# AS-IS Specification - Step 5 and Step 6

- **Owner:** Nguyên Hoàng | **Source:** process QTQL.NC2.3.1 | **Version:** 1.0 (Week 2)

## Step 5 - Thesis defense

| Item | Description |
|---|---|
| Goal | Defend the thesis at the training institution |
| Actors | Student, Training Institution (CSDT) |
| Input | Completed thesis |
| Trigger | Research finished and thesis written |
| Output | Thesis defense result and date; thesis to be revised per council comments |
| Related rules | None specific |

### Current procedure
1. Student defends the thesis at the training institution.
2. The council gives the result and comments.
3. Student revises the thesis according to the council's comments.

### Data needed by the system
Defense date, institution, result, topic ID.

## Step 6 - Acceptance and archiving

| Item | Description |
|---|---|
| Goal | Hand over the final thesis and close the topic |
| Actors | Student, QLDT (Training Management Office) |
| Input | Soft copy and one printed copy of the revised thesis |
| Trigger | Thesis revised after defense |
| Output | BM2/QTQL.NC2.3.1 receipt; topic closed; records archived |
| Related rules | BR-02, BR-03, BR-04 |

### Current procedure
1. Student submits the soft copy and one printed copy of the revised thesis to QLDT.
2. QLDT checks and receives the documents.
3. QLDT issues the receipt form BM2 (receipt code GBN-TTHL..., receiving unit, submitter, receiver, date).
4. QLDT stores the records: proposal form, thesis, receipt.

### BM2 content
Receipt code, receiving unit (Institute of Training and Research / Learning Resource Center / QLDT), submitter, receiver, receiving date, documents received.

### Records management (from the process)
| Record | Where | Retention | Form | Disposal |
|---|---|---|---|---|
| Proposal form (BM1) | QLDT | 5 years | Paper | Shredding |
| Thesis | QLDT | 5 years | Paper | Shredding |
| Receipt (BM2) | QLDT | 5 years | Paper | Shredding |

### Exceptions
| Case | Current handling |
|---|---|
| Missing soft copy or printed copy | Receipt is not issued until complete (assumed; not explicit in source) |

### Data needed by the system
Soft copy file path, submission date, receipt code, receiver, archive date, retention years (5), disposal due date.
