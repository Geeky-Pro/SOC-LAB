# Network and Addressing Plan

> Status: proposed baseline. Check conflicts on every student host.

| Zone | Network | Gateway | Suggested host |
|---|---|---|---|
| Management | 10.0.10.0/24 | 10.0.10.1 | Admin test host .10 if required |
| SOC | 10.0.30.0/24 | 10.0.30.1 | Splunk .10 |
| DMZ | 10.0.20.0/24 | 10.0.20.1 | Ubuntu web .10 |
| Endpoint | 10.0.40.0/24 | 10.0.40.1 | Windows .10 |
| Kali | 10.0.90.0/24 | 10.0.90.1 | Kali .10 |

Reserve .1 for pfSense. Record any additional static assignments. Suggested addresses may be changed if they conflict with local infrastructure.

## VMware requirements
- One NAT-backed WAN network for pfSense.
- Five isolated internal VMnets for the trust zones.
- Attach each VM only to its intended segment.
- Do not bridge Kali, Windows targets, or DMZ workloads to the physical LAN.
- Disable VMware DHCP on internal segments if pfSense DHCP is enabled; otherwise use a documented static-address plan.

## Conflict check
Inspect host LAN, VPN, Docker, and VMware networks before deployment. If a conflict exists, revise the affected subnet consistently in pfSense, VM settings, firewall rules, diagrams, and student instructions. Record each student's actual network map.

## DNS and time
Choose and document DNS and NTP sources. Synchronize all systems before timeline exercises. Permit only the required DNS/NTP flows; do not assume they are allowed between zones.

## Validation
Verify IP address, mask, gateway, DNS, and routes on every VM. Confirm gateway reachability and only the intended cross-zone destinations.
