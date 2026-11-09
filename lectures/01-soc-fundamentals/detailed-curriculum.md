# Detailed Curriculum — Module 01: SOC Fundamentals & Security Operations

> **Status:** draft — pending independent review and Project Owner approval  
> **Module ID:** 01-soc-fundamentals  
> **Curriculum version:** 0.2  
> **Proposed contact time:** 6 hours

## 1. Module purpose

SOC Fundamentals & Security Operations develops the capability to perform the domain-specific work expected of a SOC analyst. Instruction is capability-led; tools are used as supporting instruments, not as learning outcomes.

## 2. Prerequisites

None; diagnostic baseline only.

## 3. Measurable learning outcomes

By the end of this module, learners should be able to:

| ID | Learning outcome | Lesson alignment | Evidence |
|---|---|---|---|
| LO-01-01 | Explain SOC purpose, operating models, core functions, and analyst responsibilities. | L01-01, L01-02, L01-03, L01-04, L01-05, L01-06 | Practical artifact |
| LO-01-02 | Differentiate events, alerts, cases, incidents, indicators, and confirmed findings. | L01-01, L01-02, L01-03, L01-04, L01-05, L01-06 | Mapped lesson activity and assessment evidence |
| LO-01-03 | Apply a repeatable alert-triage workflow using scope, confidence, impact, and urgency. | L01-01, L01-02, L01-03, L01-04, L01-05, L01-06 | Mapped lesson activity and assessment evidence |
| LO-01-04 | Prioritize and route a case with a defensible rationale and escalation trigger. | L01-01, L01-02, L01-03, L01-04, L01-05, L01-06 | Mapped lesson activity and assessment evidence |
| LO-01-05 | Document observations, hypotheses, decisions, and uncertainty in an analyst handoff. | L01-01, L01-02, L01-03, L01-04, L01-05, L01-06 | Mapped lesson activity and assessment evidence |

## 4. Detailed lesson sequence

### L01-01 — SOC mission, operating models, roles, and service boundaries

- **Duration:** 45 minutes
- **Core content:** SOC tiers and functions; internal, outsourced, hybrid models; analyst responsibilities; ethics and authorization.
- **Learning activity:** Role-to-task mapping; classify operational responsibilities.
- **Evidence:** learner worksheet, notes, or practical artifact aligned to the lesson outcomes.

### L01-02 — Security events, alerts, incidents, and the monitoring lifecycle

- **Duration:** 45 minutes
- **Core content:** Telemetry-to-alert pipeline; event versus alert versus incident; case lifecycle; signal versus conclusion.
- **Learning activity:** Classify sample records and explain what each does not prove.
- **Evidence:** learner worksheet, notes, or practical artifact aligned to the lesson outcomes.

### L01-03 — Alert triage and analytical reasoning

- **Duration:** 60 minutes
- **Core content:** Validate source and context; scope; severity versus priority; false positives; confidence; competing hypotheses.
- **Learning activity:** Triage a synthetic alert bundle and record facts, hypotheses, unknowns.
- **Evidence:** learner worksheet, notes, or practical artifact aligned to the lesson outcomes.

### L01-04 — SOC workflow, escalation, and communication

- **Duration:** 60 minutes
- **Core content:** Queue ownership; SLAs as concepts; escalation; shift handoff; stakeholder communication.
- **Learning activity:** Prioritize a queue and prepare a concise handoff.
- **Evidence:** learner worksheet, notes, or practical artifact aligned to the lesson outcomes.

### L01-05 — Analyst documentation and evidence discipline

- **Duration:** 60 minutes
- **Core content:** Case notes; timestamps; provenance; reproducibility; privacy and safe handling.
- **Learning activity:** Complete an evidence-referenced case record.
- **Evidence:** learner worksheet, notes, or practical artifact aligned to the lesson outcomes.

### L01-06 — Integrated triage exercise

- **Duration:** 90 minutes
- **Core content:** End-to-end application of workflow and communication.
- **Learning activity:** Team triage of mixed benign/suspicious signals; individual rationale.
- **Evidence:** learner worksheet, notes, or practical artifact aligned to the lesson outcomes.

## 5. Practical learning activities

Queue triage exercise; incident-versus-alert classification; analyst handoff.

Activities must be delivered only within the authorized lab or with instructor-provided sanitized/synthetic artifacts. If required telemetry is unavailable, disclose the substitution and its limitations.

## 6. Assessment plan

**Primary assessment evidence:** Triage worksheet, prioritized queue, case note, and oral handoff; suggested 100-point formative rubric.

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

The proposed 6-hour allocation is a planning estimate. It must be checked against the actual lesson materials, learner skill level, lab setup time, and classroom pilot. Breaks and independent study are excluded.

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
