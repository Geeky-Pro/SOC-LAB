# Traffic Flows and Firewall Policy

> Status: proposed least-privilege policy; test before classroom use.

## Principles
- Default-deny between zones.
- Permit only flows required by a named learning objective.
- Keep Kali isolated from physical LAN and unrestricted Internet.
- Do not expose Splunk management or ingestion to WAN.
- Log relevant allowed and denied traffic without exhausting storage.

## Intended flows

| Source | Destination | Purpose | Default policy |
|---|---|---|---|
| Controlled admin path | pfSense management | Firewall administration | Allow narrowly |
| Controlled admin path | Splunk UI | SIEM administration | Allow narrowly |
| Windows | Splunk / approved collector | Endpoint telemetry | Allow required collection only |
| Ubuntu DMZ | Splunk / approved collector | Web telemetry | Allow required collection only |
| pfSense | Splunk / log receiver | Firewall and IDS telemetry | Allow tested method only |
| Kali | Ubuntu DMZ | Authorized web exercise | Temporary scoped allow |
| Kali | Windows | Controlled endpoint exercise | Deny unless explicitly required |
| DMZ | Endpoint / Management | Lateral movement | Deny by default |
| Kali | Host physical LAN / WAN | Uncontrolled egress | Deny |
| WAN | Internal zones | Unsolicited inbound | Deny |

## Implementation
1. Use aliases for approved hosts and services.
2. Apply rules on the ingress interface and document rule order.
3. Scope temporary exercise rules by source, destination, protocol, and duration.
4. Record expected telemetry and a cleanup step for every temporary rule.
5. Test NAT separately from inter-zone filtering.
6. Do not treat commonly used ports as final until the collection architecture and versions are selected.

## Exercise lifecycle
Every temporary rule needs an exercise ID, purpose, exact source/destination, protocol/service, expected event, start/end condition, and cleanup confirmation.

## Validation
Test allowed and denied flows from the source VM. Confirm firewall logs reflect the expected action and no secondary virtual adapter bypasses pfSense.
