# Detailed Curriculum — Module 03: Endpoint Detection & Investigation

> **Status:** draft — pending independent review and Project Owner approval  
> **Module ID:** 03-endpoint-detection-investigation  
> **Curriculum version:** 0.2  
> **Proposed contact time:** 8 hours

## 1. Module purpose

Endpoint Detection & Investigation develops the capability to perform the domain-specific work expected of a SOC analyst. Instruction is capability-led; tools are used as supporting instruments, not as learning outcomes.

## 2. Prerequisites

Modules 01–02; Windows event-log and basic process concepts.

## 3. Measurable learning outcomes

By the end of this module, learners should be able to:

| ID | Learning outcome | Lesson alignment | Evidence |
|---|---|---|---|
| LO-03-01 | Describe Windows process, logon, service, file, and network activity relevant to SOC investigations. | L03-01, L03-02, L03-03, L03-04, L03-05, L03-06 | Practical artifact |
| LO-03-02 | Interpret selected Windows Security and Sysmon event records using event context rather than ID memorization. | L03-01, L03-02, L03-03, L03-04, L03-05, L03-06 | Mapped lesson activity and assessment evidence |
| LO-03-03 | Reconstruct process ancestry and a time-bounded endpoint activity sequence. | L03-01, L03-02, L03-03, L03-04, L03-05, L03-06 | Mapped lesson activity and assessment evidence |
| LO-03-04 | Investigate suspicious script, executable, persistence-like, and logon activity while considering benign explanations. | L03-01, L03-02, L03-03, L03-04, L03-05, L03-06 | Mapped lesson activity and assessment evidence |
| LO-03-05 | Correlate endpoint observations with network and SIEM evidence and state confidence and limitations. | L03-01, L03-02, L03-03, L03-04, L03-05, L03-06 | Mapped lesson activity and assessment evidence |
| LO-03-06 | Produce a reproducible endpoint investigation report with source references. | L03-01, L03-02, L03-03, L03-04, L03-05, L03-06 | Mapped lesson activity and assessment evidence |

## 4. Detailed lesson sequence

### L03-01 — Windows endpoint telemetry and event architecture

- **Duration:** 75 minutes
- **Core content:** Windows logs; channels; event schema; Security auditing; Sysmon purpose/configuration; collection limitations.
- **Learning activity:** Map questions to relevant telemetry sources.
- **Evidence:** learner worksheet, notes, or practical artifact aligned to the lesson outcomes.

### L03-02 — Process execution, parent-child relationships, and command lines

- **Duration:** 90 minutes
- **Core content:** Process creation; image path; hashes; parent process; user/session; command-line context; normal administration.
- **Learning activity:** Analyze a synthetic process tree and identify anomalies.
- **Evidence:** learner worksheet, notes, or practical artifact aligned to the lesson outcomes.

### L03-03 — Logon, privilege, service, and scheduled execution signals

- **Duration:** 90 minutes
- **Core content:** Authentication context; logon types; account activity; services/tasks as persistence concepts; audit gaps.
- **Learning activity:** Build an account/process timeline and assess alternative causes.
- **Evidence:** learner worksheet, notes, or practical artifact aligned to the lesson outcomes.

### L03-04 — File, registry, script, and network activity

- **Duration:** 90 minutes
- **Core content:** File creation/modification; registry telemetry; PowerShell/script signals; process network connections; Sysmon coverage limits.
- **Learning activity:** Pivot between related events and distinguish evidence from inference.
- **Evidence:** learner worksheet, notes, or practical artifact aligned to the lesson outcomes.

### L03-05 — Endpoint investigation in Splunk Enterprise

- **Duration:** 75 minutes
- **Core content:** Search workflow; time bounds; field validation; pivots; event grouping; saved searches.
- **Learning activity:** Investigate a prepared dataset using discovered fields, not assumed schema.
- **Evidence:** learner worksheet, notes, or practical artifact aligned to the lesson outcomes.

### L03-06 — Endpoint case investigation and reporting

- **Duration:** 60 minutes
- **Core content:** Hypothesis testing; timeline; scope; confidence; escalation; handoff.
- **Learning activity:** Complete an endpoint case pack and peer review.
- **Evidence:** learner worksheet, notes, or practical artifact aligned to the lesson outcomes.

## 5. Practical learning activities

Investigate prepared Windows/Sysmon event dataset; process tree; timeline; evidence-backed endpoint report.

Activities must be delivered only within the authorized lab or with instructor-provided sanitized/synthetic artifacts. If required telemetry is unavailable, disclose the substitution and its limitations.

## 6. Assessment plan

**Primary assessment evidence:** Endpoint evidence matrix, process tree, timeline, Splunk search notes, and investigation report.

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
