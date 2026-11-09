# Detailed Curriculum — Module 08: Incident Response

> **Status:** draft — pending independent review and Project Owner approval  
> **Module ID:** 08-incident-response  
> **Curriculum version:** 0.2  
> **Proposed contact time:** 8 hours

## 1. Module purpose

Incident Response develops the capability to perform the domain-specific work expected of a SOC analyst. Instruction is capability-led; tools are used as supporting instruments, not as learning outcomes.

## 2. Prerequisites

Modules 01–07; confirm readiness for investigation and evidence handling.

## 3. Measurable learning outcomes

By the end of this module, learners should be able to:

| ID | Learning outcome | Lesson alignment | Evidence |
|---|---|---|---|
| LO-08-01 | Distinguish event, alert, investigation, suspected incident, and confirmed incident. | L08-01, L08-02, L08-03, L08-04, L08-05, L08-06 | Practical artifact |
| LO-08-02 | Validate an incident hypothesis and define scope, facts, unknowns, and confidence. | L08-01, L08-02, L08-03, L08-04, L08-05, L08-06 | Mapped lesson activity and assessment evidence |
| LO-08-03 | Classify and prioritize an incident using impact, scope, urgency, exposure, and confidence. | L08-01, L08-02, L08-03, L08-04, L08-05, L08-06 | Mapped lesson activity and assessment evidence |
| LO-08-04 | Construct a source-referenced timeline and maintain evidence provenance. | L08-01, L08-02, L08-03, L08-04, L08-05, L08-06 | Mapped lesson activity and assessment evidence |
| LO-08-05 | Compare proportionate containment, eradication, and recovery options with authority, impact, rollback, and verification. | L08-01, L08-02, L08-03, L08-04, L08-05, L08-06 | Mapped lesson activity and assessment evidence |
| LO-08-06 | Communicate status, escalate, maintain an incident record, and identify measurable improvements. | L08-01, L08-02, L08-03, L08-04, L08-05, L08-06 | Mapped lesson activity and assessment evidence |

## 4. Detailed lesson sequence

### L08-01 — Incident response foundations, terminology, and authority

- **Duration:** 60 minutes
- **Core content:** NIST SP 800-61r3; CSF 2.0; roles; incident governance; authority and coordination.
- **Learning activity:** Classify example cases and map decision authority.
- **Evidence:** learner worksheet, notes, or practical artifact aligned to the lesson outcomes.

### L08-02 — Incident intake, triage, and severity

- **Duration:** 75 minutes
- **Core content:** Validation; scope; severity versus priority; impact; confidence; escalation thresholds.
- **Learning activity:** Create triage and severity record.
- **Evidence:** learner worksheet, notes, or practical artifact aligned to the lesson outcomes.

### L08-03 — Investigation scope, evidence, and timeline

- **Duration:** 75 minutes
- **Core content:** Evidence provenance; timestamps; chain-of-custody concepts; timeline; unknowns.
- **Learning activity:** Build a sourced timeline and evidence matrix.
- **Evidence:** learner worksheet, notes, or practical artifact aligned to the lesson outcomes.

### L08-04 — Containment, eradication, recovery, and verification

- **Duration:** 90 minutes
- **Core content:** Containment options; business trade-offs; eradication criteria; trusted recovery; monitoring; rollback.
- **Learning activity:** Compare response options in a decision log.
- **Evidence:** learner worksheet, notes, or practical artifact aligned to the lesson outcomes.

### L08-05 — Escalation, communications, closure, and improvement

- **Duration:** 60 minutes
- **Core content:** Situation reports; stakeholder updates; closure criteria; lessons learned; corrective actions.
- **Learning activity:** Write incident update and after-action items.
- **Evidence:** learner worksheet, notes, or practical artifact aligned to the lesson outcomes.

### L08-06 — Suspicious Web Server Activity tabletop

- **Duration:** 120 minutes
- **Core content:** Staged injects; evidence-led decisions; no assumed compromise; instructor-controlled actions.
- **Learning activity:** Team tabletop, incident record, response plan, debrief.
- **Evidence:** learner worksheet, notes, or practical artifact aligned to the lesson outcomes.

## 5. Practical learning activities

Suspicious Web Server Activity tabletop using synthetic or verified sanitized evidence; response decisions remain instructor-controlled.

Activities must be delivered only within the authorized lab or with instructor-provided sanitized/synthetic artifacts. If required telemetry is unavailable, disclose the substitution and its limitations.

## 6. Assessment plan

**Primary assessment evidence:** Triage note, severity rationale, evidence matrix, decision log, situation report, incident record, and after-action items.

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
