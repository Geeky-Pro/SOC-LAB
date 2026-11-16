# Instructor Guide — Module 08: Incident Response

[النسخة العربية](./instructor-guide-ar.md)

> **Status:** draft — instructor-facing, public-safe; protected answer keys are excluded  
> **Version:** 0.2
> **Estimated contact time:** 8 hours (480 minutes; tabletop debrief included)  
> **Validation:** NOT VALIDATED

## 1. Teaching purpose

Develop disciplined response judgment. Learners validate signals, scope what is known, state uncertainty, prioritize proportionately, respect authority, communicate decisions, and define recovery verification. Grade reasoning and evidence, not memorization of a fixed lifecycle or one predetermined severity.

## 2. Delivery plan

| Segment | Duration | Instructor action | Learner activity |
|---|---:|---|---|
| Foundations and terminology | 60 min | Facilitate classification examples | Classify events, alerts, incidents |
| Triage and severity | 75 min | Model a triage note | Assign provisional category/priority |
| Evidence and timeline | 75 min | Provide labeled evidence cards | Build sourced timeline |
| Response decisions | 90 min | Introduce operational trade-offs | Compare options and approval gates |
| Communications and closure | 60 min | Review situation report | Produce incident record |
| Tabletop and debrief | 120 min | Release staged injects and facilitate debrief | Collaborate, document decisions, and identify improvements |

## 3. Preparation checklist

- [ ] Review shared procedures in incident-response/.
- [ ] Confirm prerequisites and learner readiness.
- [ ] Distribute only the student brief, not this guide or the tabletop master.
- [ ] Decide synthetic-only or hybrid verified/sanitized evidence.
- [ ] Label every synthetic artifact and record captured-artifact origin.
- [ ] Verify actual Splunk indexes, sourcetypes, fields, time ranges, and source coverage before tool-specific instructions.
- [ ] Confirm instructor decision authority and escalation route.
- [ ] Keep disruptive actions discussion-only unless explicitly authorized.
- [ ] If live action is planned, verify snapshot, rollback, and reset.
- [ ] Prepare timer, group roles, incident record, and scoring sheets.

## 4. Facilitation principles

- Ask learners to separate facts, hypotheses, and unknowns.
- Ask what evidence would change their mind when confidence is overstated.
- Reward explicit alternative explanations.
- Release injects only after teams record their current assessment.
- Allow severity to change; require timestamp and rationale.
- Do not reward unnecessary shutdown without business-impact analysis.
- Students must not contact external parties or make legal/privacy determinations.

## 5. Inject guidance

| Inject | Teaching emphasis | Facilitator prompt | Common weak response |
|---|---|---|---|
| I-01 | Intake and uncertainty | What do we know directly? | Calling it confirmed compromise |
| I-02 | Web evidence limitations | What else can cause this pattern? | Treating HTTP 500 as proof of execution |
| I-03 | Corroboration | What does a generic IDS alert prove? | Calling it C2/exfiltration without evidence |
| I-04 | Alternative hypothesis | How can maintenance be verified? | Ignoring or blindly accepting the claim |
| I-05 | Authority and proportionality | Who approves the outage and rollback? | Isolating without authority |
| I-06 | Recovery verification | What makes restoration trustworthy? | Closing immediately after service returns |

## 6. Public-repository boundary

This repository is public. This guide is a public-safe instructor-facing document and does not contain a protected answer key or private scoring solution. Any unreleased facilitator notes, detailed expected answers, or protected assessment solutions must be stored in an access-controlled instructor repository or private distribution. A folder name does not provide access control.

## 7. Common misconceptions

| Misconception | Identification | Remediation |
|---|---|---|
| Every alert is an incident | I-01 labeled confirmed | Revisit definitions and confirmation criteria |
| IDS label proves compromise | Generic alert treated as proof | Separate alert classification from validated impact |
| HTTP 500 proves exploitation | Execution inferred from error | Request application/process evidence and alternatives |
| Severity never changes | Initial rating retained despite new evidence | Require reassessment log |
| Analyst can isolate any host | Unapproved shutdown proposed | Apply authority matrix and impact analysis |
| Recovery means service is online | Closed after restart | Require trusted baseline, checks, monitoring, owner acceptance |
| Synthetic evidence is live | Synthetic card cited as captured | Require provenance label |

## 8. Assessment guidance

Use the module assessment rubric. Do not treat the proposed point threshold or severity examples as approved policy; obtain Project Owner approval before formal grading. Accept different conclusions where reasoning is defensible. Penalize unsupported certainty, missing provenance, ignored authority, and unsafe actions. Fabricated evidence or claims of unperformed actions require remediation.

## 9. Safety and classroom operations

- Student activity is analytical and discussion-based by default.
- Instructor retains authority over VM isolation, firewall changes, account changes, service restarts, deletion, and restoration.
- Do not expose production credentials or sensitive operational data.
- Stop the exercise if activity leaves the approved lab scope or affects an unrelated network.
- Record unexpected lab behavior and restore only using the approved recovery procedure.

## 10. Debrief

Ask: What did you know at the start? Which evidence changed your view? What uncertainty mattered most? Which response was proportionate? What approval was needed? What must be verified before closure? What two improvements would you prioritize?

## 11. Delivery feedback

After delivery, record actual timing, misconceptions, unclear injects, missing evidence, accessibility issues, and rubric changes. Do not mark the scenario validated until delivery and supporting evidence are recorded.

## 12. References

- NIST SP 800-61 Rev. 3: https://doi.org/10.6028/NIST.SP.800-61r3
- NIST CSF 2.0: https://doi.org/10.6028/NIST.CSWP.29
