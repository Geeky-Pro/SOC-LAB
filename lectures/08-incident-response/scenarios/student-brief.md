# Student Brief — Suspicious Web Server Activity

[النسخة العربية](./student-brief-ar.md)

> **Status:** draft  
> **Scenario ID:** IR-TTX-01  
> **Audience:** Student  
> **Estimated time:** 120 minutes  
> **Evidence status:** May include synthetic instructor-prepared artifacts. The instructor will label each item.

## Situation

At 09:20 local time, the SOC receives a report that the public-facing training web server may be behaving unusually. A monitoring analyst noticed a burst of unusual requests followed by a server-side error. The service is still responding, but the service owner asks whether it should be taken offline.

You are the SOC response team. Assess the report, explain what is known and unknown, and recommend proportionate next steps.

## Scope and safety

- Use only evidence and systems explicitly provided by the instructor.
- Do not scan, connect to, or test public or third-party systems.
- Do not run exploit code, malware, destructive commands, or unapproved configuration changes.
- Do not disable accounts, isolate VMs, alter firewall rules, delete files, or restart services unless explicitly authorized.
- Do not contact external parties. Escalate legal, privacy, and notification questions to the instructor-defined authority.

## Team roles

Assign incident lead, SOC analyst, technical liaison, recorder, and communications lead. One learner may hold multiple roles in a small group. The instructor identifies the exercise decision authority.

## Tasks

1. Register the report and separate facts, hypotheses, and unknowns.
2. Decide whether the available information represents an event, alert, investigation, suspected incident, or confirmed incident.
3. Identify affected assets, identities, services, and the evidence-supported time window.
4. Build a chronological timeline and cite every observation to an evidence ID.
5. Assign a provisional category and P1–P4 teaching severity; explain what could change the rating.
6. Recommend immediate actions and at least one alternative. State approval, business impact, rollback, and verification requirements.
7. Prepare a situation report for the decision authority.
8. Define recovery checks, monitoring, closure criteria, and two improvement actions.

## Required submissions

| Artifact | Minimum content |
|---|---|
| Triage note | Source, time/time zone, facts, hypotheses, unknowns, scope, provisional priority, owner, checkpoint |
| Timeline/evidence matrix | Time, observation, source ID, interpretation, confidence, gaps |
| Decision log | Options, benefits/risks, impact, authority, approval state, rollback, verification |
| Situation report | Summary, impact, confidence, actions, decisions needed, owner, next update |
| Incident record | Status, category, severity rationale, scope, evidence references, decisions, recovery/closure |
| After-action notes | Two lessons and owner-assigned measurable improvements |

## Evidence discipline

- Reference supplied evidence; do not invent event IDs, timestamps, fields, or telemetry.
- Distinguish direct observation from interpretation.
- Record time zone and possible clock differences.
- If evidence is missing, state what is missing and how it affects confidence.
- A network alert alone does not prove successful compromise.
- A suspicious request alone does not prove data theft or persistence.
- Preserve earlier severity decisions and their rationale when reassessing.

## Completion

Explain what you recommend, why the evidence supports it, who must approve it, and how success would be verified.
