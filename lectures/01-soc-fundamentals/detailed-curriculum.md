# Detailed Curriculum — Module 01: SOC Fundamentals & Security Operations

[النسخة العربية](./detailed-curriculum-ar.md)

> **Status:** draft — pending independent review and Project Owner approval  
> **Module ID:** 01-soc-fundamentals  
> **Curriculum version:** 0.3  
> **Proposed contact time:** 6 hours

## 1. Module purpose

SOC Fundamentals & Security Operations develops the capability to perform the domain-specific work expected of a SOC analyst. Instruction is capability-led; tools are used as supporting instruments, not as learning outcomes.

## 2. Prerequisites

None; diagnostic baseline only.

## 3. Measurable learning outcomes

By the end of this module, learners should be able to:

| ID | Learning outcome | Lesson alignment | Evidence |
|---|---|---|---|
| LO-01-01 | Explain SOC purpose, operating models, core functions, and analyst responsibilities. | L01-01, L01-04 | Prioritized queue and escalation/handoff message with rationale. |
| LO-01-02 | Differentiate events, alerts, cases, incidents, indicators, and confirmed findings. | L01-02, L01-03 | Triage record: scope, facts, hypotheses, unknowns, confidence, impact, urgency. |
| LO-01-03 | Apply a repeatable alert-triage workflow using scope, confidence, impact, and urgency. | L01-03, L01-06 | Team case disposition plus individually authored triage rationale and handoff. |
| LO-01-04 | Prioritize and route a case with a defensible rationale and escalation trigger. | L01-04, L01-06 | Team case disposition plus individually authored triage rationale and handoff. |
| LO-01-05 | Document observations, hypotheses, decisions, and uncertainty in an analyst handoff. | L01-05, L01-06 | Team case disposition plus individually authored triage rationale and handoff. |

## 4. Detailed lesson sequence

### L01-01 — SOC mission, operating models, roles, and service boundaries

- **Duration:** 45 minutes
- **Core content:** SOC tiers and functions; internal, outsourced, hybrid models; analyst responsibilities; ethics and authorization.
- **Learning activity:** Role-to-task mapping; classify operational responsibilities.
- **Evidence:** Completed role-to-task mapping; classify operational responsibilities artifact with source/time references, the learner's reasoning, and at least one stated limitation or uncertainty.

### L01-02 — Security events, alerts, incidents, and the monitoring lifecycle

- **Duration:** 45 minutes
- **Core content:** Telemetry-to-alert pipeline; event versus alert versus incident; case lifecycle; signal versus conclusion.
- **Learning activity:** Classify sample records and explain what each does not prove.
- **Evidence:** Completed classify sample records and explain what each does not prove artifact with source/time references, the learner's reasoning, and at least one stated limitation or uncertainty.

### L01-03 — Alert triage and analytical reasoning

- **Duration:** 60 minutes
- **Core content:** Validate source and context; scope; severity versus priority; false positives; confidence; competing hypotheses.
- **Learning activity:** Triage a synthetic alert bundle and record facts, hypotheses, unknowns.
- **Evidence:** Completed triage a synthetic alert bundle and record facts, hypotheses, unknowns artifact with source/time references, the learner's reasoning, and at least one stated limitation or uncertainty.

### L01-04 — SOC workflow, escalation, and communication

- **Duration:** 60 minutes
- **Core content:** Queue ownership; SLAs as concepts; escalation; shift handoff; stakeholder communication.
- **Learning activity:** Prioritize a queue and prepare a concise handoff.
- **Evidence:** Completed prioritize a queue and prepare a concise handoff artifact with source/time references, the learner's reasoning, and at least one stated limitation or uncertainty.

### L01-05 — Analyst documentation and evidence discipline

- **Duration:** 60 minutes
- **Core content:** Case notes; timestamps; provenance; reproducibility; privacy and safe handling.
- **Learning activity:** Complete an evidence-referenced case record.
- **Evidence:** Completed complete an evidence-referenced case record artifact with source/time references, the learner's reasoning, and at least one stated limitation or uncertainty.

