# Student Guide — Module 01: SOC Fundamentals & Security Operations

[النسخة العربية](./student-guide-ar.md)

> **Status:** draft  
> **Audience:** Student  
> **Related assets:** lesson content L01-01 to L01-06  
> **Estimated contact time:** 6 hours  
> **Version:** 0.1

## 1. What you will learn

By the end of this module, you should be able to:
- Explain what a SOC does and how its roles and responsibilities differ.
- Distinguish events, telemetry, indicators, alerts, cases, incidents, and findings.
- Triage an alert using evidence, scope, context, confidence, impact, and urgency.
- Prioritize work and identify when escalation is required.
- Write a case note and handoff that another analyst can continue.

## 2. Before you begin

### Prerequisites
No previous SOC experience is required. Basic computer use is expected. The instructor may provide a short refresher on networking, Windows, Linux, and common security terms.

### Required resources
- This guide and the lesson materials.
- A note-taking application or printed worksheet.
- The synthetic alert bundle in Section 5.

No virtual machine, Splunk account, or external system access is required.

### Safety rules
- All records in this guide are synthetic and invented for training.
- Do not use the identifiers, names, or addresses against real systems.
- Do not attempt to reproduce the alerts on public or third-party systems.
- Do not include real personal information or credentials in your submissions.

## 3. Key terms

| Term | Meaning |
|---|---|
| SOC | A people, process, and technology capability that monitors, investigates, communicates, and coordinates security operations. |
| Event | A recorded occurrence or state change. |
| Telemetry | Data collected about systems, identities, networks, or applications. |
| Indicator | An observable value or pattern that may help identify activity. |
| Alert | A notification that a rule, analytic, product, or person has identified something for review. |
| Case | A tracked record of an alert or investigation, including ownership, evidence, decisions, and status. |
| Incident | An event or group of events classified under organizational policy as a cybersecurity incident. |
| Finding | A conclusion supported by the evidence currently available. |
| Triage | Initial structured assessment to determine validity, scope, context, urgency, and next action. |
| Escalation | Routing a case to a person or team with required authority or expertise. |
| Handoff | A structured transfer of case ownership, evidence, decisions, and next steps. |

## 4. Your triage worksheet

Complete this worksheet for each assigned alert.

### A. Record identity
- Alert/case ID:
- Source:
- Time window and timezone:
- Affected account/asset/service:
- Scope and authorization confirmed? Explain.

### B. Observed facts
List at least three facts. Each fact must include a source and time or record locator.

| # | Fact | Source/time/locator |
|---|---|---|
| 1 | | |
| 2 | | |
| 3 | | |

### C. Hypotheses and unknowns
- Hypothesis 1:
- Hypothesis 2:
- Alternative benign explanation:
- Unknown 1:
- Unknown 2:
- Unknown 3:

### D. Assessment
- Confidence: low / medium / high — explain.
- Potential impact: low / medium / high — explain.
- Urgency: low / medium / high — explain.
- Current disposition:
- Why is this the most defensible disposition?
- What evidence would change your conclusion?

### E. Next action
- Specific action:
- Responsible role:
- Escalation trigger:
- Required approval or constraint:

## 5. Synthetic alert bundle

All names, identifiers, addresses, and timestamps are invented. Timezone: UTC. These records are not collected from a real organization and do not describe a real incident.

| Record | Time | Source | Observation | Initial alert |
|---|---|---|---|---|
| A-01 | 08:55 | Identity monitoring | 12 failed sign-ins for standard account U-104 from source S-22; one success at 08:57 | Repeated authentication failures |
| A-02 | 09:02 | Endpoint monitoring | A new scheduled task was created on workstation WS-17 by account IT-MAINT | Persistence-like configuration change |
| A-03 | 09:05 | Web monitoring | Web service returned 28 HTTP 404 responses from one client over 3 minutes | Unusual web request pattern |
| A-04 | 09:07 | Firewall monitoring | Connection attempt from lab client K-01 to a blocked internal destination; denied by policy | Denied inter-zone connection |
| A-05 | 09:10 | Endpoint monitoring | Antivirus quarantined a test file named training-eicar.txt on isolated workstation WS-22 | Test-file quarantine |
| A-06 | 09:14 | Change record | Approved maintenance window lists IT-MAINT on WS-17 from 09:00–09:30 | Change context |
| A-07 | 09:16 | Asset inventory | WS-17 is a standard engineering workstation; WS-22 is a training endpoint | Asset context |
| A-08 | 09:20 | Identity context | U-104 is a standard employee account; source S-22 ownership is not yet confirmed | Identity context |

