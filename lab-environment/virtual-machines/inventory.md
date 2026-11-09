# Virtual Machine Inventory

> Status: baseline inventory. Freeze software versions only after compatibility testing.

| VM | Role | Network | Software | Required |
|---|---|---|---|---|
| pfSense | Routing, firewall, Suricata | WAN + five internal zones | pfSense and compatible Suricata package | Yes |
| Splunk server | SIEM | SOC | Splunk Enterprise | Yes |
| Windows endpoint | Endpoint telemetry | Endpoint | Windows 10/11, Sysmon, supported collection component | Yes |
| Ubuntu server | DMZ web workload | DMZ | Ubuntu Server, web service, supported log collector | Yes |
| Kali | Authorized simulation | Kali | Kali Linux tools required by lessons | Yes |
| Mailpit | Local email capture | Isolated mail segment or documented attachment | Mailpit | Optional |

## pfSense
Use six virtual NICs: WAN plus MGMT, SOC, DMZ, Endpoint, and Kali. Install Suricata as a pfSense package, not as a separate VM. Verify package compatibility with the selected pfSense release. Restrict management access and export a configuration backup.

## Splunk Enterprise
Place it in SOC. Use Splunk Enterprise only; Enterprise Security is not required. Configure secure administration, time synchronization, storage, indexes, and retention. Restrict receiving and management interfaces to approved sources. Keep license material outside Git and follow license terms.

## Windows
Use a supported Windows release and documented Sysmon configuration. Enable only lesson-relevant events and use a supported collection component to forward telemetry over the SOC path. Use synthetic accounts and non-sensitive data.

## Ubuntu
Place only in DMZ. Run a minimal web service, generate benign access/error logs, and forward required logs over the approved path. Restrict SSH and administration.

## Kali
Attach only to Kali VMnet. Use snapshots and explicitly scoped lab targets. Never enable bridged networking.

## VM manifest
For every class build, record OS/application versions, virtual hardware, VMnet mapping, disk format, checksums, snapshot name, and validation date. Do not commit VM disks.
