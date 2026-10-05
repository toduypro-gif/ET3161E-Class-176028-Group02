# Week 3 – Activity Diagram (Swimlane)

**Owners:** Duy (layout, merge, review) · Việt (Step 1) · Nam (Steps 2–3) · Hoàng (Steps 4–5) · Hưng (Step 6, narrative)

The diagram models the full lifecycle of a research-topic record across the 6 steps of process QTQL.NC2.3.1, in 7 lanes (one per actor). BM1 is signed in sequence by the Supervisor, the Head of Dept./Center and the Board of Directors, with a decision at each level. A rejection at any level returns the form to the Student, who revises it and starts again from the Supervisor.

## Step-by-step narrative

| Step | Activity / decision | Actors | Output |
|---|---|---|---|
| 1 | Student fills in the BM1 proposal form; it is signed in order by the Supervisor → Head of Dept./Center → Board of Directors. Each level has an Approved? decision. | Student, Supervisor, Head, BoD | BM1 signed at all 3 levels |
| 1a | Reject branch: the record returns to the Student for revision and restarts from the Supervisor. | Student | Revised BM1 |
| 1b | Student scans/copies the fully signed BM1, then submits the original to the Training Mgmt. Office (QLDT). | Student, QLDT | BM1 backup; record received |
| 2 | Proposal defense is held at the Training Institution. | Training Institution | Proposal defense result |
| 3 | Student registers for ethics review; the Hospital Ethics Committee reviews and grants approval. | Student, Ethics Committee | Ethics approval |
| 4 | Research is carried out according to the approved plan. | Student (Supervisor supports) | Research results |
| 5 | Thesis/dissertation defense is held at the Training Institution. | Training Institution | Official defense result |
| 6 | Student submits a soft copy + 1 revised printed copy; QLDT issues the Document Receipt Form (BM2); paper records are kept 5 years, then shredded. | Student, QLDT | BM2; archived record |

## Design decisions

- All rejections return to the **Student**, not to the previous signer, as the process document states (BR03).
- The BM1 backup (scan/copy) happens in the Student lane before the original is handed to QLDT (BR01).
- Archiving and shredding after 5 years are shown as the final QLDT activity (BR06).
