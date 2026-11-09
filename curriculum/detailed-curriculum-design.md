# Detailed Curriculum Design — SOC-LAB

> **Status:** draft — revised following independent review; pending re-review and Project Owner approval  
> **Curriculum version:** 0.3  
> **Scope:** all 11 modules  
> **Design basis:** capability-led, evidence-based, lab-supported SOC analyst learning

## 1. Purpose and design approach
This document defines the detailed design baseline for the 11-module SOC-LAB program. Each module has measurable outcomes, a lesson sequence, practical activity blueprints, observable assessment evidence, duration, dependencies, and validation gates.

The design moves from SOC operating fundamentals and lab foundations, through focused evidence domains, to incident response, controlled detection validation, integrated investigation, and a capstone.

## 2. Proposed program duration
The instructional estimate remains **89 contact hours**, excluding breaks, optional remediation, independent study, and environment installation time. Module-level estimates are planning assumptions and must be piloted.

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
6. Integrate endpoint, email, network, IDS, web, and SIEM evidence in Operation Shadow Access.
7. Demonstrate independent end-to-end performance in the capstone.

## 4. Assessment architecture
- **Diagnostic:** entry knowledge and prerequisite check using the [Learner Readiness Checklist](learner-readiness-checklist.md).
- **Formative:** knowledge checks, guided analysis, and checkpoints.
- **Module practical:** evidence-based artifacts from each domain, mapped to explicit LO and lesson IDs.
- **Scenario-based:** incident-response tabletop and Operation Shadow Access.
- **Summative:** individual capstone package and briefing.
- **Common rubric:** use the draft [SOC-LAB Assessment Rubric](assessment-rubric.md) for performance descriptors. Weights and pass thresholds remain owner decisions.

## 5. Lab and tool constraints
- VMware Workstation; one isolated local lab instance per learner.
- Splunk Enterprise only as the current SIEM baseline; do not assume Splunk Enterprise Security.
- pfSense with Suricata integrated; do not assume standalone Suricata.
- Windows with Sysmon; Ubuntu web server in DMZ; Kali in the designated isolated segment.
- Mailpit is optional; Module 10 can use a sanitized `.eml` artifact without Mailpit.
- Network plan: Management 10.0.10.0/24; SOC 10.0.20.0/24; DMZ 10.0.30.0/24; Endpoint 10.0.40.0/24; Kali 10.0.90.0/24.
- Verify actual event sources, indexes, sourcetypes, fields, timestamps, ports, package behavior, and export methods in the deployed environment before publishing exact instructions.
- If a source is unavailable, use a clearly labeled synthetic or instructor-provided dataset and disclose the limitation.

## 6. Safety and evidence rules
All attack simulation stays within the authorized isolated lab. No public targets, uncontrolled malware, credential theft, destructive actions, or real-user phishing. Instructor approval is required for disruptive changes. Students distinguish observed behavior, generated/simulated behavior, expected telemetry, collected telemetry, detection matches, prevention outcomes, and validated results. No detection or compromise claim may be made solely because a scenario names a technique or an alert fired.

## 7. Cross-module quality gates
- Every outcome maps to a limited, defensible set of lessons and observable assessment evidence.
- Lesson order respects prerequisites and avoids unnecessary repetition.
- Practical activity blueprints identify input/environment, expected output, safety, and cleanup; final lab assets add exact tested steps.
- Every scenario separates student-facing materials from instructor-only keys.
- Module references are lesson-mapped starting points; final assets cite the exact source/edition supporting each claim.
- Estimated time is piloted; accessibility and cognitive load are reviewed.
- Runtime validation is reported only when actually performed.

## 8. Decisions pending Project Owner
1. Confirm the proposed learner entry profile and prerequisite refreshers.
2. Confirm whether 89 contact hours fit the delivery model and whether remediation is included.
3. Confirm assessment weighting, pass threshold, retake/remediation, and group/individual balance.
4. Confirm availability/licensing of lab software and learner hardware baseline.
5. Confirm whether Mailpit is included in the standard build or remains optional.
6. Confirm the final grading policy after reviewing the common rubric.

## 9. Review and validation status
- Curriculum design: draft, revision 0.3.
- Independent review of revision 0.3: pending.
- Technical lab validation: not performed by this design.
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
