# Lab Dependency Map

> **Status:** draft — logical dependencies only; not a deployment validation record.

## Baseline components

| Component | Learning use | Dependent modules |
|---|---|---|
| VMware Workstation | Isolated VMs and snapshots | 02–11 |
| pfSense | Segmentation, routing, firewall telemetry | 02, 05, 06, 09–11 |
| Suricata integrated in pfSense | Network IDS alerting | 06, 09–11 |
| Splunk Enterprise | Search, investigation, dashboards, correlation | 02–11 |
| Windows + Sysmon | Process, logon, file, and network telemetry | 03, 09–11 |
| Kali Linux | Authorized traffic generation and controlled emulation | 05–07, 09–11 |
| Ubuntu web server | Web service and access/application logs | 07, 09–11 |
| Mailpit (optional) | Local email exercises; Modules 10–11 can use sanitized .eml evidence packs when Mailpit is unavailable | 04, 10, 11 |

## Planned network zones

| Zone | Subnet | Main workload |
|---|---|---|
| Management | 10.0.10.0/24 | Controlled administration |
| SOC | 10.0.30.0/24 | Splunk Enterprise and collectors |
| DMZ | 10.0.20.0/24 | Ubuntu web server |
| Endpoint | 10.0.40.0/24 | Windows + Sysmon |
| Kali | 10.0.90.0/24 | Kali Linux |

These are proposed ranges. Students must check for overlap with physical LAN, VPN, Docker, and existing VMware networks. See lab-environment/network/addressing-plan.md.

## Logical telemetry paths
- Windows/Sysmon → supported collection path → Splunk Enterprise.
- pfSense firewall events → configured remote logging/collector → Splunk Enterprise.
- Suricata alerts from pfSense → tested package-compatible export/collector → Splunk Enterprise.
- Ubuntu web logs → supported collection path → Splunk Enterprise.
- Kali activity → pfSense/Suricata and destination telemetry.

Exact collection methods, ports, indexes, sourcetypes, and parsing must be documented and validated. See lab-environment/deployment/telemetry-pipeline.md.

## Module dependencies

Module 10 explicitly includes an email evidence artifact from Module 04. Mailpit remains optional; a sanitized, provenance-labeled .eml artifact is an accepted alternative. Module 11 uses whichever evidence sources are included in its assigned case pack.

| Module | Minimum capabilities |
|---|---|
| 01 | No deployed lab required |
| 02 | VMware, pfSense, Splunk Enterprise, segmented network |
| 03 | Windows/Sysmon, event collection, Splunk |
| 04 | Mailpit or safe sample email artifacts |
| 05 | Kali, packet capture/analysis, pfSense, Splunk |
| 06 | pfSense-integrated Suricata, event collection, Splunk |
| 07 | Ubuntu web server, logs, Kali, Splunk |
| 08 | Evidence from relevant prior modules and incident templates |
| 09 | Approved emulation, telemetry under test, Splunk |
| 10 | Combined endpoint, network, IDS, web, and SIEM telemetry |
| 11 | Integrated environment and capstone evidence |

## Validation gates
Verify VM versions, network isolation, intended routes, event generation and ingestion, timestamps/field extraction, student workflow, and cleanup/reset. Record evidence and deviations. This map describes planned dependencies only.
