# AS-IS Specification - Step 3 and Step 4

- **Owner:** Nguyên Hoàng | **Source:** process QTQL.NC2.3.1 | **Version:** 1.0 (Week 2)

## Step 3 - Ethics approval

| Item | Description |
|---|---|
| Goal | Obtain ethical approval before doing the research at the hospital |
| Actors | Student, Ethics Committee (HDDD of the hospital) |
| Input | Passed proposal; ethics registration documents |
| Trigger | Proposal defense passed |
| Output | Ethics decision (approved / rejected) and date |
| Related rules | BR-05 (legal basis) |

### Current procedure
1. Student registers the topic for ethics review with the hospital ethics committee.
2. The committee reviews the registration.
3. The committee gives its decision (approve or request changes/reject).
4. Student receives the decision.

### Exceptions
| Case | Current handling |
|---|---|
| Not approved | Student revises documents and registers again |

### Data needed by the system
Registration date, committee, decision, decision date, topic ID.
Note: the committee's internal deliberation is out of scope; the system only records registration and decision.

## Step 4 - Research implementation

| Item | Description |
|---|---|
| Goal | Carry out the research according to the approved plan |
| Actors | Student, Supervisor, Head of Department/Center |
| Input | Ethics approval; approved BM1 and proposal |
| Trigger | Ethics approval received |
| Output | Research data and progress toward the thesis; status "In Progress" |
| Related rules | None specific |

### Current procedure
1. Student implements the research following the plan.
2. Department/Center supports the student (space, patients/data access according to permission).
3. Supervisor guides the student professionally.

### Exceptions
| Case | Current handling |
|---|---|
| Delay or change of plan | Agreed between student and supervisor (not formalized in source) |

### Data needed by the system
Status = In Progress, start date, progress milestones (date, description), supervisor comments.
