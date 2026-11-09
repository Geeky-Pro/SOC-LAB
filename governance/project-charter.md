# SOC-LAB Project Charter

## Purpose

SOC-LAB is a practical learning program for developing the knowledge, investigative judgment, and operational skills required for entry-level and developing SOC analysts.

## Mission

Provide a coherent, safe, reproducible learning experience that connects security concepts, telemetry, detection, investigation, incident response, and validation.

## Intended audience

A cohort of learners studying SOC operations through instructor-led teaching and hands-on exercises. Materials should support both instructor delivery and independent student practice.

## Scope

The current program focuses on:
- SOC foundations and operational workflows.
- SOC lab architecture and deployment.
- Endpoint, email, network, intrusion, and web security investigation.
- Incident response.
- Attack simulation and detection validation.
- Integrated investigation and capstone exercises.

## Current lab baseline

The current implementation direction uses VMware Workstation, Splunk Enterprise, pfSense with integrated Suricata, Windows endpoints with Sysmon telemetry, Kali Linux, and an Ubuntu web server in a segmented lab. Mailpit may support local email exercises. Exact versions and resource requirements must be maintained in the lab documentation.

The current Splunk direction is Splunk Enterprise only. Other platforms may be discussed as alternatives or future extensions, but must not be presented as deployed baseline components without an explicit decision.

## Out of scope for the current curriculum

Digital forensics, memory forensics, Active Directory, and vulnerability management are not core modules in the current approved direction. They may be reconsidered through a documented scope decision.

## Governance

The Project Owner approves architecture, curriculum, scope changes, and releases. The Instructor delivers and adapts teaching within approved learning outcomes. Reviewers evaluate content. AI agents assist but do not hold approval authority.

## Success criteria

- Learning outcomes map to practical activities and assessments.
- Labs can be deployed and reset using documented steps.
- Scenarios provide observable evidence and expected investigative reasoning.
- Technical and instructional reviews are recorded.
- Students receive clear guides; instructors receive delivery notes and answer keys.
- Releases are traceable and do not contain secrets or unlicensed material.
