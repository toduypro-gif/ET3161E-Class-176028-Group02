# AS-IS Specification - Step 1 and Step 2

- **Owner:** Hoàng Nam | **Source:** Process QTQL.NC2.3.1 | **Version:** 1.0 (Week 2)

## Step 1: Initiation and Multi-Level Signing

| Item | Description |
|---|---|
| **Goal** | To officially secure permission to conduct the research topic at the hospital. |
| **Key Actors** | Student, Supervisor, Head of Department/Center, QLDT, and Board of Directors. |
| **Inputs** | A research idea and the standard BM1/QTQL.NC2.3.1 form (currently paper-based). |
| **Trigger** | The process kicks off when a student decides to pursue a research topic at the hospital. |
| **Outputs** | A fully signed BM1 form. The original is submitted to QLDT, while the student retains a personal copy. |
| **Related Rules**| BR-01 (Mandatory backup copy), BR-05 (Legal basis). |

### Form Content (BM1)
- **Administrative Details:** Student's name, academic year, and affiliated school/institute.
- **Topic Information:** Proposed title, core objectives, methodology, expected timeframe, and study subjects.
- **Category:** Users must select one (e.g., institutional-level, ministry/province level, S&T fund, clinical trial, new method/technique, or 'other').
- **Signatures Required:** Supervisor, Head of Department/Center, QLDT, and the Board of Directors.

### Current Manual Procedure
1. The student manually fills out the physical BM1 form.
2. The Supervisor reviews the details and signs it.
3. The Head of Department/Center signs it to formally authorize the research at their unit.
4. The QLDT joins the signing chain and physically receives the file.
5. The Board of Directors gives the final executive approval.
6. The student hands over the original, fully signed BM1 to the QLDT.
7. *Crucial step:* Before handing in the original, the student must photocopy or scan it to keep a backup for future administrative steps.

### Edge Cases & Exceptions
| Scenario | How it's handled currently |
|---|---|
| **A signer rejects the form** | The student has to revise the BM1 completely and restart the signing loop. |
| **The student loses their backup copy** | They must go back to QLDT to request a new copy (though this isn't strictly defined in the official manual). |

### Pain Points (Why we need this system)
- **Lost in Transit:** A single piece of paper has to travel between 4 different offices, making it incredibly difficult to track its current location.
- **Lack of Transparency & Reminders:** There is no centralized signing history, and students often forget to make their required backup copy because there are no automated reminders.

---

## Step 2: Proposal Defense

| Item | Description |
|---|---|
| **Goal** | To successfully defend and get the research proposal approved by the student's training institution. |
| **Key Actors** | Student, Training Institution (CSDT). |
| **Inputs** | The signed backup copy of BM1 and the draft research proposal. |
| **Trigger** | This step begins as soon as the BM1 is fully approved and submitted to QLDT. |
| **Outputs** | The official result and date of the proposal defense. |
| **Related Rules**| None specific. |

### Current Manual Procedure
1. The student registers for and completes their proposal defense at their university.
2. The university officially issues the defense results.
3. The student brings this result and the defense date back to be recorded in their hospital file.

### Edge Cases & Exceptions
| Scenario | How it's handled currently |
|---|---|
| **The student fails the defense** | The student must revise their proposal and schedule a re-defense (details on this loop are not explicitly covered in the source docs). |

### Data the System Will Need to Capture
To digitize this step, the system must record the defense date, the name of the training institution, the final result (pass/fail/revise), and link it to the specific topic ID.