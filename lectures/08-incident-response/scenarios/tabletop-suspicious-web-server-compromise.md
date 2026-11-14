# Tabletop Master — Suspicious Web Server Compromise

> **Status:** draft — public-safe scenario design; protected answer guidance excluded  
> **Scenario ID:** IR-TTX-01  
> **Difficulty:** foundational / intermediate  
> **Duration:** 120 minutes total, including debrief  
> **Evidence status:** synthetic scenario design; no lab execution claimed

## 1. Purpose and outcomes

Assess LO-08-01 through LO-08-06: signal validation, triage, timeline, classification/severity, proportionate response, communication, incident recordkeeping, and improvement.

## 2. Narrative

A public-facing Ubuntu web server in the isolated SOC-LAB DMZ hosts a training application. At 09:20, the SOC receives a report about unusual web requests and a subsequent application error. The service remains reachable. Later injects provide incomplete network context, a possible administrative access explanation, service-impact constraints, and recovery information.

Do not assert successful compromise, data exfiltration, persistence, or attacker identity unless a supplied evidence artifact supports that conclusion. A suspected-incident or blocked-pending-evidence outcome may be correct.

## 3. Authorized scope and safety

- **Environment:** isolated SOC-LAB VMware environment or synthetic evidence pack.
- **In-scope:** designated Ubuntu web-server VM and explicitly supplied related telemetry.
- **Potential sources:** Windows/Sysmon, Splunk Enterprise, pfSense/Suricata, web logs, optional packet-capture metadata. Include only sources verified for this delivery.
- **Excluded:** public internet targets, personal devices, unrelated student networks, external organizations.
- **Simulation:** discussion-based injects; no exploit, malware, destructive action, or external traffic required.
- **Impact:** no system state change in tabletop mode.
- **Reset:** not applicable to discussion-only delivery. Any separate live demonstration requires a snapshot and documented reset.

## 4. Roles

Incident lead; SOC analyst; technical owner; recorder; communications lead; instructor/decision authority. The instructor releases injects, controls scope, and approves any optional disruptive action.

## 5. Inject schedule

Do not reveal the full schedule to students. Pause between injects until teams record their current assessment.

| Inject | Time | Information released | Facilitator question |
|---|---:|---|---|---|
| I-01 Initial report | T+00 | At 09:20, an analyst reports a burst of unusual requests to the DMZ web server and an application error. Service remains available. | What is known directly? What do you need? |
| I-02 Web evidence | T+15 | Synthetic web-log excerpt shows repeated requests to an unusual path followed by HTTP 500 responses. No successful authentication or payload execution is established. | Does this prove compromise? What alternatives exist? |
| I-03 Network context | T+35 | Synthetic pfSense/Suricata summary reports an outbound connection shortly after the errors. Alert is generic and has no payload confirmation. | What does this alert prove and not prove? |
| I-04 Scope challenge | T+55 | Service owner reports no approved deployment in the window. A separate note says an administrator performed routine maintenance earlier, but exact time and source host are unknown. | How can the maintenance claim be verified? |
| I-05 Decision point | T+75 | Taking the server offline would interrupt a classroom exercise. Two discussion options are offered: narrow restriction under approval, or temporary VM isolation under approval. Neither action is executed. | Which is proportionate? Who approves? What is rollback? |
| I-06 Recovery | T+95 | A synthetic update says a known-good VM snapshot is available, but the team has not established whether the activity is understood or credentials need review. | What must be true before restoration? |

## 6. Evidence pack specification

All synthetic artifacts must be labeled **SYNTHETIC — FOR TRAINING** and use reserved documentation IP ranges or fictional identifiers.

| ID | Artifact | Minimum content | Limitation |
|---|---|---|---|
| E-01 | Initial SOC report | Report time, server asset ID, description, reporting source | Lead, not proof |
| E-02 | Web access/error excerpt | Timestamp/time zone, request path, status, source, request ID if available | Request/error does not prove code execution |
| E-03 | Firewall/IDS summary | Timestamp, source/destination, protocol, rule/alert summary | Generic alert does not prove malicious success |
| E-04 | Optional PCAP metadata | Capture interval, endpoints, protocol summary | No payload claim unless captured and reviewed |
| E-05 | Change/maintenance note | Claimed admin activity and incomplete time/source context | Must be corroborated |
| E-06 | Service owner impact note | Service criticality, downtime impact, backup/snapshot availability | Context, not technical verification |
| E-07 | Recovery verification card | Known-good baseline, health checks, monitoring window | Does not establish eradication by itself |

Do not fabricate Splunk indexes, sourcetypes, fields, event IDs, or exact log formats. If Splunk is used, attach a source manifest based on observed lab events. Otherwise provide evidence cards without claiming live telemetry.

## 7. Public-repository boundary

This file is a public scenario design document. It intentionally excludes protected answer keys and detailed expected analyst conclusions. Store any unreleased facilitator answer guidance in an access-controlled instructor repository or private distribution; the public GitHub path does not restrict access.

## 8. Response options

Learners compare at least two options, such as:
- Continue targeted monitoring and preserve evidence while rapidly validating activity.
- Apply a narrow, reversible restriction, subject to technical-owner assessment and instructor approval.
- Temporarily isolate the designated VM only if evidence and impact justify disruption and the decision authority approves.

For each option require objective, evidence basis, risk reduction, business impact, dependencies, approver, rollback, and verification. These are tabletop recommendations only.

## 9. Communications

Situation report includes case ID/status, factual summary and time, affected service/impact, category/severity/confidence, completed versus proposed actions, decisions required, evidence gaps, owner, and next update time.

External notifications and legal/privacy decisions remain outside student authority.

## 10. Debrief prompts

1. Which observation most changed your assessment?
2. Which conclusion did you revise?
3. What evidence was missing?
4. What was the least disruptive adequate response?
5. Who had authority to approve it?
6. What would you verify before restoration?
7. Which two improvements would strengthen the SOC?

## 11. Validation and limitations

- Scenario authored: yes, document only.
- Lab evidence captured: none supplied in this phase.
- Tabletop delivered: not yet.
- Lab execution and technical validation: not performed.
- Independent review: pending.
- Evidence pack specifications are not actual logs; verify source availability and schema before tool-specific exercises.

## 12. References

- NIST SP 800-61 Rev. 3 (2025): https://doi.org/10.6028/NIST.SP.800-61r3
- NIST CSF 2.0: https://doi.org/10.6028/NIST.CSWP.29
