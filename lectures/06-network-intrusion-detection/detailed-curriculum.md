# Detailed Curriculum — Module 06: Network Intrusion Detection & Prevention

> **Status:** draft — pending independent review and Project Owner approval  
> **Module ID:** 06-network-intrusion-detection  
> **Curriculum version:** 0.3  
> **Proposed contact time:** 7 hours

## 1. Module purpose

Network Intrusion Detection & Prevention develops the capability to perform the domain-specific work expected of a SOC analyst. Instruction is capability-led; tools are used as supporting instruments, not as learning outcomes.

## 2. Prerequisites

Modules 02 and 05; protocol analysis fundamentals.

## 3. Measurable learning outcomes

By the end of this module, learners should be able to:

| ID | Learning outcome | Lesson alignment | Evidence |
|---|---|---|---|
| LO-06-01 | Explain signature, protocol-anomaly, and behavior-oriented network detection approaches. | L06-01, L06-02 | Annotated Suricata alert/rule example and statement of what the alert does not prove. |
| LO-06-02 | Describe inline versus passive IDS/IPS deployment and operational trade-offs. | L06-02, L06-03 | pfSense/Suricata configuration and health evidence from deployed version or sanitized instructor output. |
| LO-06-03 | Interpret Suricata alert fields, rule metadata, flow context, and alert limitations. | L06-03, L06-06 | Annotated alert interpretation worksheet identifying field meaning, rule context, and unsupported conclusions. |
| LO-06-04 | Validate an alert against packet and environmental context and identify likely false positives. | L06-04, L06-06 | Alert triage record corroborated with packet references, environment context, and false-positive rationale. |
| LO-06-05 | Explain rule tuning, suppression, updates, and change-control considerations. | L06-05, L06-06 | Tuning change proposal with rationale, expected effect, regression checks, approval gate, and rollback. |
| LO-06-06 | Document detection test outcomes separately from telemetry visibility and analyst conclusions. | L06-06 | Validation report separating traffic generated, sensor visibility, alert generation, and prevention result. |
| LO-06-07 | Evaluate a prevention control decision, verify an authorized lab-only effect, and document impact and rollback requirements. | L06-01, L06-03, L06-05, L06-06 | Prevention decision record, allowed/denied flow test evidence, rollback and verification record. |

## 4. Detailed lesson sequence

### L06-01 — IDS/IPS concepts, architecture, and deployment modes

- **Duration:** 60 minutes
- **Core content:** Detection models; sensor placement; passive/inline; false positives/negatives; performance and risk.
- **Learning activity:** Choose sensor placement for example topologies.
- **Evidence:** Completed choose sensor placement for example topologies artifact with source/time references, the learner's reasoning, and at least one stated limitation or uncertainty.

### L06-02 — Suricata architecture, alerts, and rule anatomy

- **Duration:** 75 minutes
- **Core content:** EVE JSON concept; alert/signature/flow metadata; rule structure; classifications; reference links.
- **Learning activity:** Read sanitized alert examples and identify required context.
- **Evidence:** Completed read sanitized alert examples and identify required context artifact with source/time references, the learner's reasoning, and at least one stated limitation or uncertainty.

### L06-03 — Suricata in pfSense: operational integration

- **Duration:** 75 minutes
- **Core content:** Package role; interface selection; HOME_NET/EXTERNAL_NET concepts; updates; logging/export path verification.
- **Learning activity:** Inspect configured sensor status and document actual export behavior.
- **Evidence:** Completed inspect configured sensor status and document actual export behavior artifact with source/time references, the learner's reasoning, and at least one stated limitation or uncertainty.

### L06-04 — Alert triage and PCAP validation

- **Duration:** 90 minutes
- **Core content:** Alert context; flow direction; packet evidence; protocol context; asset criticality; benign triggers.
- **Learning activity:** Validate seeded alert records against matching packet evidence.
- **Evidence:** Completed validate seeded alert records against matching packet evidence artifact with source/time references, the learner's reasoning, and at least one stated limitation or uncertainty.

### L06-05 — Tuning, suppression, prevention policy, and change management

