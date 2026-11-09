# Detailed Curriculum — Module 02: SOC Lab Architecture & Deployment

> **Status:** draft — pending independent review and Project Owner approval  
> **Module ID:** 02-soc-lab-architecture  
> **Curriculum version:** 0.2  
> **Proposed contact time:** 8 hours

## 1. Module purpose

SOC Lab Architecture & Deployment develops the capability to perform the domain-specific work expected of a SOC analyst. Instruction is capability-led; tools are used as supporting instruments, not as learning outcomes.

## 2. Prerequisites

Module 01; basic Windows/Linux and networking familiarity.

## 3. Measurable learning outcomes

By the end of this module, learners should be able to:

| ID | Learning outcome | Lesson alignment | Evidence |
|---|---|---|---|
| LO-02-01 | Explain the lab's trust boundaries, network zones, traffic paths, and security rationale. | L02-01, L02-02, L02-03, L02-04, L02-05, L02-06 | Practical artifact |
| LO-02-02 | Deploy and configure the documented VMware virtual network and baseline VMs. | L02-01, L02-02, L02-03, L02-04, L02-05, L02-06 | Mapped lesson activity and assessment evidence |
| LO-02-03 | Apply the documented pfSense segmentation and verify permitted/denied flows. | L02-01, L02-02, L02-03, L02-04, L02-05, L02-06 | Mapped lesson activity and assessment evidence |
| LO-02-04 | Configure Splunk Enterprise and approved telemetry sources using verified settings. | L02-01, L02-02, L02-03, L02-04, L02-05, L02-06 | Mapped lesson activity and assessment evidence |
| LO-02-05 | Validate ingestion, timestamps, field extraction, and source coverage without assuming undocumented fields. | L02-01, L02-02, L02-03, L02-04, L02-05, L02-06 | Mapped lesson activity and assessment evidence |
| LO-02-06 | Troubleshoot common connectivity and telemetry failures and restore a known-good snapshot. | L02-01, L02-02, L02-03, L02-04, L02-05, L02-06 | Mapped lesson activity and assessment evidence |

## 4. Detailed lesson sequence

### L02-01 — Requirements, architecture, trust boundaries, and topology

- **Duration:** 60 minutes
- **Core content:** Functional requirements; threat boundaries; management/SOC/DMZ/endpoint/Kali zones; data-flow diagrams.
- **Learning activity:** Annotate topology and justify each boundary.
- **Evidence:** learner worksheet, notes, or practical artifact aligned to the lesson outcomes.

### L02-02 — VMware Workstation networking and VM resource planning

- **Duration:** 60 minutes
- **Core content:** Virtual switches/NAT/host-only concepts; isolation; CPU/RAM/storage; snapshots; host overlap risks.
- **Learning activity:** Build and verify isolated virtual networks.
- **Evidence:** learner worksheet, notes, or practical artifact aligned to the lesson outcomes.

### L02-03 — pfSense routing, segmentation, and firewall policy

- **Duration:** 90 minutes
- **Core content:** Interfaces; gateways; rules; least privilege; logging; rule order; safe rollback.
- **Learning activity:** Implement baseline rules and test allowed/blocked paths.
- **Evidence:** learner worksheet, notes, or practical artifact aligned to the lesson outcomes.

### L02-04 — Splunk Enterprise baseline deployment

- **Duration:** 75 minutes
- **Core content:** Installation concepts; access control; indexes as design concepts; time range; search fundamentals; data onboarding.
- **Learning activity:** Verify service health and run baseline searches.
- **Evidence:** learner worksheet, notes, or practical artifact aligned to the lesson outcomes.

### L02-05 — Endpoint and infrastructure telemetry onboarding

- **Duration:** 90 minutes
- **Core content:** Windows/Sysmon, pfSense, Suricata and Ubuntu log paths; forwarder/collector choices; timestamp and parsing validation.
- **Learning activity:** Onboard one source at a time and record observed metadata.
- **Evidence:** learner worksheet, notes, or practical artifact aligned to the lesson outcomes.

### L02-06 — End-to-end validation, troubleshooting, and recovery

- **Duration:** 105 minutes
- **Core content:** Connectivity tests; event generation; ingestion lag; time sync; snapshot strategy; reset and evidence of validation.
- **Learning activity:** Execute checklist, diagnose seeded faults, restore baseline.
- **Evidence:** learner worksheet, notes, or practical artifact aligned to the lesson outcomes.

## 5. Practical learning activities

Build segmented network; verify firewall paths; onboard one telemetry source at a time; complete validation and recovery checklist.

Activities must be delivered only within the authorized lab or with instructor-provided sanitized/synthetic artifacts. If required telemetry is unavailable, disclose the substitution and its limitations.

## 6. Assessment plan

**Primary assessment evidence:** Topology/data-flow submission, firewall test matrix, telemetry source inventory, validation checklist, and recovery demonstration.

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
