# Week 5 – Use Case Model

**Owners:** Duy (actors, standardization) · Việt (UC01–02) · Nam (UC03–04) · Hoàng (UC05–08) · Hưng (UC09–11, relationships)

## Actors

| Actor | Role in the system |
|---|---|
| Student | Creates and submits BM1, registers for ethics review, updates progress, submits final documents, tracks the record status. |
| Supervisor | Signs BM1 at level 1; follows and confirms research progress. |
| Head of Dept./Center | Signs BM1 at level 2. |
| Board of Directors (BoD) | Gives the final approval of BM1. |
| Training Mgmt. Office (QLDT) | Receives records, tracks signing, issues BM2, manages archiving and disposal. Does not make approval decisions. |
| Hospital Ethics Committee | Reviews and records the ethics approval result. |
| Training Institution | Records proposal defense and thesis defense results. |

## Use cases

| ID | Use case | Primary actor(s) | Functional group | Specified by |
|---|---|---|---|---|
| UC01 | Create / Submit BM1 Proposal Form | Student | 1. Manage BM1 Proposal Form | Việt |
| UC02 | Track Signing History | Student, QLDT | 1. Manage BM1 Proposal Form | Việt |
| UC03 | Approve / Reject Proposal | Supervisor, Head, BoD | 2. Approval & Proposal Defense | Nam |
| UC04 | Record Proposal Defense Result | Training Institution | 2. Approval & Proposal Defense | Nam |
| UC05 | Register Ethics Review | Student | 3. Ethics, Progress & Thesis Defense | Hoàng |
| UC06 | Update Ethics Approval Status | Ethics Committee | 3. Ethics, Progress & Thesis Defense | Hoàng |
| UC07 | Update Research Progress | Student, Supervisor | 3. Ethics, Progress & Thesis Defense | Hoàng |
| UC08 | Record Thesis Defense Result | Training Institution | 3. Ethics, Progress & Thesis Defense | Hoàng |
| UC09 | Submit Final Thesis | Student | 4. Final Submission & Archiving | Hưng |
| UC10 | Issue Receipt Form (BM2) | QLDT | 4. Final Submission & Archiving | Hưng |
| UC11 | Manage Record Archiving & Disposal | QLDT | 4. Final Submission & Archiving | Hưng |

## «include» relationships

| Base | Included | Reason |
|---|---|---|
| UC01 | UC02 | Submitting BM1 always records the signing history. |
| UC05 | UC06 | Registering for ethics review always leads to an ethics status update. |
| UC09 | UC10 | Submitting the final thesis always leads to issuing BM2. |

> QLDT is modeled as a separate actor that receives and tracks records; it does not make approval decisions.
