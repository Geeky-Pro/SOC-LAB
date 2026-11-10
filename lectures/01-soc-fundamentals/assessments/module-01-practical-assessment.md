# Module 01 — Practical Assessment: Alert Triage and Shift Handoff

> **Status:** draft — assessment brief and criteria for review  
> **Module:** 01-soc-fundamentals  
> **Assessment ID:** ASMT-01-A  
> **Type:** individual + team practical tabletop  
> **Suggested duration:** 60 minutes within L01-06  
> **Version:** 0.1

## 1. Purpose and outcomes

This assessment measures whether learners can interpret synthetic security records, conduct a defensible initial triage, prioritize a small queue, escalate appropriately, and communicate evidence and uncertainty.

| Outcome ID | Outcome | Evidence expected |
|---|---|---|
| LO-01-02 | Differentiate events, alerts, cases, incidents, indicators, and findings. | Record classification with explanation |
| LO-01-03 | Apply a repeatable triage workflow using scope, confidence, impact, and urgency. | Individual triage record |
| LO-01-04 | Prioritize and route a case with a defensible rationale and escalation trigger. | Team queue order and escalation decision |
| LO-01-05 | Document observations, hypotheses, decisions, and uncertainty in an analyst handoff. | Individual case note and handoff |

## 2. Candidate instructions

You are part of an entry-level SOC team reviewing a synthetic alert bundle for a fictional organization.

You must:
- Use only the supplied synthetic records and case cards.
- Identify what is known, what is hypothesized, and what remains unknown.
- Avoid claiming an incident unless the supplied evidence and stated criteria support it.
- State confidence, impact, and urgency separately.
- Recommend actions within your authority and identify when escalation is required.
- Label all evidence as synthetic training material.

Do not use real accounts, systems, networks, or external services. Do not attempt to recreate the events.

## 3. Assessment scope and environment

- **Dataset:** Module 01 Student Guide, synthetic alert bundle A-01 to A-08 and queue cards Q-01 to Q-04.
- **Environment:** paper/digital tabletop only; no deployed lab required.
- **Permitted resources:** module notes, student guide, and blank worksheets.
- **Not permitted:** external scanning, real account access, or live response actions.
- **Submission:** individual triage record and handoff; team queue priority and escalation rationale.
- **Time:** suggested 60 minutes; instructor may adapt for approved accommodations.

## 4. Tasks

### Task 1 — Record classification

Classify at least four records as event, alert, context, indicator, case, incident, or finding where applicable. Explain one distinction that could prevent a premature incident declaration.

**Expected submission:** classification table with brief reasoning.

### Task 2 — Individual triage

Select at least two alerts. For each:
- Record three evidence-backed facts with source/time references.
- Record two hypotheses and at least two unknowns.
- Assess confidence, impact, and urgency separately.
- Recommend a specific next action and escalation trigger.

**Expected submission:** two completed triage records.

### Task 3 — Queue prioritization

As a team, prioritize Q-01 to Q-04. Explain the assumptions and trade-offs. Identify the case requiring the earliest escalation and name the receiving role.

**Expected submission:** ordered queue and escalation rationale.

### Task 4 — Individual handoff

Write a handoff for one case that another analyst can continue without asking you to reconstruct the investigation.

**Expected submission:** case ID/status, summary, scope, facts, assessment, confidence, impact/urgency, completed actions, unknowns, next action, owner, and escalation trigger.

### Task 5 — Reflection

State one uncertainty that remains and one piece of evidence that could change your conclusion.

**Expected submission:** short individual reflection.

## 5. Assessment criteria

Use the common SOC-LAB rubric in [Assessment Rubric](../../../curriculum/assessment-rubric.md). Score only criteria relevant to this module.

| Criterion | Evidence of competent performance |
|---|---|
| Scope and safety | Uses only supplied synthetic records and does not recommend unauthorized actions |
| Evidence provenance | References record IDs and timestamps for material facts |
| Technical interpretation | Correctly distinguishes observed events, alerts, context, and conclusions |
| Hypothesis testing | Considers alternatives and records missing information |
| Prioritization and response reasoning | Separates impact, urgency, and confidence; identifies proportionate escalation |
| Communication and records | Produces a clear, actionable handoff with facts, assessment, unknowns, and next steps |
| Validation and limitations | Does not claim live execution, confirmed compromise, or detection validation without evidence |

## 6. Completion criteria

A complete submission must include:
- [ ] Classification table.
- [ ] Two individual triage records.
- [ ] Team queue priority and escalation rationale.
- [ ] Individual handoff.
- [ ] Individual reflection.

A missing mandatory evidence item should be returned for completion or handled under the instructor's approved remediation process. No numeric pass threshold is set in this draft.

## 7. Instructor scoring notes

- Accept alternative priority orders when the learner makes assumptions explicit and explains impact, urgency, confidence, and escalation.
- Do not award full credit for a correct label unsupported by reasoning.
- Penalize unsupported claims such as “account compromised” or “web server exploited” when evidence is insufficient.
- Require individual artifacts in addition to team output.
- Give feedback on evidence quality and analytical reasoning, not only the final disposition.

The detailed expected reasoning belongs in the instructor guide and must not be copied into the student-facing assessment brief.

## 8. Validation and fairness review

- Outcome alignment: mapped to LO-01-02 through LO-01-05.
- Clarity: synthetic data, scope, tasks, and evidence are stated.
- Time/load: proposed 60 minutes; classroom timing not tested.
- Accessibility: adapt format/time for approved accommodations.
- Technical validation: no live platform or telemetry used.
- Independent review: pending.
- Project Owner decisions: weighting, pass threshold, grade boundaries, remediation/retake policy, and final assessment conditions.

## 9. References

- NIST SP 800-61 Rev. 3 — https://csrc.nist.gov/pubs/sp/800/61/r3/final
- NIST CSF 2.0 — https://www.nist.gov/cyberframework
