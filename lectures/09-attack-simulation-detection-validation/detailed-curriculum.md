# Detailed Curriculum — Module 09: Attack Simulation & Detection Validation

> **Status:** draft — pending independent review and Project Owner approval  
> **Module ID:** 09-attack-simulation-detection-validation  
> **Curriculum version:** 0.3  
> **Proposed contact time:** 8 hours

## 1. Module purpose

Attack Simulation & Detection Validation develops the capability to perform the domain-specific work expected of a SOC analyst. Instruction is capability-led; tools are used as supporting instruments, not as learning outcomes.

## 2. Prerequisites

Modules 03, 05, 06, 08; lab safety and telemetry readiness gates.

## 3. Measurable learning outcomes

By the end of this module, learners should be able to:

| ID | Learning outcome | Lesson alignment | Evidence |
|---|---|---|---|
| LO-09-01 | Design a bounded, authorized test plan with explicit objectives, scope, safety controls, and rollback. | L09-01, L09-02 | Test plan with target allowlist, preconditions, stop conditions, cleanup, rollback, and approval. |
| LO-09-02 | Select benign or controlled emulation cases that produce observable telemetry in the isolated lab. | L09-03, L09-05 | Execution or supplied-evidence record with operator, timestamps, target, output, cleanup, deviations. |
| LO-09-03 | Predict expected telemetry and detection outcomes before executing a test. | L09-04 | Pre-execution expected telemetry matrix with source, event hypothesis, field assumptions, ATT&CK version. |
| LO-09-04 | Execute or analyze approved tests and compare expected versus observed results. | L09-05, L09-06 | Validation matrix separating execution, telemetry, parsing, search match, alert, prevention, and gaps. |
| LO-09-05 | Diagnose gaps among behavior execution, telemetry visibility, parsing, search logic, and alerting. | L09-04, L09-06 | Validation matrix separating execution, telemetry, parsing, search match, alert, prevention, and gaps. |
| LO-09-06 | Produce reproducible validation records and prioritized engineering recommendations. | L09-02, L09-06 | Validation matrix separating execution, telemetry, parsing, search match, alert, prevention, and gaps. |

## 4. Detailed lesson sequence

### L09-01 — Purpose and lifecycle of attack emulation

- **Duration:** 60 minutes
- **Core content:** Purple-team loop; ATT&CK as behavior vocabulary; simulation versus real attack; safety and scope.
- **Learning activity:** Map a learning objective to a bounded test.
- **Evidence:** Completed map a learning objective to a bounded test artifact with source/time references, the learner's reasoning, and at least one stated limitation or uncertainty.

### L09-02 — Test planning, authorization, and safety controls

- **Duration:** 75 minutes
- **Core content:** Rules of engagement; target allowlist; preconditions; blast radius; snapshots; stop conditions; rollback.
- **Learning activity:** Write and peer-review a test plan.
- **Evidence:** Completed write and peer-review a test plan artifact with source/time references, the learner's reasoning, and at least one stated limitation or uncertainty.

### L09-03 — Emulation frameworks and test-case selection

- **Duration:** 75 minutes
- **Core content:** Atomic Red Team concepts; Caldera concepts; prerequisites; test metadata; avoid tool-first learning.
- **Learning activity:** Select a low-risk test and identify expected side effects.
- **Evidence:** Completed select a low-risk test and identify expected side effects artifact with source/time references, the learner's reasoning, and at least one stated limitation or uncertainty.

### L09-04 — Expected telemetry and detection hypothesis

- **Duration:** 90 minutes
- **Core content:** Behavior-to-source mapping; expected events; field validation; detection logic; ATT&CK mapping version.
- **Learning activity:** Create an expected-versus-observed matrix before test.
- **Evidence:** Completed create an expected-versus-observed matrix before test artifact with source/time references, the learner's reasoning, and at least one stated limitation or uncertainty.

### L09-05 — Controlled execution and evidence capture

- **Duration:** 90 minutes
- **Core content:** Instructor-supervised execution; event collection; timestamps; cleanup; reset; no external targets.
- **Learning activity:** Execute approved benign test or analyze instructor-captured evidence.
- **Evidence:** Completed execute approved benign test or analyze instructor-captured evidence artifact with source/time references, the learner's reasoning, and at least one stated limitation or uncertainty.

### L09-06 — Detection validation and gap analysis

- **Duration:** 90 minutes
- **Core content:** Behavior executed; telemetry visible; fields parsed; logic matched; alert delivered; limitations.
- **Learning activity:** Complete validation report and recommend next action.
- **Evidence:** Completed complete validation report and recommend next action artifact with source/time references, the learner's reasoning, and at least one stated limitation or uncertainty.

## 5. Practical learning activities

The following are curriculum-level activity blueprints, not final student lab instructions. Convert each activity into its module-specific lab/scenario asset before delivery.

