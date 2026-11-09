# Detailed Curriculum Design — SOC-LAB

> **Status:** draft — proposed for independent review and Project Owner approval  
> **Curriculum version:** 0.2  
> **Scope:** all 11 modules  
> **Design basis:** capability-led, evidence-based, lab-supported SOC analyst learning

## 1. Purpose and design approach

This document defines the detailed design baseline for the 11-module SOC-LAB program. Each module has a dedicated `detailed-curriculum.md` containing measurable outcomes, lesson sequence, topics, activities, assessment evidence, duration, dependencies, and validation gates.

The design moves from SOC operating fundamentals and lab foundations, through focused evidence domains, to incident response, controlled detection validation, integrated investigation, and a capstone.

## 2. Proposed program duration

The current instructional estimate is **89 contact hours**, excluding breaks, optional remediation, independent study, and environment installation time. Module-level estimates are planning assumptions and must be piloted.

| Module | Focus | Proposed hours |
|---|---|---:|
| 01 | SOC Fundamentals & Security Operations | 6 |
| 02 | SOC Lab Architecture & Deployment | 8 |
| 03 | Endpoint Detection & Investigation | 8 |
| 04 | Phishing & Email Security Investigation | 7 |
| 05 | Network Security Monitoring & Analysis | 8 |
| 06 | Network Intrusion Detection & Prevention | 7 |
| 07 | Web Security Monitoring & Investigation | 7 |
| 08 | Incident Response | 8 |
| 09 | Attack Simulation & Detection Validation | 8 |
| 10 | Integrated Threat Investigation — Operation Shadow Access | 10 |
| 11 | SOC Capstone Project | 12 |
| | **Total** | **89** |

## 3. Program-level progression

1. Establish SOC vocabulary, workflow, ethics, triage, and reporting.
2. Build and validate the isolated lab and telemetry pipeline.
3. Investigate endpoint, email, network, IDS, and web evidence independently.
4. Consolidate investigation into incident handling and response decisions.
5. Safely emulate selected behaviors and validate telemetry/detection.
6. Integrate all evidence domains in Operation Shadow Access.
7. Demonstrate independent end-to-end performance in the capstone.

## 4. Assessment architecture

- **Diagnostic:** entry knowledge and prerequisite check; no assumed prior SOC employment.
- **Formative:** short knowledge checks, guided analysis, checkpoints, and peer explanation.
- **Module practical:** evidence-based artifacts from each domain.
- **Scenario-based:** incident response tabletop and Operation Shadow Access.
- **Summative:** individual capstone package and briefing.

All assessments must map to module outcomes. Rubric dimensions: safety/scope, evidence provenance, technical interpretation, hypothesis testing, correlation/timeline, prioritization/response, communication, and validation/limitations. Passing thresholds and weighting remain provisional pending Project Owner decision.

## 5. Lab and tool constraints

- VMware Workstation; one isolated local lab instance per learner.
- Splunk Enterprise only as the current SIEM baseline; do not assume Splunk Enterprise Security.
- pfSense with Suricata integrated; do not assume standalone Suricata.
- Windows with Sysmon; Ubuntu web server in DMZ; Kali in the designated isolated segment.
- Mailpit is optional for local email exercises.
- Network plan: Management 10.0.10.0/24; SOC 10.0.20.0/24; DMZ 10.0.30.0/24; Endpoint 10.0.40.0/24; Kali 10.0.90.0/24.
- Verify actual event sources, indexes, sourcetypes, fields, timestamps, ports, package behavior, and export methods in the deployed environment before publishing exact instructions.
- If a source is unavailable, use a clearly labeled synthetic or instructor-provided dataset and disclose that limitation.

## 6. Safety and evidence rules

All attack simulation stays within the authorized isolated lab. No public targets, uncontrolled malware, credential theft, destructive actions, or real-user phishing. Instructor approval is required for disruptive changes. Students must distinguish observed behavior, generated/simulated behavior, expected telemetry, collected telemetry, detection matches, and validated outcomes. No detection or compromise claim may be made solely because a scenario names a technique or an alert fired.

## 7. Cross-module quality gates

- Every outcome is measurable and mapped to a lesson and assessment artifact.
- Lesson order respects the prerequisite map and avoids unnecessary repetition.
- Tool use supports a capability; it is not itself the learning outcome.
- Every lab has prerequisites, scope, setup, expected observations, cleanup, and safety notes.
- Every scenario separates student-facing materials from instructor-only keys.
- References are authoritative, current, and tied to claims.
- Estimated time is piloted; content is reviewed for accessibility and cognitive load.
- Runtime validation is reported only when actually performed.

## 8. Decisions pending Project Owner

1. Confirm learner entry level and assumed networking/Windows/Linux knowledge.
2. Confirm whether the proposed 89 contact hours fit the delivery model.
3. Confirm module order and whether Module 04 (email) is delivered before Module 05 (network).
4. Confirm assessment weighting, pass threshold, retake/remediation, and group/individual balance.
5. Confirm availability and licensing of all lab software and learner hardware baseline.
6. Confirm whether Mailpit is included in the standard build or remains optional.

## 9. Review status

- Curriculum design: draft baseline.
- Independent Quality Reviewer: pending.
- Technical lab validation: not performed by this design document.
- Classroom pilot: not conducted.
- Project Owner approval: pending.

## 10. Module detail index

- [01 — SOC Fundamentals & Security Operations](../lectures/01-soc-fundamentals/detailed-curriculum.md)
- [02 — SOC Lab Architecture & Deployment](../lectures/02-soc-lab-architecture/detailed-curriculum.md)
- [03 — Endpoint Detection & Investigation](../lectures/03-endpoint-detection-investigation/detailed-curriculum.md)
- [04 — Phishing & Email Security Investigation](../lectures/04-phishing-email-investigation/detailed-curriculum.md)
- [05 — Network Security Monitoring & Analysis](../lectures/05-network-security-monitoring/detailed-curriculum.md)
- [06 — Network Intrusion Detection & Prevention](../lectures/06-network-intrusion-detection/detailed-curriculum.md)
- [07 — Web Security Monitoring & Investigation](../lectures/07-web-security-investigation/detailed-curriculum.md)
- [08 — Incident Response](../lectures/08-incident-response/detailed-curriculum.md)
- [09 — Attack Simulation & Detection Validation](../lectures/09-attack-simulation-detection-validation/detailed-curriculum.md)
- [10 — Integrated Threat Investigation — Operation Shadow Access](../lectures/10-operation-shadow-access/detailed-curriculum.md)
- [11 — SOC Capstone Project](../lectures/11-soc-capstone/detailed-curriculum.md)
