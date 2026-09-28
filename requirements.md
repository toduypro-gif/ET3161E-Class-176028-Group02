# Requirement Specification - Research Topic Management System

- Project: Scientific Research Topic Management System (based on process QTQL.NC2.3.1)
- Version: 1.0 (Week 2)
- Owner: Tố Duy | Reviewed by: whole team
# 1. Purpose
This document lists the functional (FR) and non-functional (NFR) requirements of the system. Each requirement has a unique ID, an owner actor, a priority and the process step it belongs to, so that it can be traced to Use Cases (Week 5-6), the database (Week 7) and test cases (Week 12).

# 2. Priority definition
| Priority | Meaning |
| High | Core to the 6-step process; system is unusable without it |
| Medium | Important but the process can run manually without it for a short time |
| Low | Nice to have |

# 3. Functional requirements (FR)

| ID | Requirement | Actor | Priority | Step | Acceptance criteria 

| FR-01 | Create, edit and save a draft BM1  | Student | High | 1 | Draft can be saved with incomplete data; all mandatory fields required before submit 
| FR-02 | Submit BM1 for signing; system routes it Supervisor -> Head of Dept./Center -> QLDT -> Board of Directors| Student, System | High | 1 | Next approver only sees BM1 after previous approver approved 
| FR-03 | Approve or reject BM1 with a comment at each approval level; rejection returns BM1 to the student | Supervisor, Head, BGD | High | 1 | Reject requires a comment; status becomes Rejected and student can revise and resubmit 
| FR-04 | View signing history (who signed, when, decision, comment) | Student, QLDT | Medium | 1 | History list shows every decision in time order 
| FR-05 | Upload/store a scanned copy of the fully signed BM1 and remind the student to keep a copy | Student | Medium | 1 | Scan file (PDF/image) stored and linked to the topic; reminder shown at submission 
| FR-06 | QLDT confirms receipt of the original signed BM1 | QLDT | High | 1 | Status changes to Received with date and receiver 
| FR-07 | Record proposal defense date and result | QLDT / Student | Medium | 2 | Defense record (date, institution, result) saved and shown on topic page 
| FR-08 | Register ethics review and record the committee's decision | Student, Ethics Committee | High | 3 | Registration creates a pending review; decision (approved/rejected) and date saved 
| FR-09 | Change status to In Progress after ethics approval; update research progress milestones | System, Supervisor | High | 4 | Status changes automatically on ethics approval; milestones can be added with dates | 
| FR-10 | Record thesis defense date and result | QLDT / Student | Medium | 5 | Defense record saved; status becomes Thesis Defended 
| FR-11 | Upload thesis soft copy; QLDT confirms receipt of the revised printed thesis | Student, QLDT | High | 6 | File stored; QLDT confirmation recorded with date 
| FR-12 | Generate BM2 receipt (receipt code, receiving unit, submitter, receiver, date) | QLDT, System | High | 6 | Unique receipt code generated; BM2 can be viewed/printed 
| FR-13 | Create archive record on closing: retention 5 years, paper form, shredding disposal; flag records due for disposal | System, QLDT | Medium | 6 | Disposal-due date = archive date + 5 years; records past due are flagged 
| FR-14 | Search and filter topics by status, student, unit, date; dashboard of topic statuses | All roles | Medium | All | Results filtered correctly; users only see topics permitted by their role 
| FR-15 | Manage user accounts and assign roles | Administrator | Medium | All | Admin can create/disable users and set role 

# 4. Non-functional requirements (NFR)

| ID | Category | Requirement | Measurable target |
| NFR-01 | Security / access control | Role-based access; passwords stored hashed | Each role can only perform its allowed actions |
| NFR-02 | Audit trail | Every signing, rejection and status change is logged with user, timestamp, comment | Log entries cannot be edited or deleted by normal users |
| NFR-03 | Data integrity | Only valid state transitions allowed; approvals follow the fixed order | Invalid transition is rejected with an error message |
| NFR-04 | Usability | BM1/BM2 forms match the paper templates | A user familiar with the paper process can complete BM1 without training |
| NFR-05 | Performance | Common screens respond quickly | <= 3 seconds for up to 500 topic records |
| NFR-06 | Availability / backup | Regular backup | Daily database backup; uploaded files kept in persistent storage |
| NFR-07 | Retention compliance | Retention rule from the hospital process | 5-year retention; disposal-due date computed automatically |
| NFR-08 | Compatibility | Web-based | Works on current Chrome, Edge, Firefox |

# 5. Traceability (requirement -> process step)
| Step | Requirements |
| 1. Initiation & multi-level signing | FR-01, FR-02, FR-03, FR-04, FR-05, FR-06 |
| 2. Proposal defense | FR-07 |
| 3. Ethics approval | FR-08 |
| 4. Research implementation | FR-09 |
| 5. Thesis defense | FR-10 |
| 6. Acceptance & archiving | FR-11, FR-12, FR-13 |
| Cross-cutting | FR-14, FR-15, NFR-01 to NFR-08 |

# 7. Change log
| Version | Date | Author | Change |
| 1.0 | 28/09/2026 | Tố Duy | First complete version |
