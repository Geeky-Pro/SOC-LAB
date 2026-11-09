# Telemetry Source Catalog

> **Status:** initial catalog. Source readiness is NOT VALIDATED until actual events and fields are inspected.

## Source readiness states
- `planned`: intended source, not configured.
- `configured`: collection settings applied.
- `receiving`: events are arriving.
- `parsed`: required fields are extracted and checked.
- `validated`: representative test events and failure cases were checked.
- `degraded`: source is present but incomplete or unreliable.
- `retired`: no longer used.

## Initial source inventory

| Source | Expected telemetry | Candidate transport | Readiness |
|---|---|---|---|
| Windows + Sysmon | Process, network, logon, file/registry events as configured | Supported Windows collection path to Splunk | NOT VALIDATED |
| pfSense | Firewall and selected system events | Configured remote logging/collector | NOT VALIDATED |
| Suricata on pfSense | Alerts and selected metadata | Package-compatible export/collector | NOT VALIDATED |
| Ubuntu web server | Access and error logs | Supported Linux collection path | NOT VALIDATED |
| Kali activity | Activity visible in sensor/target logs and packet telemetry | Indirect observation through lab sensors | NOT VALIDATED |

## Required record for each source
Record:
- Source name, host role, OS/product version, and owner.
- Collection agent/forwarder, version, and configuration reference.
- Index, sourcetype, host identity, and event-time field.
- Expected fields with sample values from sanitized real test events.
- Event volume, retention needs, and known collection delays.
- Network path, firewall dependencies, and permitted ports.
- Health check, failure symptoms, and recovery procedure.
- Data quality limitations and privacy considerations.
- Last observed event, validation date, and evidence reference.

## Important constraints
Do not assume exact ports, sourcetypes, indexes, field extractions, or Suricata EVE delivery behavior until the chosen product versions and collection method have been tested. Use the lab telemetry pipeline as the architecture reference. Missing events must be investigated as collection/visibility gaps, not interpreted as proof that behavior did not occur.
