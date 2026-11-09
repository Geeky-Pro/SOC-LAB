# Incident Classification and Severity

> **Status:** draft — proposed educational model  
> **Validation:** NOT VALIDATED

## 1. Purpose

Classification describes the nature of suspected activity. Severity prioritizes response based on potential or actual impact and urgency. They are related but not interchangeable: a category alone does not determine severity.

## 2. Suggested educational categories

Use one primary category and optional secondary tags. Categories are descriptive, not mutually exclusive.

| Category | Examples of activity to investigate |
|---|---|
| Malware / suspicious execution | Unexpected executable, script, persistence indicator, or malicious payload |
| Unauthorized access / account compromise | Suspicious authentication, unexpected privilege use, account takeover indicators |
| Data exposure / exfiltration | Unexpected transfer, public exposure, or unauthorized access to sensitive data |
| Network intrusion / command and control | Suspicious inbound access, beacon-like traffic, or unauthorized remote control |
| Web application / server compromise | Exploitation indicators, web shell suspicion, unauthorized content or process changes |
| Phishing / social engineering | Malicious message, credential harvesting, or user interaction with a lure |
| Denial of service / availability | Resource exhaustion or disruption affecting service availability |
| Policy / insider-related concern | Suspected misuse of authorized access or violation of security policy |

Do not label activity as insider abuse, data breach, or malware infection without sufficient evidence.

## 3. Severity dimensions

Assess and record the following dimensions:
- **Impact:** confidentiality, integrity, availability, safety, and operational consequences.
- **Scope:** number and criticality of affected assets, identities, services, and locations.
- **Data sensitivity:** whether regulated, confidential, personal, or business-critical data may be involved.
- **Exposure and spread:** external reachability, lateral movement, persistence, or continuing access.
- **Urgency:** active exploitation, ongoing exfiltration, destructive behavior, or time-sensitive business impact.
- **Confidence:** quality and corroboration of evidence; uncertainty must not be hidden.
- **Recoverability:** availability of trusted backups, alternate service, and restoration options.

A high-impact possibility with low confidence may still require urgent investigation; confidence is not a reason to ignore plausible severe harm.

## 4. Proposed SOC-LAB severity scale

This scale is for classroom prioritization only. It is not a production SLA or universal standard.

| Level | Teaching interpretation | Typical handling |
|---|---|---|
| **P1 — Critical** | Credible evidence of severe or ongoing impact, critical service disruption, widespread compromise, destructive activity, or high-risk data exposure | Immediate instructor/incident-lead escalation; continuous coordination in the exercise |
| **P2 — High** | Significant compromise or exposure affecting important assets, privileged identities, or multiple systems; material risk remains active | Urgent investigation and decision on containment |
| **P3 — Moderate** | Bounded suspected compromise or suspicious activity with limited known impact and no evidence of broad spread | Prioritized investigation with defined update checkpoints |
| **P4 — Low** | Low-impact, contained, or weakly corroborated activity requiring documentation or routine follow-up | Queue for review; preserve rationale and reassess if new evidence appears |

## 5. Decision method

1. Record known facts and unknowns.
2. Identify affected assets, identities, services, and data.
3. Assess each severity dimension.
4. Assign a provisional level with a short rationale.
5. Identify what evidence could raise or lower the level.
6. Escalate based on uncertainty, impact, and local authority rules.
7. Reassess whenever material new evidence or impact information arrives.

Severity is dynamic. Record changes, timestamps, and reasons; do not silently overwrite the initial assessment.

## 6. Minimum classification record

- Incident ID and status
- Primary category and secondary tags
- Provisional severity and rationale
- Affected assets / identities / services
- Known or suspected data impact
- Current activity and exposure
- Evidence confidence and gaps
- Decision owner and next review time

## 7. References

- NIST SP 800-61r3: https://doi.org/10.6028/NIST.SP.800-61r3
- CISA incident response playbooks (reference example; designed for FCEB agencies): https://www.cisa.gov/resources-tools/resources/federal-government-cybersecurity-incident-and-vulnerability-response-playbooks
