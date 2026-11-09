# Detailed Curriculum — Module 06: Network Intrusion Detection & Prevention

> **Status:** draft — pending independent review and Project Owner approval  
> **Module ID:** 06-network-intrusion-detection  
> **Curriculum version:** 0.2  
> **Proposed contact time:** 7 hours

## 1. Module purpose

Network Intrusion Detection & Prevention develops the capability to perform the domain-specific work expected of a SOC analyst. Instruction is capability-led; tools are used as supporting instruments, not as learning outcomes.

## 2. Prerequisites

Modules 02 and 05; protocol analysis fundamentals.

## 3. Measurable learning outcomes

By the end of this module, learners should be able to:

| ID | Learning outcome | Lesson alignment | Evidence |
|---|---|---|---|
| LO-06-01 | Explain signature, protocol-anomaly, and behavior-oriented network detection approaches. | L06-01, L06-02, L06-03, L06-04, L06-05, L06-06 | Practical artifact |
| LO-06-02 | Describe inline versus passive IDS/IPS deployment and operational trade-offs. | L06-01, L06-02, L06-03, L06-04, L06-05, L06-06 | Mapped lesson activity and assessment evidence |
| LO-06-03 | Interpret Suricata alert fields, rule metadata, flow context, and alert limitations. | L06-01, L06-02, L06-03, L06-04, L06-05, L06-06 | Mapped lesson activity and assessment evidence |
| LO-06-04 | Validate an alert against packet and environmental context and identify likely false positives. | L06-01, L06-02, L06-03, L06-04, L06-05, L06-06 | Mapped lesson activity and assessment evidence |
| LO-06-05 | Explain rule tuning, suppression, updates, and change-control considerations. | L06-01, L06-02, L06-03, L06-04, L06-05, L06-06 | Mapped lesson activity and assessment evidence |
| LO-06-06 | Document detection test outcomes separately from telemetry visibility and analyst conclusions. | L06-01, L06-02, L06-03, L06-04, L06-05, L06-06 | Mapped lesson activity and assessment evidence |

## 4. Detailed lesson sequence

### L06-01 — IDS/IPS concepts, architecture, and deployment modes

- **Duration:** 60 minutes
- **Core content:** Detection models; sensor placement; passive/inline; false positives/negatives; performance and risk.
- **Learning activity:** Choose sensor placement for example topologies.
- **Evidence:** learner worksheet, notes, or practical artifact aligned to the lesson outcomes.

### L06-02 — Suricata architecture, alerts, and rule anatomy

- **Duration:** 75 minutes
- **Core content:** EVE JSON concept; alert/signature/flow metadata; rule structure; classifications; reference links.
- **Learning activity:** Read sanitized alert examples and identify required context.
- **Evidence:** learner worksheet, notes, or practical artifact aligned to the lesson outcomes.

### L06-03 — Suricata in pfSense: operational integration

- **Duration:** 75 minutes
- **Core content:** Package role; interface selection; HOME_NET/EXTERNAL_NET concepts; updates; logging/export path verification.
- **Learning activity:** Inspect configured sensor status and document actual export behavior.
- **Evidence:** learner worksheet, notes, or practical artifact aligned to the lesson outcomes.

### L06-04 — Alert triage and PCAP validation

- **Duration:** 90 minutes
- **Core content:** Alert context; flow direction; packet evidence; protocol context; asset criticality; benign triggers.
- **Learning activity:** Validate seeded alert records against matching packet evidence.
- **Evidence:** learner worksheet, notes, or practical artifact aligned to the lesson outcomes.

### L06-05 — Tuning, suppression, and change management

- **Duration:** 75 minutes
- **Core content:** Thresholds; suppressions; rule updates; regression risk; rollback; test cases.
- **Learning activity:** Propose a tuning change with before/after validation criteria.
- **Evidence:** learner worksheet, notes, or practical artifact aligned to the lesson outcomes.

### L06-06 — Detection validation report

- **Duration:** 45 minutes
- **Core content:** Coverage versus visibility versus logic versus runtime validation; limitations.
- **Learning activity:** Complete a detection validation record.
- **Evidence:** learner worksheet, notes, or practical artifact aligned to the lesson outcomes.

## 5. Practical learning activities

Interpret Suricata alerts; validate against packet context; propose a safe tuning change and regression test.

Activities must be delivered only within the authorized lab or with instructor-provided sanitized/synthetic artifacts. If required telemetry is unavailable, disclose the substitution and its limitations.

## 6. Assessment plan

**Primary assessment evidence:** Alert interpretation, corroborating packet context, tuning proposal, and detection validation record.

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

**Current validation state:** NOT VALIDATED. No classroom pilot or end-to-end practical execution is claimed.

## 11. References

Use authoritative, versioned sources appropriate to the lesson. Record the publication/version and access date during content development. Do not add references that were not consulted or that do not support the relevant claims.

## 12. Change history

| Version | Change | Status |
|---|---|---|
| 0.2 | Initial detailed curriculum design for this module | Draft |
