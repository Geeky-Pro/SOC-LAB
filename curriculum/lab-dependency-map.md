# Lab Dependency Map

> **Status:** draft — logical dependencies only; not a deployment validation record

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
| Mailpit (optional) | Local email exercises | 04, 10, 11 |

## Logical telemetry paths
- Windows/Sysmon → configured collection path → Splunk Enterprise.
- pfSense/Suricata → configured collection path → Splunk Enterprise.
- Ubuntu web logs → configured collection path → Splunk Enterprise.
- Kali traffic → isolated lab network → pfSense/Suricata and destination telemetry.
- Mailpit artifacts → local email investigation workflow.

Exact collection methods, ports, addresses, parsing, indexes, and sourcetypes must be documented and validated in `lab-environment/` and `detection-engineering/`.

## Network constraints
Use the approved `10.0.0.0` addressing plan. Kali is assigned to `10.0.90.0/24`. Other segment addresses and routes must come from the approved lab architecture; do not invent them here.

## Module dependencies

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
