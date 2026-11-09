# Evidence and Incident Recordkeeping

> **Status:** draft  
> **Validation:** NOT VALIDATED

## 1. Purpose and limits

This document defines minimum operational recordkeeping for SOC-LAB investigations. It is not a digital forensics or memory forensics procedure and does not authorize collection of personal or restricted data.

## 2. Evidence handling principles

- Collect only what is authorized, relevant, and proportionate to the exercise or incident.
- Preserve original records where possible; analyze copies or exports.
- Do not alter, delete, rename, or overwrite source evidence.
- Record who collected or handled an item, when, from where, and how.
- Use consistent timestamps and explicitly record time zone and clock uncertainty.
- Restrict access to evidence and avoid placing sensitive material in public repositories or unapproved channels.
- Record integrity checks (for example, a cryptographic hash) when the workflow and tools support them; do not claim integrity verification if it was not performed.
- Preserve provenance: source system, query/filter, export method, time range, and relevant configuration.
- Escalate suspected legal, privacy, or regulatory issues to the designated authority.

## 3. Evidence register fields

| Field | Description |
|---|---|
| Evidence ID | Unique reference within the incident |
| Description | What the item represents |
| Source | Host, log source, network sensor, application, or reporter |
| Collection time | Timestamp with time zone |
| Event time range | Time range represented by the data |
| Collector | Person/role collecting the item |
| Method | Query, export, capture, or other authorized method |
| Original/reference location | Controlled location or system reference; never a secret-bearing public URL |
| Integrity | Hash/verification method and result, if actually performed |
| Handling history | Transfers, access, transformations, and analysis copies |
| Limitations | Missing fields, clock skew, truncation, retention gaps, or uncertainty |

## 4. Incident timeline

Maintain a chronological record of:
- observed events and supporting evidence IDs;
- analyst actions and queries;
- decisions and approvals;
- containment, remediation, and recovery actions;
- communications and escalations;
- state and severity changes.

Distinguish the time an event occurred from the time it was detected, collected, or reported.

## 5. SOC-LAB evidence sources

Possible sources include Windows/Sysmon events, Splunk search results, pfSense and Suricata logs, PCAP files, Ubuntu web logs, and Mailpit messages. Availability depends on the actual lab configuration. Verify source readiness and document missing telemetry rather than assuming it exists.

Use synthetic or sanitized evidence in teaching materials. Do not commit real credentials, tokens, personal data, unlicensed data, or large raw captures. Store lab evidence only in approved locations and follow the repository security and data-handling policies.

## 6. Reporting and retention

The incident lead determines the approved record location, access, retention, and sharing rules. These details are organization-specific and must not be invented by a learner. In classroom exercises, use the instructor-designated workspace and remove generated data during cleanup where appropriate.

## 7. References

- NIST SP 800-61r3: https://doi.org/10.6028/NIST.SP.800-61r3
- NIST Incident Response project: https://csrc.nist.gov/projects/incident-response
