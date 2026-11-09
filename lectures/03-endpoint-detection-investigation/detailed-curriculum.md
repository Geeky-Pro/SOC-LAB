# Detailed Curriculum — Module 03: Endpoint Detection & Investigation

> **Status:** draft — pending independent review and Project Owner approval  
> **Module ID:** 03-endpoint-detection-investigation  
> **Curriculum version:** 0.3  
> **Proposed contact time:** 8 hours

## 1. Module purpose

Endpoint Detection & Investigation develops the capability to perform the domain-specific work expected of a SOC analyst. Instruction is capability-led; tools are used as supporting instruments, not as learning outcomes.

## 2. Prerequisites

Modules 01–02; Windows event-log and basic process concepts.

## 3. Measurable learning outcomes

By the end of this module, learners should be able to:

| ID | Learning outcome | Lesson alignment | Evidence |
|---|---|---|---|
| LO-03-01 | Describe Windows process, logon, service, file, and network activity relevant to SOC investigations. | L03-01 | Telemetry-source map: event channel, producer, observed fields, and coverage limits. |
| LO-03-02 | Interpret selected Windows Security and Sysmon event records using event context rather than ID memorization. | L03-01, L03-02, L03-03, L03-04 | Correlated file/registry/script/network worksheet separating observation from inference. |
| LO-03-03 | Reconstruct process ancestry and a time-bounded endpoint activity sequence. | L03-02, L03-03, L03-06 | Endpoint report with scope, timeline, evidence matrix, hypothesis disposition, confidence, and escalation. |
| LO-03-04 | Investigate suspicious script, executable, persistence-like, and logon activity while considering benign explanations. | L03-03, L03-04, L03-06 | Endpoint report with scope, timeline, evidence matrix, hypothesis disposition, confidence, and escalation. |
| LO-03-05 | Correlate endpoint observations with network and SIEM evidence and state confidence and limitations. | L03-04, L03-05, L03-06 | Endpoint report with scope, timeline, evidence matrix, hypothesis disposition, confidence, and escalation. |
| LO-03-06 | Produce a reproducible endpoint investigation report with source references. | L03-06 | Endpoint report with scope, timeline, evidence matrix, hypothesis disposition, confidence, and escalation. |

## 4. Detailed lesson sequence

### L03-01 — Windows endpoint telemetry and event architecture

- **Duration:** 75 minutes
- **Core content:** Windows logs; channels; event schema; Security auditing; Sysmon purpose/configuration; collection limitations.
- **Learning activity:** Map questions to relevant telemetry sources.
- **Evidence:** Completed map questions to relevant telemetry sources artifact with source/time references, the learner's reasoning, and at least one stated limitation or uncertainty.

### L03-02 — Process execution, parent-child relationships, and command lines

- **Duration:** 90 minutes
- **Core content:** Process creation; image path; hashes; parent process; user/session; command-line context; normal administration.
- **Learning activity:** Analyze a synthetic process tree and identify anomalies.
- **Evidence:** Completed analyze a synthetic process tree and identify anomalies artifact with source/time references, the learner's reasoning, and at least one stated limitation or uncertainty.

### L03-03 — Logon, privilege, service, and scheduled execution signals

- **Duration:** 90 minutes
- **Core content:** Authentication context; logon types; account activity; services/tasks as persistence concepts; audit gaps.
- **Learning activity:** Build an account/process timeline and assess alternative causes.
- **Evidence:** Completed build an account/process timeline and assess alternative causes artifact with source/time references, the learner's reasoning, and at least one stated limitation or uncertainty.

### L03-04 — File, registry, script, and network activity

- **Duration:** 90 minutes
- **Core content:** File creation/modification; registry telemetry; PowerShell/script signals; process network connections; Sysmon coverage limits.
- **Learning activity:** Pivot between related events and distinguish evidence from inference.
- **Evidence:** Completed pivot between related events and distinguish evidence from inference artifact with source/time references, the learner's reasoning, and at least one stated limitation or uncertainty.

### L03-05 — Endpoint investigation in Splunk Enterprise

- **Duration:** 75 minutes
- **Core content:** Search workflow; time bounds; field validation; pivots; event grouping; saved searches.
- **Learning activity:** Investigate a prepared dataset using discovered fields, not assumed schema.
- **Evidence:** Completed investigate a prepared dataset using discovered fields, not assumed schema artifact with source/time references, the learner's reasoning, and at least one stated limitation or uncertainty.

### L03-06 — Endpoint case investigation and reporting

- **Duration:** 60 minutes
- **Core content:** Hypothesis testing; timeline; scope; confidence; escalation; handoff.
- **Learning activity:** Complete an endpoint case pack and peer review.
- **Evidence:** Completed complete an endpoint case pack and peer review artifact with source/time references, the learner's reasoning, and at least one stated limitation or uncertainty.

## 5. Practical learning activities

The following are curriculum-level activity blueprints, not final student lab instructions. Convert each activity into its module-specific lab/scenario asset before delivery.

| Activity ID | Learner task | Required input / environment | Expected output | Safety, cleanup, and recovery |
|---|---|---|---|---|
| LAB-03-A | Investigate a prepared Windows/Sysmon activity bundle and reconstruct process ancestry. | Sanitized event export or isolated Windows VM with approved Sysmon configuration. | Process tree, logon/activity timeline, evidence references, alternative explanations. | No malware execution; use benign/synthetic records; snapshot before configuration changes. |
| LAB-03-B | Investigate a bounded endpoint case in Splunk Enterprise. | Sanitized dataset with source metadata; Splunk Enterprise. | Reproducible searches, evidence matrix, endpoint report. | Discover fields from sample events; no sensitive host/user data; no disruptive remediation. |

Before publication, the corresponding lab/scenario asset must add exact steps, tested versions, instructor preparation, troubleshooting, reset procedure, expected outputs, and evidence-capture instructions. If a telemetry source is unavailable, use a clearly labeled instructor-provided dataset and record the substitution.

## 6. Assessment plan

**Primary assessment evidence:** LAB-03-A, LAB-03-B — see the practical activity blueprint above and the [common SOC-LAB assessment rubric](../../curriculum/assessment-rubric.md).

| Learning outcome | Lesson mapping (I/P/A) | Observable assessment evidence |
|---|---|---|
| LO-03-01 | L03-01 (I/P/A) | Telemetry-source map: event channel, producer, observed fields, and coverage limits. |
| LO-03-02 | L03-01 (I), L03-02 (P), L03-03 (P), L03-04 (A) | Correlated file/registry/script/network worksheet separating observation from inference. |
| LO-03-03 | L03-02 (I), L03-03 (P), L03-06 (A) | Endpoint report with scope, timeline, evidence matrix, hypothesis disposition, confidence, and escalation. |
| LO-03-04 | L03-03 (I), L03-04 (P), L03-06 (A) | Endpoint report with scope, timeline, evidence matrix, hypothesis disposition, confidence, and escalation. |
| LO-03-05 | L03-04 (I), L03-05 (P), L03-06 (A) | Endpoint report with scope, timeline, evidence matrix, hypothesis disposition, confidence, and escalation. |
| LO-03-06 | L03-06 (I/P/A) | Endpoint report with scope, timeline, evidence matrix, hypothesis disposition, confidence, and escalation. |

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
