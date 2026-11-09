# Lab Validation Checklist

> Status: checklist template. No item is passed until evidence is collected.

## Host and hypervisor
- [ ] VMware and hardware virtualization work.
- [ ] Host resource headroom supports required simultaneous VMs.
- [ ] VM disks/snapshots are outside Git.
- [ ] No subnet overlaps host LAN, VPN, Docker, or existing VMnets.

## Network isolation
- [ ] pfSense WAN uses intended NAT uplink.
- [ ] Internal VMnets map to the correct zones.
- [ ] Kali is not bridged and cannot reach physical LAN.
- [ ] Inter-zone traffic traverses pfSense.
- [ ] DHCP, DNS, NTP, and static addressing do not conflict.

## Firewall and Suricata
- [ ] Management access is restricted.
- [ ] Default-deny between zones is verified.
- [ ] Required allow rules are scoped and logged.
- [ ] Suricata package matches pfSense version.
- [ ] Safe test alert is generated on intended interface.
- [ ] Firewall and IDS telemetry reaches the configured collector.

## Endpoint, web, and SIEM
- [ ] Windows address, gateway, time, and Sysmon configuration are correct.
- [ ] Known Windows event is searchable in Splunk.
- [ ] Ubuntu service is reachable only from intended sources.
- [ ] Known web access event is searchable.
- [ ] Splunk is reachable only from approved management/collection sources.
- [ ] Indexes, sourcetypes, host, timestamps, and fields are correct.
- [ ] Event volume and disk use remain within budget.

## Classroom and recovery
- [ ] Student steps are reproducible.
- [ ] Clean baseline snapshots exist.
- [ ] Temporary rules and test artifacts can be removed.
- [ ] Reset restores the intended clean state.
- [ ] Evidence is sanitized and contains no secrets or personal data.

## Validation record
| Field | Value |
|---|---|
| Build identifier | [Set] |
| VMware version | [Set] |
| pfSense / Suricata versions | [Set] |
| Splunk Enterprise version | [Set] |
| Windows / Sysmon versions | [Set] |
| Ubuntu / web versions | [Set] |
| Host hardware | [Set] |
| Date / validator | [Set] |
| Result | NOT VALIDATED |
| Evidence location | [Set] |
| Deviations | [Set] |

Unchecked items mean the environment remains unvalidated. Do not mark PASS without evidence.
