# L01-06 — Integrated Triage Workshop

> **Status:** draft  
> **Module:** 01-soc-fundamentals  
> **Duration:** 90 minutes  
> **Outcomes:** LO-01-03, LO-01-04, LO-01-05  
> **Audience:** Entry-level SOC learners

## Learning outcomes

Learners will be able to:
1. Triage a mixed set of synthetic alerts using a consistent method.
2. Test competing hypotheses and explain confidence.
3. Prioritize cases and identify escalation triggers.
4. Produce an evidence-referenced case record and handoff.

## 1. Workshop overview

Learners act as an entry-level SOC team receiving a small queue of synthetic records. They must decide what is known, what needs checking, what should be escalated, and what can be closed with a documented reason.

No live systems are targeted. The evidence pack is fabricated for teaching. It must never be presented as a real incident or a validated detection result.

## 2. Scenario context

A fictional organization, Northwind Parts, has a small mixed environment:
- Employee workstations.
- A customer-facing web service.
- Standard and privileged user accounts.
- An IT maintenance window.

The SOC queue receives several unrelated-looking alerts during the same morning. Learners must avoid assuming that all alerts are connected.

## 3. Synthetic alert bundle

All names, identifiers, addresses, and timestamps below are invented. Timezone: UTC.

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

The bundle intentionally includes alerts, contextual records, and benign/suspicious possibilities. It does not contain enough information to prove every cause.

## 4. Suggested investigation pivots

- A-01: Is there a successful sign-in? Is the source known? Is the account privileged? What else would validate the activity?
- A-02/A-06: Does the task creation match the approved change? Is the task name, creator, and time consistent? What evidence is missing?
- A-03: What URI, user-agent, response pattern, and application context would be needed? Does a 404 pattern alone prove exploitation?
- A-04: Was the block expected under the lab policy? Is there any evidence the connection succeeded? A denied attempt is not proof of compromise.
- A-05: Was the file intentionally used as a safe test artifact? What does quarantine prove and what does it not prove?

## 5. Workshop procedure

### Phase 1 — Individual review (15 minutes)
Each learner:
1. Reads all records.
2. Labels each as alert, event, context, or other evidence.
3. Writes at least three facts, two hypotheses, and three unknowns.
4. Selects one record requiring immediate follow-up and explains why.

### Phase 2 — Team triage (25 minutes)
As a team:
1. Group related records only where evidence supports a relationship.
2. Identify possible benign explanations and suspicious alternatives.
3. Decide the next evidence source or owner to consult.
4. Record a provisional disposition for each alert.
5. Mark any case requiring escalation.

### Phase 3 — Prioritization and handoff (15 minutes)
The team:
1. Orders cases by priority.
2. Explains impact, urgency, and confidence separately.
3. Identifies the escalation trigger and responsible role.
4. Writes a concise handoff for the highest-priority case.

### Phase 4 — Individual case record (13 minutes)
Each learner writes their own case note with source references, timestamps, facts, hypotheses, unknowns, current assessment, and next action.

### Phase 5 — Debrief (22 minutes)
The instructor reveals the intended reasoning boundaries, compares alternative defensible decisions, and asks learners what additional evidence would change their conclusion.

## 6. Required student submission

- Alert classification table.
- Individual triage record for at least two alerts.
- Team queue priority with rationale.
- One escalation/handoff message.
- Individual reflection: one uncertainty and one next investigative action.

## 7. Expected reasoning boundaries

- A-01 warrants validation because failures are followed by success; compromise is not established without source and sign-in context.
- A-02 may be expected because of A-06, but the change record alone does not prove every detail of the task was authorized.
- A-03 requires application and request context; repeated 404 responses alone do not prove exploitation.
- A-04 is a denied attempt; do not claim the destination was reached.
- A-05 is consistent with a known training artifact, but learners should confirm that the host and exercise context match.
- A-07 and A-08 are contextual records, not proof that the associated activity is safe.

The instructor may accept different priority orders when the learner identifies the assumptions and explains the risk trade-offs.

## 8. Safety, cleanup, and reset

- Use only this synthetic evidence pack.
- Do not generate real authentication attempts, scan external systems, execute malware, or alter live infrastructure.
- No VM or network changes are required.
- Reset by distributing a clean copy of the evidence pack and blank worksheets.
- If an instructor substitutes another dataset, label its provenance and remove real personal data.

## 9. Validation status

- Evidence type: synthetic, authored for training.
- Runtime execution: not applicable; no live telemetry was generated.
- Classroom pilot: not performed.
- Technical validation: content review only; no production system behavior is asserted.
- Independent Quality Reviewer: pending.
