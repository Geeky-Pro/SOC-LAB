# SOC-LAB Environment

> Status: draft architecture baseline; not deployed or practically validated.

## Design baseline
- One isolated virtual lab per student on VMware Workstation.
- Splunk Enterprise only; Splunk Enterprise Security is not a dependency.
- pfSense provides routing and segmentation; Suricata is installed inside pfSense.
- Windows 10/11 with Sysmon is the endpoint telemetry source.
- Ubuntu Server hosts the DMZ web workload.
- Kali Linux resides on 10.0.90.0/24.
- Mailpit is optional for local email exercises.

## Documentation map
- architecture/topology.md — trust zones and logical topology
- network/addressing-plan.md — IPv4 allocation and VMnet requirements
- network/traffic-flows-and-firewall-policy.md — least-privilege flows
- virtual-machines/inventory.md — VM roles and software
- virtual-machines/resource-planning.md — capacity planning
- deployment/deployment-guide.md — staged installation
- deployment/telemetry-pipeline.md — source-to-SIEM design
- validation/validation-checklist.md — acceptance tests
- validation/reset-and-recovery.md — rollback and rebuild

## Proposed trust zones

| Zone | Subnet | Purpose |
|---|---|---|
| Management | 10.0.10.0/24 | Controlled administration |
| SOC | 10.0.30.0/24 | Splunk Enterprise and collectors |
| DMZ | 10.0.20.0/24 | Ubuntu web workload |
| Endpoint | 10.0.40.0/24 | Windows and Sysmon |
| Kali | 10.0.90.0/24 | Authorized simulation |

These are proposed lab-internal ranges. Check for overlap with each student's LAN, VPN, Docker, and VMware networks before deployment.

## Safety and status
Do not bridge attack-generation VMs to physical or production networks. Use synthetic accounts, snapshots, scoped targets, and sanitized evidence. Never commit credentials, license files, private keys, student data, or VM images.

All procedures are drafts until executed on a clean reference host and supported by validation evidence. See curriculum/lab-dependency-map.md for module dependencies.
