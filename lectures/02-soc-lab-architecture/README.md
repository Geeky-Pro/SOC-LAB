# SOC Lab Architecture & Deployment

> **Status:** draft — pending module design, practical validation, and Project Owner approval  
> **Module ID:** 02-soc-lab-architecture  
> **Curriculum version:** 0.1

## Purpose
Teach learners to understand, deploy, and validate an isolated SOC-LAB environment, including trust zones, virtual machines, network paths, telemetry sources, and SIEM data flow.

## Preliminary learning outcomes
Learners should be able to:
- Explain the topology, trust boundaries, and role of each component.
- Map VMware virtual networks to pfSense interfaces and security zones.
- Deploy or verify the required virtual machines using a documented build manifest.
- Apply and test least-privilege inter-zone firewall rules.
- Verify endpoint, firewall/IDS, and web telemetry ingestion into Splunk Enterprise.
- Diagnose common network, collection, and resource issues.
- Capture sanitized validation evidence and restore a clean baseline.

These outcomes require measurable assessment criteria before release.

## Shared environment documentation
Use the canonical shared environment documentation:
- [Lab environment overview](../../lab-environment/README.md)
- [Logical topology](../../lab-environment/architecture/topology.md)
- [Addressing plan](../../lab-environment/network/addressing-plan.md)
- [Firewall policy and traffic flows](../../lab-environment/network/traffic-flows-and-firewall-policy.md)
- [VM inventory](../../lab-environment/virtual-machines/inventory.md)
- [Resource planning](../../lab-environment/virtual-machines/resource-planning.md)
- [Deployment guide](../../lab-environment/deployment/deployment-guide.md)
- [Telemetry pipeline](../../lab-environment/deployment/telemetry-pipeline.md)
- [Validation checklist](../../lab-environment/validation/validation-checklist.md)
- [Reset and recovery](../../lab-environment/validation/reset-and-recovery.md)

## Architecture baseline
- VMware Workstation; one isolated lab per student.
- Splunk Enterprise only for the current implementation.
- pfSense with Suricata integrated as a package; no separate Suricata VM.
- Windows 10/11 with Sysmon.
- Ubuntu Server in a dedicated DMZ.
- Kali Linux on 10.0.90.0/24.
- All other lab segments use the proposed 10.0.0.0 address plan documented in lab-environment/.

## Topics and teaching sequence
To be developed from the architecture docs: virtualization and VM networking; segmentation and trust zones; pfSense interface/rule design; SIEM placement; telemetry collection; validation and troubleshooting; baseline snapshots and recovery.

## Practical activities
To be authored using the canonical lab template after software versions and a clean reference deployment are validated.

## Assessment
Map assessment tasks to the final measurable outcomes and curriculum/assessment-framework.md.

## Validation status
- Technical documentation: draft
- Reference deployment: not executed
- Network isolation tests: not executed
- Telemetry ingestion tests: not executed
- Instructional review: not completed
- Project Owner approval: pending

## Change history
| Version | Date | Change | Status |
|---|---|---|---|
| 0.1 | 2026-11-10 | Module charter aligned with lab environment baseline | Draft |