- **Duration:** 75 minutes
- **Core content:** Thresholds; suppressions; rule updates; regression risk; rollback; test cases.
- **Learning activity:** Propose a tuning change with before/after validation criteria.
- **Evidence:** Completed propose a tuning change with before/after validation criteria artifact with source/time references, the learner's reasoning, and at least one stated limitation or uncertainty.

### L06-06 — Detection validation report

- **Duration:** 45 minutes
- **Core content:** Coverage versus visibility versus logic versus runtime validation; limitations.
- **Learning activity:** Complete a detection validation record.
- **Evidence:** Completed complete a detection validation record artifact with source/time references, the learner's reasoning, and at least one stated limitation or uncertainty.

## 5. Practical learning activities

The following are curriculum-level activity blueprints, not final student lab instructions. Convert each activity into its module-specific lab/scenario asset before delivery.

| Activity ID | Learner task | Required input / environment | Expected output | Safety, cleanup, and recovery |
|---|---|---|---|---|
| LAB-06-A | Interpret Suricata alerts and corroborate with PCAP. | Sanitized alert/EVE output and matching PCAP, or verified pfSense telemetry. | Alert/rule worksheet, packet references, triage, false-positive notes. | Alert-only mode unless prevention capability is verified and explicitly authorized. |
| LAB-06-B | Evaluate a prevention control and verify effect safely. | Isolated lab firewall rule or instructor-controlled policy simulation; snapshots and rollback. | Prevention decision record, allowed/denied flow tests, impact and rollback evidence. | Do not enable inline IPS by default; require authorization, allowlist, out-of-band access, rollback. |

Before publication, the corresponding lab/scenario asset must add exact steps, tested versions, instructor preparation, troubleshooting, reset procedure, expected outputs, and evidence-capture instructions. If a telemetry source is unavailable, use a clearly labeled instructor-provided dataset and record the substitution.

## 6. Assessment plan

**Primary assessment evidence:** LAB-06-A, LAB-06-B — see the practical activity blueprint above and the [common SOC-LAB assessment rubric](../../curriculum/assessment-rubric.md).

| Learning outcome | Lesson mapping (I/P/A) | Observable assessment evidence |
|---|---|---|
| LO-06-01 | L06-01 (I/P), L06-02 (A) | Annotated Suricata alert/rule example and statement of what the alert does not prove. |
| LO-06-02 | L06-02 (I/P), L06-03 (A) | pfSense/Suricata configuration and health evidence from deployed version or sanitized instructor output. |
| LO-06-03 | L06-03 (I/P), L06-06 (A) | Validation report separating traffic generated, sensor visibility, alert generation, and prevention result. |
| LO-06-04 | L06-04 (I/P), L06-06 (A) | Validation report separating traffic generated, sensor visibility, alert generation, and prevention result. |
| LO-06-05 | L06-05 (I/P), L06-06 (A) | Validation report separating traffic generated, sensor visibility, alert generation, and prevention result. |
| LO-06-06 | L06-06 (I/P/A) | Validation report separating traffic generated, sensor visibility, alert generation, and prevention result. |
| LO-06-07 | L06-01 (I), L06-03 (P), L06-05 (P), L06-06 (A) | Validation report separating traffic generated, sensor visibility, alert generation, and prevention result. |

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

The proposed 7-hour allocation is a planning estimate. It must be checked against the actual lesson materials, learner skill level, lab setup time, and classroom pilot. Breaks and independent study are excluded.

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

**Prevention scope:** Distinguish passive Suricata alerting from inline IPS and pfSense firewall enforcement. The student exercise evaluates a reversible, isolated firewall-policy change or a tabletop policy simulation. Inline Suricata prevention is not assumed; it may be demonstrated only after package/version/interface support is verified and the instructor authorizes a rollback-tested change.

**Current validation state:** NOT VALIDATED. No classroom pilot or end-to-end practical execution is claimed.

## 11. References

Use the lesson-mapped [Module Reference Catalog](../../curriculum/references/module-reference-catalog.md) as the research starting point. During lesson production, record the exact page/edition and access date for every technical claim. The catalog does not imply that lab-specific versions or configurations have been validated.

## 12. Change history

| Version | Change | Status |
|---|---|---|
| 0.3 | Revised outcome mapping, evidence expectations, activity blueprint, and lesson evidence following independent review | Draft |
| 0.2 | Initial detailed curriculum design for this module | Draft |
