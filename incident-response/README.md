# Incident Response Foundation

> **Status:** draft — pending independent review and Project Owner approval  
> **Version:** 0.1  
> **Validation:** NOT VALIDATED — documentation baseline only

## Purpose

This directory defines reusable, vendor-neutral incident response guidance for SOC-LAB. It supports analyst learning and scenario design; it is not an organizational incident response policy, legal directive, or production runbook.

## Documents

| Document | Purpose |
|---|---|
| [Framework](framework.md) | Scope, principles, authority, and relationship to NIST CSF 2.0 |
| [Classification and severity](classification-and-severity.md) | Proposed educational incident categories and prioritization model |
| [Incident lifecycle](incident-lifecycle.md) | End-to-end response workflow and state transitions |
| [Triage procedures](triage-procedures.md) | Initial validation, prioritization, scoping, and escalation |
| [Containment, eradication, and recovery](containment-eradication-recovery.md) | Decision guidance for limiting impact and restoring operations |
| [Evidence and recordkeeping](evidence-and-recordkeeping.md) | Minimum evidence handling and incident record expectations |
| [Communications and escalation](communications-and-escalation.md) | Stakeholder coordination, escalation, and status updates |
| [Playbook standard](playbook-standard.md) | Requirements for reusable and scenario-specific playbooks |

## Templates

- [Incident record template](templates/incident-record.template.md)
- [Response playbook template](templates/response-playbook.template.md)

## Placement and ownership

- Shared procedures and standards belong here.
- Scenario-specific playbooks, injects, evidence, and answer keys belong inside the relevant `lectures/<module-id>/` directory.
- The Content Engineer may draft and revise these materials.
- The Quality Reviewer independently assesses them and reports findings.
- Only the Project Owner can approve content for intended use or authorize release.

## Teaching and lab boundaries

SOC-LAB is an isolated educational environment. Learners practice analysis and propose response actions. Potentially disruptive actions (disconnecting a VM, changing firewall policy, disabling an account, deleting files, or rebuilding a host) require explicit instructor authorization and a documented reset path. Never target systems outside the authorized lab.

The current lab baseline includes Splunk Enterprise, pfSense with integrated Suricata, Windows with Sysmon, Kali Linux, and an Ubuntu web server in a segmented DMZ. Do not assume response automation, EDR isolation, enterprise ticketing, or Splunk Enterprise Security capabilities are available.

## Reference baseline

The primary current reference is NIST SP 800-61 Rev. 3 (April 2025), aligned with CSF 2.0. It supersedes SP 800-61 Rev. 2. The operational stages in these teaching procedures are a practical workflow, not a claim that NIST Rev. 3 prescribes one universal linear lifecycle.

- NIST SP 800-61r3: https://doi.org/10.6028/NIST.SP.800-61r3
- NIST Incident Response project: https://csrc.nist.gov/projects/incident-response
- CISA Federal Government Cybersecurity Incident and Vulnerability Response Playbooks: https://www.cisa.gov/resources-tools/resources/federal-government-cybersecurity-incident-and-vulnerability-response-playbooks

## Change and validation

Review technical references and organizational assumptions before each course release. Record document review separately from tabletop exercise, lab execution, and operational validation. No procedure in this directory is currently represented as tested in a live environment.
