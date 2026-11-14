# Assessment — Incident Response Tabletop and Case Record

[النسخة العربية](./incident-response-assessment-ar.md)

> **Status:** draft  
> **Assessment ID:** IR-ASSESS-01  
> **Type:** team practical / individual reflection  
> **Duration:** 120 minutes total, including the 20-minute individual reflection  
> **Total:** 100 points

## 1. Purpose and outcome alignment

| Outcome | Evidence |
|---|---|
| LO-08-01 | Classification and incident-threshold rationale |
| LO-08-02 | Triage note; validated hypothesis, scope, facts, unknowns, and confidence |
| LO-08-03 | Category/severity record, priority rationale, and reassessment |
| LO-08-04 | Timeline and evidence matrix with provenance |
| LO-08-05 | Response decision log |
| LO-08-06 | Situation report, incident record, and after-action improvements |

## 2. Candidate instructions

Use only evidence released by the instructor. Submit the artifacts below. Distinguish observations from hypotheses and identify missing information. Do not invent evidence, timestamps, event IDs, fields, or actions. Do not perform disruptive changes; live lab actions require explicit instructor authorization.

## 3. Tasks and points

| Task | Required output | Points |
|---|---|---:|
| 1. Signal validation and triage | Facts, hypotheses, unknowns, scope, owner, checkpoint | 15 |
| 2. Evidence analysis | Source-referenced timeline and evidence matrix | 20 |
| 3. Classification and severity | Category, provisional P1–P4, rationale, confidence, reassessment triggers | 15 |
| 4. Response decision | Two or more options, impact, authority, rollback, verification | 20 |
| 5. Communications and records | Situation report and incident record | 15 |
| 6. Recovery and improvement | Recovery/closure criteria and two measurable improvements | 10 |
| 7. Safety and integrity | Scope, provenance, approval gates | 5 |
| **Total** |  | **100** |

## 4. Scoring rubric

| Criterion | Insufficient | Developing | Proficient | Advanced |
|---|---|---|---|---|
| Triage (15) | Missing facts or unsupported conclusion | Partial fields; gaps unexplained | Complete note; separates facts/hypotheses; owner and next step | Strong alternatives and confidence analysis |
| Evidence/timeline (20) | Unsourced or fabricated | Partial timeline; weak provenance/time handling | Chronological, source-referenced, time-aware; gaps explicit | Careful correlation and conflict/clock analysis |
| Severity (15) | No rationale or category confused with severity | Plausible rating with limited analysis | Defensible rating across impact, scope, urgency, exposure, confidence | Clear reassessment triggers and decision history |
| Response (20) | Unsafe/unauthorized action presented as automatic | Options without trade-offs | Two options with impact, approver, rollback, verification | Proportionate choice and residual-risk communication |
| Communication/record (15) | Incomplete, unclear, untraceable | Main facts present; decisions/owners missing | Clear report and complete incident record | Concise, audience-aware, decision-oriented |
| Recovery/improvement (10) | Closure without verification | Generic checks/actions | Trusted restoration checks, monitoring, closure, two measurable improvements | Risk-prioritized improvements with completion evidence |
| Safety/integrity (5) | Scope violation, fabricated evidence, or unapproved action | Repeated reminders needed | Scope, provenance, approval gates followed | Proactively identifies and mitigates risks |

## 5. Passing criteria — proposed

- Suggested pass mark: 70/100.
- Proficient performance is mandatory for safety and evidence integrity; unsafe behavior or fabricated evidence triggers remediation regardless of total score.
- All core artifacts must be submitted. Missing evidence is a limitation, not permission to assume.
- Project Owner approval is required before the threshold becomes official grading policy.

## 6. Instructor scoring notes

- Do not require one exact severity if multiple ratings are supported by evidence and assumptions.
- A suspected incident or blocked outcome may be correct if evidence is insufficient.
- Award credit for recognizing that an IDS alert or HTTP error does not independently prove compromise.
- Deduct for unsupported claims of data theft, persistence, malware, or attribution.
- Reward authority, rollback, verification, and business-impact analysis.
- Score team artifacts collectively; individual reflection may be scored separately.

## 7. Individual reflection

1. What did your team conclude, and what evidence supports it?
2. What uncertainty most affected your recommendation?
3. Which action required approval, and from whom?
4. What would you verify before closure?
5. What would you improve in your investigation process?

## 8. Validation and fairness

- Outcome alignment: mapped to LO-08-01–LO-08-06.
- Clarity and accessibility review: pending.
- Timing/load: proposed, not piloted.
- Technical validation: not performed.
- Tabletop delivery: not yet conducted.
- Independent Quality Reviewer review: pending.
