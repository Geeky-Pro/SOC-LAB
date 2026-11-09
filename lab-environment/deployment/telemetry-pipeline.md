# Telemetry Pipeline

> Status: logical design. Exact forwarding products, ports, parsing, and compatibility must be tested.

| Source | Events | Logical destination | Acceptance evidence |
|---|---|---|---|
| Windows + Sysmon | Process, network, logon, file/registry events as configured | Splunk via supported Windows collection path | Known test event searchable with correct host/time |
| pfSense | Firewall and selected system events | Splunk via configured remote logging/collector | Test rule event searchable and classified |
| Suricata in pfSense | Alerts and selected metadata | Splunk via package-compatible export/collector | Safe test alert searchable with signature and endpoints |
| Ubuntu web | Access and error logs | Splunk via supported Linux collection path | HTTP request searchable with URI/status/client/time |
| Kali | Activity observed by sensors and targets | Suricata, pfSense, Windows, or web telemetry | Expected evidence appears in relevant sources |

## Collection principles
- Use supported mechanisms for the exact OS/product versions.
- Do not assume a particular Suricata EVE forwarding method is available in every pfSense package release.
- Keep collection traffic on explicitly permitted paths to SOC.
- Synchronize clocks and preserve original event timestamps.
- Document index, sourcetype, host identity, parsing, and retention.
- Tune event volume to lesson objectives.
- Never commit credentials or secrets.

## Minimum source tests
- Windows: generate harmless process and network events; verify host attribution and fields.
- Web: make a benign HTTP request; verify URI, status, client, and timestamp.
- pfSense: trigger a known firewall rule; verify action and interface.
- Suricata: use a safe documented test signature; verify alert creation and delivery. Do not use real malware.

Before a detection depends on a source, document its index/sourcetype, expected fields, sanitized sample, search query, expected result, and blind spots. Shared searches belong in detection-engineering; module-specific searches stay with the module.