| Activity ID | Learner task | Required input / environment | Expected output | Safety, cleanup, and recovery |
|---|---|---|---|---|
| LAB-09-A | Plan a low-risk authorized behavior test and predict telemetry. | Isolated Windows VM, approved test catalog, snapshots, allowlist, telemetry readiness record. | Approved test plan and expected-versus-observed matrix prepared before execution. | No public targets, credential theft, destructive tests, or uncontrolled malware; instructor approval. |
| LAB-09-B | Execute approved benign test or analyze captured output, then validate visibility/detection. | Pre-approved isolated test or supplied captured evidence. | Execution/evidence record and validation matrix with stage-specific gaps. | Verify cleanup and restore snapshot; if prerequisites fail, stop and use labeled captured evidence. |

Before publication, the corresponding lab/scenario asset must add exact steps, tested versions, instructor preparation, troubleshooting, reset procedure, expected outputs, and evidence-capture instructions. If a telemetry source is unavailable, use a clearly labeled instructor-provided dataset and record the substitution.

## 6. Assessment plan

**Primary assessment evidence:** LAB-09-A, LAB-09-B — see the practical activity blueprint above and the [common SOC-LAB assessment rubric](../../curriculum/assessment-rubric.md).

| Learning outcome | Lesson mapping (I/P/A) | Observable assessment evidence |
|---|---|---|
| LO-09-01 | L09-01 (I/P), L09-02 (A) | Test plan with target allowlist, preconditions, stop conditions, cleanup, rollback, and approval. |
| LO-09-02 | L09-03 (I/P), L09-05 (A) | Execution or supplied-evidence record with operator, timestamps, target, output, cleanup, deviations. |
| LO-09-03 | L09-04 (I/P/A) | Pre-execution expected telemetry matrix with source, event hypothesis, field assumptions, ATT&CK version. |
| LO-09-04 | L09-05 (I/P), L09-06 (A) | Validation matrix separating execution, telemetry, parsing, search match, alert, prevention, and gaps. |
| LO-09-05 | L09-04 (I/P), L09-06 (A) | Validation matrix separating execution, telemetry, parsing, search match, alert, prevention, and gaps. |
| LO-09-06 | L09-02 (I/P), L09-06 (A) | Validation matrix separating execution, telemetry, parsing, search match, alert, prevention, and gaps. |

**Mapping legend:** I = introduces the outcome; P = provides guided/independent practice; A = contains the observable assessment evidence. A single-lesson outcome is marked I/P/A in that lesson. These labels are the proposed instructional design and must be confirmed when the lecture and lab assets are authored.

Assessment conditions:
- The student brief must state permitted dataset/environment, time limit, allowed references, and submission format before delivery.
- Score only rubric criteria relevant to the outcomes assessed; weighting and pass threshold remain pending Project Owner decision.
- Require source/time references, reasoning, alternatives, uncertainty, and limitations where relevant.
- Identify individual versus team-produced evidence; team output alone does not establish individual mastery.
- Keep instructor answer keys and expected reasoning separate from student-facing materials.

## 7. Lab and resource dependencies

Refer to [Lab Dependency Map](../../curriculum/lab-dependency-map.md) and the shared [Lab Environment](../../lab-environment/README.md). Exact indexes, sourcetypes, fields, ports, versions, export methods, and collection paths must be verified against the deployed lab before being taught as facts.

## 8. Safety and operational boundaries

- Use only authorized, isolated lab assets and approved datasets.
- No public targets, real-user accounts, uncontrolled malware, or unauthorized data collection.
- Disruptive actions require explicit instructor authorization, impact assessment, rollback, and verification.
- Preserve evidence provenance and label synthetic, simulated, captured, and inferred data distinctly.

## 9. Estimated workload

The proposed 8-hour allocation is a planning estimate. It must be checked against the actual lesson materials, learner skill level, lab setup time, and classroom pilot. Breaks and independent study are excluded.

## 10. Quality and validation gates

- [ ] Outcomes are observable and assessable.
- [ ] Every lesson maps to outcomes and evidence.
- [ ] Activities and assessment instructions are complete and accessible.
- [ ] Technical references and versions are checked.
- [ ] Lab dependencies and telemetry are verified or clearly marked unavailable.
- [ ] Safety, cleanup, and reset instructions are present for every hands-on activity.
- [ ] Instructor and student materials are separated.
- [ ] Independent Quality Reviewer review completed.
- [ ] Project Owner approval recorded.

**Current validation state:** NOT VALIDATED. No classroom pilot or end-to-end practical execution is claimed.

## 11. References

Use the lesson-mapped [Module Reference Catalog](../../curriculum/references/module-reference-catalog.md) as the research starting point. During lesson production, record the exact page/edition and access date for every technical claim. The catalog does not imply that lab-specific versions or configurations have been validated.

## 12. Change history

| Version | Change | Status |
|---|---|---|
| 0.3 | Revised outcome mapping, evidence expectations, activity blueprint, and lesson evidence following independent review | Draft |
| 0.2 | Initial detailed curriculum design for this module | Draft |