### L01-06 — Integrated triage exercise

- **Duration:** 90 minutes
- **Core content:** End-to-end application of workflow and communication.
- **Learning activity:** Team triage of mixed benign/suspicious signals; individual rationale.
- **Evidence:** Completed team triage of mixed benign/suspicious signals; individual rationale artifact with source/time references, the learner's reasoning, and at least one stated limitation or uncertainty.

## 5. Practical learning activities

The following are curriculum-level activity blueprints, not final student lab instructions. Convert each activity into its module-specific lab/scenario asset before delivery.

| Activity ID | Learner task | Required input / environment | Expected output | Safety, cleanup, and recovery |
|---|---|---|---|---|
| LAB-01-A | Classify a mixed alert bundle and create a triage case. | Synthetic event/alert records; no live infrastructure. | Classification worksheet, triage record, escalation rationale. | Synthetic records only; no external accounts or live response. |
| LAB-01-B | Prioritize a queue and produce a shift handoff. | Scenario cards and case-record template. | Prioritized queue, handoff note, individual rationale. | No real personal data; instructor debrief on severity, urgency, and confidence. |

Before publication, the corresponding lab/scenario asset must add exact steps, tested versions, instructor preparation, troubleshooting, reset procedure, expected outputs, and evidence-capture instructions. If a telemetry source is unavailable, use a clearly labeled instructor-provided dataset and record the substitution.

## 6. Assessment plan

**Primary assessment evidence:** LAB-01-A, LAB-01-B — see the practical activity blueprint above and the [common SOC-LAB assessment rubric](../../curriculum/assessment-rubric.md).

| Learning outcome | Lesson mapping (I/P/A) | Observable assessment evidence |
|---|---|---|
| LO-01-01 | L01-01 (I/P), L01-04 (A) | Prioritized queue and escalation/handoff message with rationale. |
| LO-01-02 | L01-02 (I/P), L01-03 (A) | Triage record: scope, facts, hypotheses, unknowns, confidence, impact, urgency. |
| LO-01-03 | L01-03 (I/P), L01-06 (A) | Team case disposition plus individually authored triage rationale and handoff. |
| LO-01-04 | L01-04 (I/P), L01-06 (A) | Team case disposition plus individually authored triage rationale and handoff. |
| LO-01-05 | L01-05 (I/P), L01-06 (A) | Team case disposition plus individually authored triage rationale and handoff. |

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

The proposed 6-hour allocation is a planning estimate. It must be checked against the actual lesson materials, learner skill level, lab setup time, and classroom pilot. Breaks and independent study are excluded.

## 10. Quality and validation gates

- [ ] Outcomes are observable and assessable.
- [ ] Every lesson maps to outcomes and evidence.
- [ ] Activities and assessment instructions are complete and accessible.
- [ ] Technical references and versions are checked.
- [ ] Lab dependencies and telemetry are verified or clearly marked unavailable.
- [ ] Safety, cleanup, and reset instructions are present for every hands-on activity.
- [ ] Instructor and student materials are separated.
- [x] Independent Quality Reviewer review completed (PASS WITH NOTES; 2026-11-10).
- [ ] Project Owner approval recorded.

**Current validation state:** NOT VALIDATED. No classroom pilot or end-to-end practical execution is claimed.

## 11. References

Use the lesson-mapped [Module Reference Catalog](../../curriculum/references/module-reference-catalog.md) as the research starting point. During lesson production, record the exact page/edition and access date for every technical claim. The catalog does not imply that lab-specific versions or configurations have been validated.

## 12. Change history

| Version | Change | Status |
|---|---|---|
| 0.3 | Revised outcome mapping, evidence expectations, activity blueprint, and lesson evidence following independent review | Draft |
| 0.2 | Initial detailed curriculum design for this module | Draft |
