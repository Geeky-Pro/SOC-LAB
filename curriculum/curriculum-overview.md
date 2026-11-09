# SOC-LAB Curriculum Overview

> **Status:** draft — revised after independent review; pending re-review and Project Owner approval  
> **Version:** 0.3

## Purpose
Develop practical SOC capabilities: understanding security operations, working with telemetry, investigating suspicious activity, validating detections, responding to incidents, and communicating evidence-based conclusions.

## Audience and proposed entry profile
Learners developing foundational SOC analyst skills through instructor-led teaching and isolated hands-on exercises. Prior SOC employment, security certification, advanced programming, and professional incident-response experience are not assumed. The proposed entry baseline is general computer literacy plus basic IP/network, Windows, Linux, web/email, and evidence-recording familiarity.

Use the [Learner Entry Profile & Readiness Checklist](learner-readiness-checklist.md) to identify support needs. This profile remains a proposal until confirmed for the actual cohort.

## Design principles
- Capability-led, not tool-led.
- Concepts precede vendor-specific implementation.
- Progress from individual telemetry sources to cross-source investigations.
- Practice evidence collection, hypothesis testing, validation, and analyst communication.
- Keep all simulations within the authorized isolated lab.
- Separate student and instructor materials appropriately.
- Require measurable outcomes and traceable assessment evidence.

## Detailed curriculum
The proposed detailed design is documented in [Detailed Curriculum Design](detailed-curriculum-design.md). Each module now includes more discriminating outcome-to-lesson mappings, specific evidence expectations, and curriculum-level practical activity blueprints.

**Proposed duration:** 89 contact hours across 11 modules, excluding breaks, independent study, remediation, and lab installation time. This remains an estimate requiring instructor review and classroom piloting, not an approved schedule.

## Supporting design controls
- [Common assessment rubric](assessment-rubric.md) defines draft performance descriptors; it does not set grading weights or pass thresholds.
- [Assessment framework](assessment-framework.md) defines the assessment layers and evidence rules.
- [Prerequisite map](prerequisite-map.md) and [readiness checklist](learner-readiness-checklist.md) define proposed entry and progression gates.
- [Module reference catalog](references/module-reference-catalog.md) provides primary-source starting points for lesson development; each claim still requires lesson-level source verification.
- Practical activity blueprints are not final student lab instructions. Exact steps, tested versions, troubleshooting, reset, and instructor preparation remain production work.

## Proposed 11-module sequence
1. [SOC Fundamentals & Security Operations](../lectures/01-soc-fundamentals/README.md)
2. [SOC Lab Architecture & Deployment](../lectures/02-soc-lab-architecture/README.md)
3. [Endpoint Detection & Investigation](../lectures/03-endpoint-detection-investigation/README.md)
4. [Phishing & Email Security Investigation](../lectures/04-phishing-email-investigation/README.md)
5. [Network Security Monitoring & Analysis](../lectures/05-network-security-monitoring/README.md)
6. [Network Intrusion Detection & Prevention](../lectures/06-network-intrusion-detection/README.md)
7. [Web Security Monitoring & Investigation](../lectures/07-web-security-investigation/README.md)
8. [Incident Response](../lectures/08-incident-response/README.md)
9. [Attack Simulation & Detection Validation](../lectures/09-attack-simulation-detection-validation/README.md)
10. [Integrated Threat Investigation — Operation Shadow Access](../lectures/10-operation-shadow-access/README.md)
11. [SOC Capstone Project](../lectures/11-soc-capstone/README.md)

## Learning progression
SOC operations fundamentals → lab and telemetry foundations → endpoint/email/network/IDS/web investigation → incident response → controlled simulation and detection validation → integrated investigation → capstone.

## Current lab direction
VMware Workstation, Splunk Enterprise only, pfSense with integrated Suricata, Windows with Sysmon, Kali Linux, and an Ubuntu web server in a segmented DMZ. Mailpit may support local email exercises. Detailed versions and configuration belong in `lab-environment/`.

This is a proposed baseline, not evidence of completed deployment or validation. Wazuh, Splunk ES, and standalone Suricata are not part of the current baseline.

## Current core exclusions
Digital forensics, memory forensics, Active Directory, and vulnerability management require a separate scope decision before inclusion.

## Decisions still required
Confirm cohort entry profile, whether 89 contact hours fit the delivery model, assessment weighting/pass threshold, retake/remediation, individual/team balance, delivery schedule, and whether Mailpit is installed as a standard component or remains optional. Project Owner approval is required before this curriculum is marked approved or released.
