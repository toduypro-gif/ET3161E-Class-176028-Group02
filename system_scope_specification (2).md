# System Scope Specification

- **Project:** Scientific Research Management System (Process QTQL.NC2.3.1)
- **Document Version:** 1.0 (Week 2)
- **Author/Owner:** Hung

---

## 1. System Purpose
The primary objective of the system is to digitize and streamline the management of student scientific research topics at the National Children's Hospital in compliance with procedure **QTQL.NC2.3.1**. 

By replacing manual paper-routing with an online platform, the system enables electronic submission and multi-tier approval of the initial registration form (BM1), transparent lifecycle tracking across all research phases, and automated management of closing receipts (BM2) alongside physical archive tracking.

---

## 2. In-Scope (Functional Capabilities)
The system actively implements and supports the following core capabilities:

| # | Capability | Description | Traced Requirements |
|---|---|---|---|
| **1** | **Digital BM1 Submission & Approval Workflow** | Web form submission for students and a strictly enforced sequential approval chain: $\text{Supervisor} \rightarrow \text{Head of Dept./Center} \rightarrow \text{QLDT Dept.} \rightarrow \text{Directorate (BGD)}$. | FR-01 to FR-06 |
| **2** | **Topic Lifecycle Tracking** | End-to-end status management tracking research progression through 6 standard steps (Submission, Proposal Defense, Ethics Review, Execution, Final Defense, Archiving). | FR-07, FR-09, FR-10, FR-14 |
| **3** | **Ethics Review Recording** | Capturing IRB review submissions, committee decisions, approval references, and official decision dates. | FR-08 |
| **4** | **BM2 Receipt Issuance & Thesis Upload** | Digital upload of the final approved thesis (soft copy) and automated issuance of the BM2 confirmation receipt. | FR-11, FR-12 |
| **5** | **Archive & Disposal Record Management** | Automated calculation of the 5-year retention period, tracking physical document location at QLDT, and flagging expired records for shredding. | FR-13, NFR-07 |
| **6** | **Role-Based Access Control (RBAC)** | Dedicated roles and permissions for Student, Supervisor, Department Head, QLDT Staff, Board of Directors, and System Administrator. | FR-15, NFR-01 |
| **7** | **Audit Trail & Action Logs** | Complete logging of approval decisions, feedback/rejection notes, timestamps, and stage transitions for compliance and audit purposes. | NFR-02 |

---

## 3. Out-of-Scope (Boundaries & Exclusions)
The following elements are deliberately excluded from system implementation to ensure project feasibility within the academic timeline:

| # | Excluded Item | Justification / Handling Method |
|---|---|---|
| **1** | **Scientific & Academic Assessment** | Evaluating research merit is performed by human experts (Supervisors and Academic Review Boards). The system only records administrative decisions. |
| **2** | **University Defense Administration** | Scheduling and defense council scoring at the affiliated universities are managed externally; the system only captures defense status (Passed/Failed) and date. |
| **3** | **Internal Ethics Committee Scoring** | The internal scoring rubrics and deliberations of the Institutional Review Board (IRB) occur offline; the system only records the formal approval/rejection outcome. |
| **4** | **Plagiarism Detection** | Automated text similarity scanning is outside the hospital's administrative process scope. |
| **5** | **Physical Shredding & Warehouse Logistics** | Physical execution of document destruction remains a manual facility management task; the system solely generates disposal candidate lists and flags. |
| **6** | **External System Integration** | Direct API integrations with the hospital's Hospital Information System (HIS) or external university student portals are excluded from this phase. |

---

## 4. Course Project Work Breakdown
To clearly distinguish project deliverables from the overall real-world system:

| Deliverable Domain | Coverage Level | Focus & Artifacts |
|---|---|---|
| **Business Process Analysis** | **Complete** | AS-IS / TO-BE process flows, actor identification, artifact definitions, business rules catalog. |
| **Requirements Engineering** | **Complete** | Functional (FR) and non-functional requirements (NFR) with formal acceptance criteria. |
| **System Modeling (UML)** | **Complete** | Use Case diagrams, Activity diagrams, Sequence diagrams, State Machine diagrams, Class diagrams. |
| **Database Design** | **Complete** | Entity-Relationship Diagram (ERD), Data Dictionary, and SQL DDL schemas. |
| **Application Prototype (MVP)** | **Core Workflows** | Working web interface for BM1 form submission, sequential multi-level approval, status transitions, BM2 generation, and archive record tracking. |
| **Conceptual / Non-Coded Specs** | **Specification Only** | Advanced email/SMS notification queues, external webhooks, and automated document OCR. |

---

## 5. Working Assumptions
1. **User Background:** Target users (hospital staff, clinicians, students) are already accustomed to paper-based process QTQL.NC2.3.1.
2. **Topic Concurrency:** A student acts as the primary lead for only one active research topic at any given time.
3. **Approval Sequence:** The multi-tier sign-off hierarchy is strictly fixed and cannot bypass intermediate roles.
4. **Retention Baseline:** The 5-year legal archive duration begins on the exact date the topic is closed and BM2 is issued.

---

## 6. Project Constraints
- **Regulatory Framework:** System rules must strictly align with hospital protocol QTQL.NC2.3.1, Circular 37/2010/TT-BYT (Ministry of Health), and Circular 14/2014/TT-BKHCN (Ministry of Science and Technology).
- **Execution Budget:** 14-week academic development lifecycle delivered by a 5-member team.

---

## 7. System Boundary & External Interfaces
- **Inside the Boundary:** The web application, backend business logic, relational database, uploaded document repository, and internal audit logs.
- **Outside the Boundary:** Partner medical universities, external Institutional Review Boards (IRB), physical paper archives, and paper shredding units.
- **Interface Mechanism:** Human-in-the-loop data entry. Authorized staff (QLDT) or students input verification results, reference numbers, and upload scanned supporting documents.