### Questions for the bundle

1. Which records are alerts, events, or contextual evidence?
2. Which records might be related? What evidence supports the relationship?
3. Which record requires the earliest follow-up? Explain impact, urgency, and confidence separately.
4. What do you know about A-01, and what remains unknown?
5. Does A-02 become automatically benign because a maintenance window exists?
6. Does A-03 prove that the web service was exploited?
7. Does A-04 prove that the destination was reached?
8. What does A-05 prove, and what does it not prove?

## 6. Queue-prioritization worksheet

Use the following four case cards. They are separate from the alert bundle and are designed to test prioritization.

| Case | Summary | Context |
|---|---|---|
| Q-01 | A privileged account has a successful sign-in from a source not recognized in the current asset inventory. | The account has administrative privileges; activity may still be legitimate but requires rapid validation. |
| Q-02 | A standard user has three failed sign-ins and no successful sign-in. | No other suspicious activity is supplied; the user is available for confirmation. |
| Q-03 | A critical customer-facing service shows unusual errors during an approved maintenance window. | Change owner confirmation is pending; service impact is not yet known. |
| Q-04 | A known training endpoint quarantined the documented test artifact during the scheduled exercise. | The exercise record and host identifier match the supplied context. |

### Your task
- Rank Q-01 to Q-04 by the order you would handle them.
- Identify which case should be escalated now and to whom.
- State which case can be handled through routine validation.
- Explain what additional evidence could change your ranking.
- Do not use a numerical priority formula unless your instructor supplies one.

There may be more than one defensible ranking. Your reasoning and evidence matter more than matching a single answer.

## 7. Handoff template

**Case ID and status:**  
**Summary:**  
**Scope (accounts/assets/services and time window):**  
**Facts (source and timestamp):**  
**Current assessment and confidence:**  
**Potential impact and urgency:**  
**Actions completed and results:**  
**Unknowns and alternative explanations:**  
**Requested next action and responsible role:**  
**Escalation trigger / required approval:**  

## 8. Case-note quality checklist

- [ ] Scope and authorization are clear.
- [ ] Facts are traceable to sources and timestamps.
- [ ] Facts are separated from hypotheses.
- [ ] Confidence and uncertainty are stated.
- [ ] Impact and urgency are explained separately.
- [ ] Actions completed and results are recorded.
- [ ] Next action is specific and assigned.
- [ ] Privacy and authorization boundaries are respected.
- [ ] Another analyst could continue the work.

## 9. Evidence submission

Submit:
1. Alert classification table.
2. Individual triage records for at least two alerts.
3. Team queue-priority order with rationale.
4. One escalation/handoff message.
5. Individual reflection describing one uncertainty and one next investigative action.

Do not include credentials, personal data, or unrelated system information.

## 10. Reflection

- What did you observe?
- Which evidence most strongly supports your assessment?
- What remains uncertain?
- What alternative explanation did you consider?
- What would you investigate next?
- Which action would require approval from another role?

## 11. Further reading

- NIST Cybersecurity Framework (CSF) 2.0 — https://www.nist.gov/cyberframework
- NIST NICE Framework Resource Center — https://www.nist.gov/itl/applied-cybersecurity/nice/nice-framework-resource-center
- NIST SP 800-61 Rev. 3 — https://csrc.nist.gov/pubs/sp/800/61/r3/final
