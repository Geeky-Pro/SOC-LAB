# SOC-LAB Curriculum Overview

> **Status:** draft — pending Project Owner approval  
> **Version:** 0.1

## Purpose
Develop practical SOC capabilities: understanding security operations, working with telemetry, investigating suspicious activity, validating detections, responding to incidents, and communicating evidence-based conclusions.

## Audience
Learners developing foundational SOC analyst skills through instructor-led teaching and isolated hands-on exercises. Entry requirements and pacing remain to be confirmed.

## Design principles
- Capability-led, not tool-led.
- Concepts precede vendor-specific implementation.
- Progress from individual telemetry sources to cross-source investigations.
- Practice evidence collection, hypothesis testing, validation, and analyst communication.
- Keep all simulations within the authorized isolated lab.
- Separate student and instructor materials appropriately.

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
Confirm learner entry level, total contact hours, module order, outcome granularity, assessment thresholds, and delivery schedule. Project Owner approval is required before this curriculum is marked approved or released.
