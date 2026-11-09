# Detailed Curriculum — Module 02: SOC Lab Architecture & Deployment

> **Status:** draft — pending independent review and Project Owner approval  
> **Module ID:** 02-soc-lab-architecture  
> **Curriculum version:** 0.3  
> **Proposed contact time:** 8 hours

## 1. Module purpose

SOC Lab Architecture & Deployment develops the capability to perform the domain-specific work expected of a SOC analyst. Instruction is capability-led; tools are used as supporting instruments, not as learning outcomes.

## 2. Prerequisites

Module 01; basic Windows/Linux and networking familiarity.

## 3. Measurable learning outcomes

By the end of this module, learners should be able to:

| ID | Learning outcome | Lesson alignment | Evidence |
|---|---|---|---|
| LO-02-01 | Explain the lab's trust boundaries, network zones, traffic paths, and security rationale. | L02-01, L02-02 | VM/network configuration record, isolation checks, resource plan, snapshot identifier. |
| LO-02-02 | Deploy and configure the documented VMware virtual network and baseline VMs. | L02-02, L02-06 | Completed validation checklist, fault diagnosis log, and recovery/snapshot evidence. |
| LO-02-03 | Apply the documented pfSense segmentation and verify permitted/denied flows. | L02-03, L02-06 | Completed validation checklist, fault diagnosis log, and recovery/snapshot evidence. |
| LO-02-04 | Configure Splunk Enterprise and approved telemetry sources using verified settings. | L02-04, L02-05 | Source onboarding record with sample event, observed metadata, timestamps, and limitations. |
| LO-02-05 | Validate ingestion, timestamps, field extraction, and source coverage without assuming undocumented fields. | L02-05, L02-06 | Completed validation checklist, fault diagnosis log, and recovery/snapshot evidence. |
| LO-02-06 | Troubleshoot common connectivity and telemetry failures and restore a known-good snapshot. | L02-06 | Completed validation checklist, fault diagnosis log, and recovery/snapshot evidence. |

## 4. Detailed lesson sequence

### L02-01 — Requirements, architecture, trust boundaries, and topology

- **Duration:** 60 minutes
- **Core content:** Functional requirements; threat boundaries; management/SOC/DMZ/endpoint/Kali zones; data-flow diagrams.
- **Learning activity:** Annotate topology and justify each boundary.
- **Evidence:** Completed annotate topology and justify each boundary artifact with source/time references, the learner's reasoning, and at least one stated limitation or uncertainty.

### L02-02 — VMware Workstation networking and VM resource planning

- **Duration:** 60 minutes
- **Core content:** Virtual switches/NAT/host-only concepts; isolation; CPU/RAM/storage; snapshots; host overlap risks.
- **Learning activity:** Build and verify isolated virtual networks.
- **Evidence:** Completed build and verify isolated virtual networks artifact with source/time references, the learner's reasoning, and at least one stated limitation or uncertainty.

### L02-03 — pfSense routing, segmentation, and firewall policy

- **Duration:** 90 minutes
- **Core content:** Interfaces; gateways; rules; least privilege; logging; rule order; safe rollback.
- **Learning activity:** Implement baseline rules and test allowed/blocked paths.
- **Evidence:** Completed implement baseline rules and test allowed/blocked paths artifact with source/time references, the learner's reasoning, and at least one stated limitation or uncertainty.

### L02-04 — Splunk Enterprise baseline deployment

- **Duration:** 75 minutes
- **Core content:** Installation concepts; access control; indexes as design concepts; time range; search fundamentals; data onboarding.
- **Learning activity:** Verify service health and run baseline searches.
- **Evidence:** Completed verify service health and run baseline searches artifact with source/time references, the learner's reasoning, and at least one stated limitation or uncertainty.

### L02-05 — Endpoint and infrastructure telemetry onboarding

- **Duration:** 90 minutes
- **Core content:** Windows/Sysmon, pfSense, Suricata and Ubuntu log paths; forwarder/collector choices; timestamp and parsing validation.
- **Learning activity:** Onboard one source at a time and record observed metadata.
- **Evidence:** Completed onboard one source at a time and record observed metadata artifact with source/time references, the learner's reasoning, and at least one stated limitation or uncertainty.

### L02-06 — End-to-end validation, troubleshooting, and recovery

- **Duration:** 105 minutes
- **Core content:** Connectivity tests; event generation; ingestion lag; time sync; snapshot strategy; reset and evidence of validation.
- **Learning activity:** Execute checklist, diagnose seeded faults, restore baseline.
- **Evidence:** Completed execute checklist, diagnose seeded faults, restore baseline artifact with source/time references, the learner's reasoning, and at least one stated limitation or uncertainty.

## 5. Practical learning activities

The following are curriculum-level activity blueprints, not final student lab instructions. Convert each activity into its module-specific lab/scenario asset before delivery.

| Activity ID | Learner task | Required input / environment | Expected output | Safety, cleanup, and recovery |
|---|---|---|---|---|
| LAB-02-A | Build or inspect isolated VM networks and verify segmentation. | VMware Workstation; documented topology; approved VM images. | Annotated topology, VM/network inventory, allowed/denied flow evidence. | Check subnet overlap; isolate lab; snapshot before firewall changes; restore baseline. |
| LAB-02-B | Onboard telemetry sources and verify ingestion. | Splunk Enterprise and available Windows/pfSense/Suricata/Ubuntu sources; dataset fallback. | Source readiness matrix with observed events, timestamps, actual fields, limitations. | Do not assume indexes/sourcetypes/ports/export methods; no credentials in submissions. |

Before publication, the corresponding lab/scenario asset must add exact steps, tested versions, instructor preparation, troubleshooting, reset procedure, expected outputs, and evidence-capture instructions. If a telemetry source is unavailable, use a clearly labeled instructor-provided dataset and record the substitution.

## 6. Assessment plan

**Primary assessment evidence:** LAB-02-A, LAB-02-B — see the practical activity blueprint above and the [common SOC-LAB assessment rubric](../../curriculum/assessment-rubric.md).

| Learning outcome | Lesson mapping (I/P/A) | Observable assessment evidence |
|---|---|---|
| LO-02-01 | L02-01 (I/P), L02-02 (A) | VM/network configuration record, isolation checks, resource plan, snapshot identifier. |
| LO-02-02 | L02-02 (I/P), L02-06 (A) | Completed validation checklist, fault diagnosis log, and recovery/snapshot evidence. |
| LO-02-03 | L02-03 (I/P), L02-06 (A) | Completed validation checklist, fault diagnosis log, and recovery/snapshot evidence. |
| LO-02-04 | L02-04 (I/P), L02-05 (A) | Source onboarding record with sample event, observed metadata, timestamps, and limitations. |
| LO-02-05 | L02-05 (I/P), L02-06 (A) | Completed validation checklist, fault diagnosis log, and recovery/snapshot evidence. |
| LO-02-06 | L02-06 (I/P/A) | Completed validation checklist, fault diagnosis log, and recovery/snapshot evidence. |

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
