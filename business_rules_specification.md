# Business Rules Specification

- **Project:** Scientific Research Management System (Process QTQL.NC2.3.1)
- **Document Version:** 1.0 (Week 2)
- **Author/Owner:** Member 5

---

## 1. Process-Mandated Business Rules
These rules are directly extracted from official procedure **QTQL.NC2.3.1** and governing health/science circulars.

| Rule ID | Business Rule Description | Regulatory Source | Applicable Stage | System Logic & Enforcement |
|---|---|---|---|---|
| **BR-01** | The student must scan/photocopy the fully signed BM1 form before submitting the physical original to QLDT, retaining a verified copy for subsequent milestones. | Procedure QTQL.NC2.3.1, Step 1 | Step 1 (Registration) | Provide a mandatory/conditional upload field for the scanned BM1 (`signed_scan_url`). Display an explicit submission checklist prompt. |
| **BR-02** | Official research documentation (Proposal, Full Thesis soft-copy, and BM2 record) must be archived for a mandatory duration of **5 years** at QLDT. | Records Retention Guidelines | Step 6 (Archiving) | Automatically generate an archive entry upon topic closure with `retention_years = 5` and calculate $\text{disposal\_due\_date} = \text{archive\_date} + 5\text{ years}$. |
| **BR-03** | The official legal repository format for completed topics is physical paper documents. | Records Management Policy | Step 6 (Archiving) | Set `storage_form = 'Paper'`. The system serves as a digital index referencing the physical cabinet/shelf identifier (`physical_location_code`). |
| **BR-04** | Upon reaching the retention deadline (5 years), archived documentation must be destroyed exclusively via mechanical shredding. | Records Disposal Policy | Post-Archiving | Automatically flag records where $\text{current\_date} \ge \text{disposal\_due\_date}$ with status `Due_For_Disposal` and `disposal_method = 'Shredding'`. |
| **BR-05** | Workflow and terminology must conform to Circular 37/2010/TT-BYT (MOH) and Circular 14/2014/TT-BKHCN (MOST). | Legal Framework | System-Wide | Standardize topic categorization, metadata definitions, and archiving terminology according to ministerial standards. |

---

## 2. Derived Workflow & Logical Rules
Rules deduced from workflow constraints, subject to final instructor confirmation.

| Rule ID | Logical Rule & Description | Rationale | System Enforcement |
|---|---|---|---|
| **BR-06** | **Enforced Approval Hierarchy:**<br>BM1 approval must follow an immutable sequence:<br>$\text{Student} \rightarrow \text{Supervisor} \rightarrow \text{Head of Dept./Center} \rightarrow \text{QLDT} \rightarrow \text{Directorate (BGD)}$. | Authority strictly escalates from immediate clinical supervisor to institutional leadership. | The action button to approve/sign is disabled for level $N+1$ until level $N$ has submitted an `Approved` decision. |
| **BR-07** | **Rejection Return Mechanism:**<br>A rejection (`Rejected`) at any stage terminates the forward workflow and returns the proposal to the student with mandatory reviewer comments. | A rejected sign-off requires corrective revisions by the student before re-submission. | Transitions topic status to `Revision_Required` / `Rejected`. Unlocks the form for student updates; requires recorded justification text. |
| **BR-08** | **Implementation Prerequisite:**<br>A topic may only transition to active execution (`In_Progress`) after successfully passing proposal defense AND obtaining formal Ethics Committee approval. | Strict adherence to biomedical research safety and patient rights regulations. | Prevent setting status to `In_Progress` unless `defense_result == 'Passed'` AND `ethics_status == 'Approved'`. |
| **BR-09** | **Definitive Topic Closure:**<br>A topic is considered formally closed and eligible for graduation clearance only after the BM2 confirmation receipt has been generated. | Proves that the student has fulfilled all thesis handover requirements to the hospital. | Transition status to `Closed` triggers simultaneous creation of the corresponding `ArchiveRecord`. |
| **BR-10** | **Single Academic Categorization:**<br>Each research topic must be mapped to exactly one of the five approved academic categories (Resident, Master, Specialist I, Specialist II, Other). | Required for accurate hospital training statistics and regulatory reporting. | Render as a single-select dropdown or radio group on the registration form; multiple selections are disallowed. |

---

## 3. Assumptions & Verification Points
Key assumptions to be confirmed during upcoming consultation sessions with the instructor/stakeholders:

| # | Working Assumption | Open Question for Clarification | Risk / Impact if Changed |
|---|---|---|---|
| **A1** | The 5-year retention period begins strictly on the date BM2 is issued (`closure_date`). | Does the retention clock start immediately on closure date, or at the end of the current academic/fiscal calendar year? | Affects auto-calculation formula for `disposal_due_date`. |
| **A2** | Uploading the scanned BM1 is an administrative verification step rather than a hard system blocker. | Should the system strictly prohibit final physical submission if no digital scan is uploaded? | Influences form validation logic in Step 1. |
| **A3** | A student can only lead one single `In_Progress` research topic at any point in time. | Are there exceptions where a postgraduate student might lead two concurrent projects? | Determines whether database schema enforces a unique constraint on `(student_id, active_status)`. |

---

## 4. Rule-to-Data Model Mapping
Direct traceability mapping between business rules and the relational schema fields:

| Rule ID | Target Table | Target Column / Field | Data Type & Constraint |
|---|---|---|---|
| **BR-01** | `research_proposals` | `signed_scan_file_path` | `VARCHAR(255)`, Nullable (Required prior to Step 2) |
| **BR-02** | `archive_records` | `retention_years`<br>`archive_date` | `INT DEFAULT 5`<br>`DATE NOT NULL` |
| **BR-03** | `archive_records` | `storage_form`<br>`physical_location_code` | `VARCHAR(50) DEFAULT 'Paper'`<br>`VARCHAR(100)` (Cabinet/Shelf ID) |
| **BR-04** | `archive_records` | `disposal_method`<br>`disposal_due_date` | `VARCHAR(50) DEFAULT 'Shredding'`<br>`DATE GENERATED ALWAYS` |
| **BR-06** / **07** | `proposal_approvals` | `approval_level`<br>`decision`<br>`rejection_notes` | `INT (1 to 4)`<br>`ENUM('Pending', 'Approved', 'Rejected')`<br>`TEXT` |
| **BR-08** | `research_topics`<br>`ethics_reviews` | `status`<br>`irb_decision` | `ENUM('Draft', 'Reviewing', 'In_Progress', ...)`<br>`ENUM('Approved', 'Rejected')` |
| **BR-09** | `research_topics` | `status`<br>`bm2_receipt_number` | Update to `'Closed'`<br>`VARCHAR(50) UNIQUE` |
| **BR-10** | `research_topics` | `topic_category` | `ENUM('Resident', 'Master', 'Specialist_I', 'Specialist_II', 'Other')` |