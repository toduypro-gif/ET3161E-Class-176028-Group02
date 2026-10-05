# Week 4 – State Machine Diagram

**Owners:** Duy (state list, merge) · Việt (group 1) · Nam (group 2) · Hoàng (group 3) · Hưng (transition table)

A research-topic record has **8 main states** plus **1 exception state** (Rejected / Returned).

## States

| ID | State | Meaning |
|---|---|---|
| S1 | Draft | Student is preparing the BM1 form; not yet submitted. |
| S2 | Pending Approval | BM1 submitted; waiting for Supervisor → Head → Board of Directors to sign in order. |
| S3 | Rejected / Returned | An approver rejected the form; waiting for the Student to revise. |
| S4 | Received | BM1 signed at all 3 levels; the original has been received by QLDT. |
| S5 | Proposal Defense | Defense scheduled or in progress at the Training Institution. |
| S6 | Pending Ethics Review | Proposal defense passed; waiting for the Ethics Committee. |
| S7 | In Progress | Ethics approval granted; research is being carried out. |
| S8 | Thesis Defended | Thesis/dissertation defended; waiting for final submission. |
| S9 | Closed / Archived | Final documents submitted, BM2 issued; paper record kept for 5 years. |

## Transitions

| From | Event / condition | To | Actor |
|---|---|---|---|
| (start) | Student creates a BM1 form | Draft | Student |
| Draft | Student submits BM1 | Pending Approval | Student |
| Pending Approval | Any of the three approvers rejects | Rejected / Returned | Supervisor / Head / BoD |
| Rejected / Returned | Student revises and resubmits | Draft | Student |
| Pending Approval | Signed by Supervisor + Head + BoD and original submitted | Received | QLDT |
| Received | Proposal defense scheduled | Proposal Defense | Training Institution |
| Proposal Defense | Proposal defense passed | Pending Ethics Review | Training Institution |
| Pending Ethics Review | Ethics Committee grants approval | In Progress | Ethics Committee |
| In Progress | Thesis/dissertation defense completed | Thesis Defended | Training Institution |
| Thesis Defended | Soft copy + printed copy submitted, BM2 issued | Closed / Archived | Student, QLDT |
| Closed / Archived | 5-year retention expires → paper records shredded | (end) | QLDT |
