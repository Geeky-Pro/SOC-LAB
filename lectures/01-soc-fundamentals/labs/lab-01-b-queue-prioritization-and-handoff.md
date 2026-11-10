# LAB-01-B — Queue Prioritization and Shift Handoff

> **Status:** draft — authored, not classroom-tested  
> **Module:** 01-soc-fundamentals  
> **Lab ID:** LAB-01-B  
> **Difficulty:** introductory  
> **Estimated duration:** 45–60 minutes  
> **Environment:** synthetic case cards only

## 1. Purpose and outcomes

Practice prioritizing a small SOC queue and transferring work to the next analyst.

Learners will be able to:
- Compare confidence, impact, and urgency.
- Produce a reasoned priority order.
- Identify escalation triggers and authority boundaries.
- Write a clear, actionable handoff.

## 2. Authorization and safety scope

- **Authorized environment:** fictional case cards Q-01 to Q-04 in the Module 01 Student Guide.
- **In-scope assets:** fictional cases only.
- **Out-of-scope targets:** real accounts, services, and networks.
- **Expected impact:** none; no live systems are accessed or modified.
- **Cleanup/rollback:** no system changes.

## 3. Prerequisites

- Complete LAB-01-A or read L01-03 and L01-04.
- Understand severity, priority, impact, urgency, and confidence.

## 4. Procedure

### Step 1 — Read the queue

Review Q-01 through Q-04 in the Student Guide. Identify the affected identity or service and the context provided.

### Step 2 — Assess each case

For each case, record:
- Known facts.
- Missing information.
- Potential impact.
- Urgency.
- Confidence in the current interpretation.
- Whether escalation is required.

### Step 3 — Prioritize the queue

Order the cases from first to last. Explain the trade-offs. Do not invent a universal mathematical scoring formula.

### Step 4 — Select an escalation

Choose the case that most clearly requires escalation now. Identify the receiving role and the reason for escalation.

### Step 5 — Write the handoff

Use the handoff template in the Student Guide. Include facts, current assessment, unknowns, completed actions, and next action.

### Step 6 — Peer review

A partner checks whether the handoff is understandable without asking the original analyst to explain it.

## 5. Student tasks

1. Produce a priority order for Q-01 to Q-04.
2. Explain why the first case outranks the second.
3. Identify a case that can be handled through routine validation.
4. Identify the escalation trigger for the highest-priority case.
5. Write a handoff that includes one alternative explanation and one explicit unknown.

## 6. Evidence to submit

| Evidence | Expected attributes |
|---|---|
| Queue priority | All four cases ordered with rationale |
| Case assessment | Separate impact, urgency, and confidence |
| Escalation decision | Receiving role, trigger, and requested action |
| Handoff note | Scope, facts, assessment, unknowns, next action |
| Peer-review note | One strength and one improvement |

## 7. Expected outcome

A priority order supported by clear assumptions and evidence. Multiple orders may be acceptable when the learner explains the risk trade-offs and does not ignore a critical escalation trigger.

## 8. Troubleshooting

| Problem | Guidance |
|---|---|
| Learner ranks only by alert wording | Ask them to consider asset criticality, privilege, and corroborating context. |
| Learner treats a known test as a confirmed incident | Ask them to verify that the host and exercise record match. |
| Handoff says “please investigate” | Require a named next action, owner, and question to answer. |
| Learner omits uncertainty | Ask what information is unavailable and how it affects confidence. |

## 9. Cleanup and reset

No systems are changed. Reset by redistributing the four case cards and blank handoff worksheet.

## 10. Instructor guidance

Expected considerations:
- Q-01 deserves rapid validation because a privileged account has an unrecognized successful sign-in context. Escalation to the identity/security lead is appropriate while validating the source.
- Q-03 may also require rapid service-owner engagement because a critical customer-facing service is involved, even though maintenance is approved.
- Q-02 appears lower urgency on the supplied facts but should still be validated.
- Q-04 is likely routine closure after confirming the training context matches; retain the evidence and rationale.

Accept different orderings when assumptions, impact, urgency, and confidence are explicit.

## 11. Validation record

- **Documented:** yes.
- **Statically checked:** outcome alignment, instructions, evidence, safety, and reset sections are present.
- **Executed:** not executed; synthetic tabletop activity only.
- **Tested against criteria:** not classroom-tested.
- **Independently validated:** pending.
- **Known limitations:** no live queue-management platform is used.
