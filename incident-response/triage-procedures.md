# Incident Triage Procedures

> **Status:** draft  
> **Validation:** NOT VALIDATED

## 1. Objective

Triage determines whether a report warrants further investigation, how urgently it should be handled, and what immediate coordination is needed. Triage is not a substitute for a full investigation or formal forensic examination.

## 2. Initial handling checklist

1. **Acknowledge and register**
   - Assign a unique incident or case identifier.
   - Record reporter/source, received time, time zone, and communication channel.
   - Preserve the original alert/report reference.
2. **Understand the signal**
   - What was observed?
   - Which detection, person, or system raised it?
   - When did it begin, and is it ongoing?
   - What is directly observed versus inferred?
3. **Check context**
   - Identify affected hostnames, IPs, accounts, services, and business owners.
   - Confirm whether activity is expected, approved, or part of a scheduled test.
   - Check relevant change windows and known maintenance.
4. **Assess potential impact**
   - Consider asset criticality, data sensitivity, scope, exposure, and availability.
   - Identify signs of active compromise, persistence, spread, or continuing loss.
5. **Assess confidence**
   - Corroborate with independent sources where available.
   - Record missing telemetry, parsing uncertainty, clock skew, and alternative explanations.
6. **Classify and prioritize**
   - Apply the proposed SOC-LAB category and provisional severity.
   - State why and what would change the assessment.
7. **Escalate and assign**
   - Notify the designated incident lead/instructor according to exercise rules.
   - Assign an owner and a next update/review time.
8. **Preserve references**
   - Record source event IDs, search references, filenames, and collection context.
   - Do not modify or delete original evidence.

## 3. Investigation pivots

Use only data sources that are actually available and authorized:
- Endpoint: process, user, host, logon, service, and Sysmon event context.
- Network: source/destination, protocol, time window, DNS/HTTP/TLS metadata, and packet capture where available.
- Firewall/IDS: pfSense rule events and Suricata alerts, subject to configured logging and verified export.
- Web: server access/error logs and relevant application context.
- Email: message headers and local Mailpit artifacts when the exercise uses Mailpit.
- SIEM: Splunk searches against verified indexes, sourcetypes, and fields.

Do not assume any particular index, sourcetype, field name, retention period, or telemetry source exists. Verify it against the lab's observed data and telemetry documentation.

## 4. Triage outcome

Choose and document one:
- Escalate as suspected/confirmed incident.
- Continue investigation with a named owner and next checkpoint.
- Monitor with a stated rationale and trigger for reopening.
- Close as benign, duplicate, or false positive with supporting evidence.
- Mark blocked when required data, authority, or access is unavailable.

## 5. Escalation triggers

Escalate promptly when there is credible evidence of:
- privileged account compromise;
- active command and control or unauthorized remote access;
- destructive behavior or material service disruption;
- suspected sensitive data exposure or exfiltration;
- multiple affected systems or likely lateral movement;
- compromise of a critical service or security control;
- uncertainty that could conceal severe impact.

Follow the organization's approved escalation and notification requirements. SOC-LAB learners should escalate to the instructor rather than contacting external parties.

## 6. Minimum triage note

Record the alert/report, observed facts, affected entities, time window, category, provisional severity, evidence references, confidence, alternative explanations, actions taken, escalation decision, owner, and next checkpoint.
