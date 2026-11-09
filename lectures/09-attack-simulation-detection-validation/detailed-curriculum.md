# Detailed Curriculum — Module 09: Attack Simulation & Detection Validation

> **Status:** draft — pending independent review and Project Owner approval  
> **Module ID:** 09-attack-simulation-detection-validation  
> **Curriculum version:** 0.2  
> **Proposed contact time:** 8 hours

## 1. Module purpose

Attack Simulation & Detection Validation develops the capability to perform the domain-specific work expected of a SOC analyst. Instruction is capability-led; tools are used as supporting instruments, not as learning outcomes.

## 2. Prerequisites

Modules 03, 05, 06, 08; lab safety and telemetry readiness gates.

## 3. Measurable learning outcomes

By the end of this module, learners should be able to:

| ID | Learning outcome | Lesson alignment | Evidence |
|---|---|---|---|
| LO-09-01 | Design a bounded, authorized test plan with explicit objectives, scope, safety controls, and rollback. | L09-01, L09-02, L09-03, L09-04, L09-05, L09-06 | Practical artifact |
| LO-09-02 | Select benign or controlled emulation cases that produce observable telemetry in the isolated lab. | L09-01, L09-02, L09-03, L09-04, L09-05, L09-06 | Mapped lesson activity and assessment evidence |
| LO-09-03 | Predict expected telemetry and detection outcomes before executing a test. | L09-01, L09-02, L09-03, L09-04, L09-05, L09-06 | Mapped lesson activity and assessment evidence |
| LO-09-04 | Execute or analyze approved tests and compare expected versus observed results. | L09-01, L09-02, L09-03, L09-04, L09-05, L09-06 | Mapped lesson activity and assessment evidence |
| LO-09-05 | Diagnose gaps among behavior execution, telemetry visibility, parsing, search logic, and alerting. | L09-01, L09-02, L09-03, L09-04, L09-05, L09-06 | Mapped lesson activity and assessment evidence |
| LO-09-06 | Produce reproducible validation records and prioritized engineering recommendations. | L09-01, L09-02, L09-03, L09-04, L09-05, L09-06 | Mapped lesson activity and assessment evidence |

## 4. Detailed lesson sequence

### L09-01 — Purpose and lifecycle of attack emulation

- **Duration:** 60 minutes
- **Core content:** Purple-team loop; ATT&CK as behavior vocabulary; simulation versus real attack; safety and scope.
- **Learning activity:** Map a learning objective to a bounded test.
- **Evidence:** learner worksheet, notes, or practical artifact aligned to the lesson outcomes.

### L09-02 — Test planning, authorization, and safety controls

- **Duration:** 75 minutes
- **Core content:** Rules of engagement; target allowlist; preconditions; blast radius; snapshots; stop conditions; rollback.
- **Learning activity:** Write and peer-review a test plan.
- **Evidence:** learner worksheet, notes, or practical artifact aligned to the lesson outcomes.

### L09-03 — Emulation frameworks and test-case selection

- **Duration:** 75 minutes
- **Core content:** Atomic Red Team concepts; Caldera concepts; prerequisites; test metadata; avoid tool-first learning.
- **Learning activity:** Select a low-risk test and identify expected side effects.
- **Evidence:** learner worksheet, notes, or practical artifact aligned to the lesson outcomes.

### L09-04 — Expected telemetry and detection hypothesis

- **Duration:** 90 minutes
- **Core content:** Behavior-to-source mapping; expected events; field validation; detection logic; ATT&CK mapping version.
- **Learning activity:** Create an expected-versus-observed matrix before test.
- **Evidence:** learner worksheet, notes, or practical artifact aligned to the lesson outcomes.

### L09-05 — Controlled execution and evidence capture

- **Duration:** 90 minutes
- **Core content:** Instructor-supervised execution; event collection; timestamps; cleanup; reset; no external targets.
- **Learning activity:** Execute approved benign test or analyze instructor-captured evidence.
- **Evidence:** learner worksheet, notes, or practical artifact aligned to the lesson outcomes.

### L09-06 — Detection validation and gap analysis

- **Duration:** 90 minutes
- **Core content:** Behavior executed; telemetry visible; fields parsed; logic matched; alert delivered; limitations.
- **Learning activity:** Complete validation report and recommend next action.
- **Evidence:** learner worksheet, notes, or practical artifact aligned to the lesson outcomes.

## 5. Practical learning activities

Instructor-approved, low-risk emulation or pre-captured evidence analysis; expected-versus-observed telemetry and detection validation.

Activities must be delivered only within the authorized lab or with instructor-provided sanitized/synthetic artifacts. If required telemetry is unavailable, disclose the substitution and its limitations.

## 6. Assessment plan

**Primary assessment evidence:** Approved test plan, expected telemetry matrix, execution/evidence record, validation result, and gap recommendations.

Assessment design rules:
- Map every scored task to one or more LO identifiers.
- Require source references, timestamps where available, reasoning, limitations, and uncertainty.
- Score analytical process and evidence quality, not merely the final verdict.
- Do not require a single severity/verdict when multiple evidence-supported conclusions are reasonable.
- Keep instructor answer keys separate from student-facing instructions.

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

Use authoritative, versioned sources appropriate to the lesson. Record the publication/version and access date during content development. Do not add references that were not consulted or that do not support the relevant claims.

## 12. Change history

| Version | Change | Status |
|---|---|---|
| 0.2 | Initial detailed curriculum design for this module | Draft |
