# Business Rules Specification
  
| Metadata | Value |
|---|---|
| **Project** | Scientific Research Management System (Process QTQL.NC2.3.1) |
| **Document Version** | 1.0 (Week 2) |
| **Author/Owner** | Hung |
 
## Table of Contents
 
- [1. Process-Mandated Business Rules](#1-process-mandated-business-rules)
- [2. Derived Workflow & Logical Rules](#2-derived-workflow--logical-rules)
- [3. Assumptions & Verification Points](#3-assumptions--verification-points)
- [4. Rule-to-Data Model Mapping](#4-rule-to-data-model-mapping)
---
 
## 1. Process-Mandated Business Rules
 
These rules are directly derived from hospital procedure **QTQL.NC2.3.1** and governing circulars.
 
| Rule ID | Business Rule Description | Regulatory Source | Applicable Stage | System Logic & Enforcement |
|---|---|---|---|---|
| **BR-01** | The student must scan/photocopy the fully signed BM1 form before submitting the physical original to QLDT, retaining a verified copy for subsequent milestones. | Procedure QTQL.NC2.3.1, Step 1 | Step 1 (Registration) | Provide an upload field for the signed BM1 scan (`signed_scan_file_path`) and display an explicit submission checklist prompt before handover. |
| **BR-02** | Official research documentation (Proposal, full thesis soft-copy, and BM2 record) must be archived for a mandatory duration of 5 years at QLDT. | Records Retention Guidelines | Step 6 (Archiving) | Automatically create an archive entry upon topic closure with `retention_years = 5` and calculate: `disposal_due_date = archive_date + 5 years`. |
| **BR-03** | The official legal repository format for completed topics is physical paper documents. | Records Management Policy | Step 6 (Archiving) | Set `storage_form = 'Paper'`. The system records the physical storage coordinate (`physical_location_code` for cabinet/shelf ID). |
| **BR-04** | Upon reaching the 5-year retention deadline, archived records must be destroyed exclusively via mechanical shredding. | Records Disposal Policy | Post-Archiving | Automatically flag records where `current_date >= disposal_due_date` with status `Due_For_Disposal` and `disposal_method = 'Shredding'`. |
| **BR-05** | Workflow and terminology must conform to Circular 37/2010/TT-BYT (MOH) and Circular 14/2014/TT-BKHCN (MOST). | Legal Framework | System-Wide | Standardize topic categorization, metadata attributes, and retention compliance fields across the application. |
 
---
 
## 2. Derived Workflow & Logical Rules
 
Rules deduced from operational workflow constraints, subject to instructor confirmation.
 
| Rule ID | Rule Description & Flow | Rationale | System Enforcement |
|---|---|---|---|
| **BR-06** | **Enforced Approval Hierarchy:**<br>Student → Supervisor → Head of Dept./Center → QLDT → Directorate (BGD) | Authority escalates strictly from direct clinical oversight to hospital executive leadership. | The action button to sign/approve is disabled for level N+1 until level N has submitted an `Approved` decision. |
| **BR-07** | **Rejection Return Mechanism:**<br>A rejection at any review level halts forward progression and routes the proposal back to the student with mandatory reviewer comments. | A denied signature requires student revisions before the workflow can be restarted or resumed. | Sets status to `Rejected` / `Revision_Required`, unlocks the form for student modifications, and requires justification notes. |
| **BR-08** | **Implementation Prerequisite:**<br>A topic may only transition to active execution (`In_Progress`) after passing proposal defense AND obtaining formal Ethics Committee approval. | Strict adherence to biomedical research safety, patient privacy, and clinical trial regulations. | State transition to `In_Progress` is blocked unless `defense_result == 'Passed'` and `ethics_status == 'Approved'`. |
| **BR-09** | **Definitive Topic Closure:**<br>A topic is formally closed and eligible for institutional clearance only after the BM2 confirmation receipt has been issued. | Verifies that all thesis deliverables and physical handovers have been fulfilled. | Updating status to `Closed` automatically triggers instantiation of the linked `ArchiveRecord`. |
| **BR-10** | **Single Academic Categorization:**<br>Each research topic must belong to exactly one of the five approved academic categories. | Required for institutional training reporting and ministerial statistical returns. | Form field rendered as a single-select dropdown/radio list (Resident, Master, Specialist I, Specialist II, Other). Multiple selections disallowed. |
 
---
 
## 3. Assumptions & Verification Points
 
Key working assumptions to be confirmed during upcoming consultation sessions:
 
| # | Working Assumption | Open Question for Clarification | Risk / Impact if Changed |
|---|---|---|---|
| **A1** | The 5-year retention period begins on the exact date BM2 is issued (`closure_date`). | Does the retention clock start immediately on closure date, or at the end of the current academic/fiscal calendar year? | Affects the automatic calculation formula for `disposal_due_date`. |
| **A2** | Uploading the scanned BM1 is an administrative verification step rather than a hard system blocker. | Should the system strictly prohibit physical submission if no digital scan is uploaded? | Influences form validation logic in Step 1. |
| **A3** | A student can lead only one active (`In_Progress`) research topic at any point in time. | Are there exceptions where a postgraduate student might lead two concurrent projects? | Determines whether the database schema enforces a unique constraint on `(student_id, active_status)`. |
 
---
 
## 4. Rule-to-Data Model Mapping
 
Traceability matrix linking business rules directly to relational database entities and attributes:
 
| Rule ID | Target Table | Target Column / Field | Data Type & Constraint |
|---|---|---|---|
| **BR-01** | `research_proposals` | `signed_scan_file_path` | `VARCHAR(255)`, nullable (required before Step 2) |
| **BR-02** | `archive_records` | `retention_years`, `archive_date` | `INT DEFAULT 5`, `DATE NOT NULL` |
| **BR-03** | `archive_records` | `storage_form`, `physical_location_code` | `VARCHAR(50) DEFAULT 'Paper'`, `VARCHAR(100)` |
| **BR-04** | `archive_records` | `disposal_method`, `disposal_due_date` | `VARCHAR(50) DEFAULT 'Shredding'`, `DATE GENERATED ALWAYS AS (archive_date + INTERVAL retention_years YEAR) STORED` |
| **BR-06 / BR-07** | `proposal_approvals` | `approval_level`, `decision`, `rejection_notes` | `INT` (1 to 4), `ENUM('Pending', 'Approved', 'Rejected')`, `TEXT` |
| **BR-08** | `research_topics`, `ethics_reviews` | `status`, `irb_decision` | `ENUM` (status list defined in the data model), `ENUM('Approved', 'Rejected')` |
| **BR-09** | `research_topics` | `status`, `bm2_receipt_number` | Updated to `'Closed'`, `VARCHAR(50) UNIQUE` |
| **BR-10** | `research_topics` | `topic_category` | `ENUM('Resident', 'Master', 'Specialist_I', 'Specialist_II', 'Other')` |
