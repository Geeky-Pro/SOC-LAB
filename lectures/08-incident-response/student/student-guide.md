# Student Guide — Module 08: Incident Response

[النسخة العربية](./student-guide-ar.md)

> **Status:** draft — student-facing  
> **Estimated time:** 8 hours (480 minutes; proposed, instructor may adjust)  
> **Version:** 0.1

## 1. What you will learn

You will practice distinguishing events and incidents, triaging reports, building evidence-based timelines, assigning provisional severity, recommending proportionate responses, communicating status, documenting decisions, and identifying improvements.

## 2. Before you begin

### Prerequisites
Review SOC operations, lab scope and safety, endpoint investigation, network monitoring, intrusion detection, and web security investigation.

### Resources
This guide, lesson materials, instructor-provided scenario brief/evidence pack, and templates supplied in class. Lab access is only available when explicitly authorized.

### Safety
- Work only within the instructor-approved SOC-LAB scope.
- Do not scan or interact with public or third-party systems.
- Do not run exploit code, malware, destructive commands, or unapproved changes.
- Do not isolate VMs, disable accounts, change firewall rules, delete files, or restart services without explicit instructor authorization.
- Do not contact external parties or make legal/privacy notification decisions.
- Do not include credentials, personal data, or unrelated host information in submissions.

## 3. Key terms

| Term | Meaning |
|---|---|
| Event | Observable occurrence in a system or network |
| Alert | Notification that an event or pattern may need review |
| Investigation | Authorized analysis to determine what happened |
| Suspected incident | Credible indication of an incident, not yet confirmed |
| Confirmed incident | Occurrence meeting the applicable incident threshold |
| Triage | Initial validation, prioritization, and routing |
| Containment | Action intended to limit ongoing impact or spread |
| Eradication | Removal of the cause or unauthorized access |
| Recovery | Restoration and verification of trusted service |
| Evidence provenance | Where evidence came from and how it was obtained/handled |

## 4. Learning activities

### A — Classify the signal
Classify each supplied example and explain what additional evidence is needed for ambiguous cases.

### B — Write a triage note
Record report source/time/time zone, affected asset/service, time window, direct observations, hypotheses, alternatives, unknowns, provisional category/severity, owner, escalation, and next checkpoint.

### C — Build a timeline
Order supplied evidence by time. Record evidence ID, timestamp/time zone, observation, interpretation, and confidence. Mark clock uncertainty and missing intervals.

### D — Compare response options
For at least two options, record risk reduction, evidence basis, business impact, decision authority, dependencies, rollback, and verification. Do not execute proposed actions without instructor authorization.

### E — Communicate and close
Prepare a situation report and incident record. Define recovery checks, monitoring, residual risk, closure criteria, and two improvement actions.

## 5. Tabletop scenario

Use only the student brief and evidence released by your instructor. Do not seek or access the instructor master or answer guidance.

## 6. Evidence submission

| Artifact | Required content |
|---|---|
| Triage note | Facts, hypotheses, unknowns, scope, priority, owner, checkpoint |
| Timeline/evidence matrix | Time, source ID, observation, interpretation, confidence, gaps |
| Decision log | Options, trade-offs, approver, rollback, verification |
| Situation report | Status, impact, confidence, actions, decisions needed, next update |
| Incident record | Classification, severity rationale, evidence, decisions, recovery/closure |
| After-action notes | Two lessons and measurable improvements |

## 7. Troubleshooting

If a source is unavailable, a search returns no data, timestamps do not align, or a field is missing:
- Record the limitation.
- Do not invent a result or field.
- Ask the instructor whether to use a synthetic evidence card.
- Explain how the limitation affects confidence and scope.

## 8. Completion checklist

- [ ] I separated facts, hypotheses, and unknowns.
- [ ] I cited important observations to supplied evidence.
- [ ] I justified category and provisional severity.
- [ ] I compared response options and identified approval authority.
- [ ] I prepared a situation report and incident record.
- [ ] I defined recovery checks and monitoring.
- [ ] I proposed two measurable improvements.
- [ ] I followed scope and safety rules.

## 9. Reflection

Which evidence most influenced your assessment? What did you assume that the evidence did not prove? What information was unavailable? Which response was proportionate? What would you verify before closure? What would you improve?

## 10. Further reading

- NIST SP 800-61 Rev. 3: https://doi.org/10.6028/NIST.SP.800-61r3
- NIST CSF 2.0: https://doi.org/10.6028/NIST.CSWP.29
