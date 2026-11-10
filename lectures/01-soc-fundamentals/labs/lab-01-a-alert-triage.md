# LAB-01-A — Synthetic Alert Classification and Triage

> **Status:** draft — authored, not classroom-tested  
> **Module:** 01-soc-fundamentals  
> **Lab ID:** LAB-01-A  
> **Difficulty:** introductory  
> **Estimated duration:** 45–60 minutes  
> **Environment:** synthetic records only; no deployed SOC lab required

## 1. Purpose and outcomes

Practice classifying records and creating a defensible first-pass triage record.

Learners will be able to:
- Distinguish alert records from events and context.
- Identify facts, hypotheses, and unknowns.
- Assess confidence, potential impact, and urgency separately.
- Recommend a next step and escalation trigger.

## 2. Authorization and safety scope

- **Authorized environment:** the synthetic evidence bundle included in the Module 01 Student Guide.
- **In-scope assets:** fictional identities and assets in the evidence pack only.
- **Out-of-scope targets:** all real systems, public addresses, personal accounts, and third-party services.
- **Expected impact:** none; no live systems are accessed or modified.
- **Safety precautions:** do not attempt to recreate the events.
- **Cleanup/rollback:** no system changes; discard working copies if required by the instructor.

## 3. Prerequisites

- Read L01-02 and L01-03.
- Understand the terms event, alert, indicator, case, incident, fact, hypothesis, and unknown.
- Have the Module 01 Student Guide available.

## 4. Required resources

- Synthetic alert bundle in the Student Guide.
- Triage worksheet.
- Pen or note-taking application.

## 5. Procedure

### Step 1 — Identify the record type

Review A-01 through A-08. For each, record whether it is primarily an alert, event observation, or contextual record. Explain where a record contains more than one element.

**Expected result:** a classification table that does not label every row as an incident.

### Step 2 — Establish scope and time

Record the fictional organization, assets, accounts, time window, and timezone. State that the evidence is synthetic and that no live source was queried.

**Expected result:** a clear scope statement and UTC time window.

### Step 3 — Extract facts

Write at least three facts supported directly by the records. Include the record ID and time for each.

**Expected result:** statements that can be traced to the supplied evidence.

### Step 4 — Build hypotheses

Write at least two possible explanations for A-01 and one plausible alternative explanation. Identify at least three unknowns.

**Expected result:** hypotheses are not presented as confirmed findings.

### Step 5 — Assess confidence, impact, and urgency

For A-01, select low, medium, or high for each dimension and explain why. Do not combine them into one score.

**Expected result:** three separate assessments with a reason for each.

### Step 6 — Recommend the next action

Name a specific next check, the role responsible, and the condition that would trigger escalation.

**Expected result:** an actionable recommendation within the analyst's authority.

## 6. Student tasks and questions

1. What does the successful sign-in after the failures establish?
2. What does it not establish?
3. Which benign explanations remain possible?
4. What information would most increase or decrease confidence?
5. Why should the case not be closed as benign based only on the current records?

## 7. Evidence to submit

| Evidence | Source | Expected attributes |
|---|---|---|
| Record classification | Student worksheet | Correctly distinguishes alerts, events, and context |
| Fact list | Student worksheet | At least three traceable facts |
| Hypothesis/unknown table | Student worksheet | At least two hypotheses and three unknowns |
| Triage assessment | Student worksheet | Separate confidence, impact, urgency, and rationale |
| Next-action statement | Student worksheet | Specific action, owner, and escalation trigger |

## 8. Expected outcome

A complete triage record that:
- Does not claim compromise without evidence.
- Preserves alternative explanations.
- Identifies missing context.
- Recommends proportionate next steps.
- Distinguishes synthetic data from real evidence.

## 9. Troubleshooting

| Problem | Guidance |
|---|---|
| Learner labels all rows as alerts | Revisit the difference between an event record, an alert, and context. |
| Learner claims account compromise | Ask which supplied fact proves unauthorized access and which alternatives remain. |
| Learner cannot assess urgency | Ask whether activity may be ongoing and what impact is possible. |
| Learner uses confidence as impact | Revisit the separate definitions and require one sentence for each. |

## 10. Cleanup and reset

No systems are changed. Reset by providing a fresh copy of the synthetic evidence bundle and a blank worksheet.

## 11. Instructor facilitation

Use a think-aloud to model how to distinguish facts from hypotheses. Ask learners to identify what additional evidence would support or weaken each hypothesis. Detailed answer keys are intentionally excluded from this public-facing lab file; keep them in an access-controlled instructor distribution.

## 12. Validation record

- **Documented:** yes.
- **Statically checked:** outcome, scope, steps, evidence, safety, and cleanup sections are present.
- **Executed:** not executed; synthetic tabletop activity only.
- **Tested against criteria:** not classroom-tested.
- **Independently validated:** pending.
- **Known limitations:** no live telemetry or operational platform is used.
