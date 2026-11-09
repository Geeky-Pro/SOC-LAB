# Deployment Guide

> Status: draft procedure. Test on a clean reference host before classroom release.

## Phase 0 — Preflight
- Confirm VMware Workstation, hardware virtualization, free disk, RAM, and CPU.
- Check proposed subnets against LAN, VPN, Docker, and existing VMnets.
- Obtain installers from official sources and verify checksums where available.
- Record versions and license requirements.
- Create a lab directory outside the Git working tree.

## Phase 1 — VMware networks
1. Create one NAT-backed network for pfSense WAN.
2. Create isolated VMnets for MGMT, SOC, DMZ, Endpoint, and Kali.
3. Configure DHCP consistently: disable VMware DHCP if pfSense DHCP is used.
4. Confirm no internal VMnet is bridged.
5. Record the VMnet-to-zone mapping.

## Phase 2 — pfSense and Suricata
1. Create pfSense with six NICs and map each to its intended zone.
2. Install pfSense from the official image.
3. Assign gateway addresses from the addressing plan.
4. Restrict management access.
5. Configure DNS, NTP, and only required DHCP.
6. Install a Suricata package compatible with the selected pfSense release.
7. Configure monitored interfaces, ruleset, and alert logging.
8. Apply least-privilege firewall rules.
9. Export a configuration backup.

## Phase 3 — Splunk Enterprise
1. Create the Splunk VM in SOC with a documented static address.
2. Install a supported Splunk Enterprise release from official documentation.
3. Secure administrative access and configure time synchronization.
4. Create indexes, retention, and required receiving interfaces.
5. Restrict management and ingestion by source network.
6. Test with a benign sample event.

## Phase 4 — Endpoint and DMZ
1. Install Windows in Endpoint and verify gateway/time.
2. Install Sysmon with a documented configuration.
3. Install the selected supported collection component.
4. Install Ubuntu Server in DMZ and deploy a minimal web service.
5. Configure approved log forwarding.
6. Confirm only required collection and admin flows are permitted.

## Phase 5 — Kali and optional Mailpit
1. Install Kali on the Kali VMnet only.
2. Verify it cannot reach the host physical LAN or unrestricted WAN.
3. Add narrowly scoped rules for the exercise target.
4. Deploy Mailpit only if email exercises require it; use synthetic messages.

## Phase 6 — Integration
Generate benign Windows, web, firewall, and Suricata test events. Confirm delivery, timestamps, host identity, source type, parsing, and searchability. Execute the validation checklist, capture sanitized evidence, and snapshot the clean baseline.

## Release gate
Do not label the environment classroom-ready until a clean rebuild passes validation on a representative student host. Record versions, deviations, and known limitations.
