# Detailed Curriculum — Module 10: Integrated Threat Investigation — Operation Shadow Access

> **Status:** draft — pending independent review and Project Owner approval  
> **Module ID:** 10-operation-shadow-access  
> **Curriculum version:** 0.2  
> **Proposed contact time:** 10 hours

## 1. Module purpose

Integrated Threat Investigation — Operation Shadow Access develops the capability to perform the domain-specific work expected of a SOC analyst. Instruction is capability-led; tools are used as supporting instruments, not as learning outcomes.

## 2. Prerequisites

Modules 03–09; all relevant telemetry sources validated or synthetic datasets clearly labeled.

## 3. Measurable learning outcomes

By the end of this module, learners should be able to:

| ID | Learning outcome | Lesson alignment | Evidence |
|---|---|---|---|
| LO-10-01 | Define investigation scope and competing hypotheses from an ambiguous initial alert. | L10-01, L10-02, L10-03, L10-04, L10-05, L10-06, L10-07 | Practical artifact |
| LO-10-02 | Collect and correlate endpoint, network, IDS, web, and SIEM evidence using source-aware methods. | L10-01, L10-02, L10-03, L10-04, L10-05, L10-06, L10-07 | Mapped lesson activity and assessment evidence |
| LO-10-03 | Construct a normalized timeline and distinguish observed facts from inferred stages. | L10-01, L10-02, L10-03, L10-04, L10-05, L10-06, L10-07 | Mapped lesson activity and assessment evidence |
| LO-10-04 | Assess attack progression, affected assets, potential impact, and confidence without unsupported attribution. | L10-01, L10-02, L10-03, L10-04, L10-05, L10-06, L10-07 | Mapped lesson activity and assessment evidence |
| LO-10-05 | Evaluate detection coverage and identify visibility or validation gaps. | L10-01, L10-02, L10-03, L10-04, L10-05, L10-06, L10-07 | Mapped lesson activity and assessment evidence |
| LO-10-06 | Recommend proportionate response actions and communicate a defensible incident assessment. | L10-01, L10-02, L10-03, L10-04, L10-05, L10-06, L10-07 | Mapped lesson activity and assessment evidence |

## 4. Detailed lesson sequence

### L10-01 — Scenario orientation, scope, and initial hypothesis

- **Duration:** 60 minutes
- **Core content:** Scenario brief; assets; evidence availability; scope boundaries; hypothesis register.
- **Learning activity:** Create investigation plan and initial hypotheses.
- **Evidence:** learner worksheet, notes, or practical artifact aligned to the lesson outcomes.

### L10-02 — Endpoint evidence investigation

- **Duration:** 90 minutes
- **Core content:** Process ancestry; logon; script/process activity; host timeline.
- **Learning activity:** Produce endpoint findings with source references.
- **Evidence:** learner worksheet, notes, or practical artifact aligned to the lesson outcomes.

### L10-03 — Network and IDS evidence investigation

- **Duration:** 90 minutes
- **Core content:** PCAP/flow; firewall events; Suricata alerts; corroboration and alert limits.
- **Learning activity:** Correlate network activity and assess alert significance.
- **Evidence:** learner worksheet, notes, or practical artifact aligned to the lesson outcomes.

### L10-04 — Web evidence and request reconstruction

- **Duration:** 75 minutes
- **Core content:** Access logs; request sequences; response codes; impact indicators.
- **Learning activity:** Reconstruct web activity and alternative explanations.
- **Evidence:** learner worksheet, notes, or practical artifact aligned to the lesson outcomes.

### L10-05 — Cross-source timeline and hypothesis testing

- **Duration:** 105 minutes
- **Core content:** Time normalization; entity pivots; contradictions; confidence; ATT&CK mapping only when supported.
- **Learning activity:** Build unified timeline and hypothesis disposition.
- **Evidence:** learner worksheet, notes, or practical artifact aligned to the lesson outcomes.

### L10-06 — Response decision and stakeholder briefing

- **Duration:** 90 minutes
- **Core content:** Severity; containment trade-offs; residual risk; situation report; executive briefing.
- **Learning activity:** Present evidence-led incident assessment.
- **Evidence:** learner worksheet, notes, or practical artifact aligned to the lesson outcomes.

### L10-07 — Detection coverage and lessons learned

- **Duration:** 90 minutes
- **Core content:** Scenario versus telemetry versus detection versus validation; improvements.
- **Learning activity:** Submit gap analysis and after-action review.
- **Evidence:** learner worksheet, notes, or practical artifact aligned to the lesson outcomes.

## 5. Practical learning activities

Operation Shadow Access multi-source case using endpoint, network, IDS, web, and Splunk evidence; synthetic sources explicitly labeled.

Activities must be delivered only within the authorized lab or with instructor-provided sanitized/synthetic artifacts. If required telemetry is unavailable, disclose the substitution and its limitations.

## 6. Assessment plan

**Primary assessment evidence:** Investigation plan, evidence matrix, unified timeline, hypothesis register, response recommendation, and briefing.

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

The proposed 10-hour allocation is a planning estimate. It must be checked against the actual lesson materials, learner skill level, lab setup time, and classroom pilot. Breaks and independent study are excluded.

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
