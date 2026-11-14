# Module 08 — Lesson Sequence and Teaching Plan

> **Status:** draft — proposed delivery plan; pending Project Owner approval  
> **Version:** 0.2  
> **Estimated contact time:** 8 hours (480 minutes)  
> **Curriculum baseline:** 0.3  
> **Validation:** NOT VALIDATED

[Arabic version](lesson-plan-ar.md)

## Delivery sequence

| Lesson | Topic | Duration | Outcomes | Learner output |
|---|---|---:|---|---|
| L08-01 | Foundations, terminology, and authority | 60 min | LO-08-01 | Classification check and authority map |
| L08-02 | Intake, triage, and severity | 75 min | LO-08-01, LO-08-02, LO-08-03 | Triage note and provisional priority |
| L08-03 | Investigation scope, evidence, and timeline | 75 min | LO-08-02, LO-08-04 | Evidence matrix and timeline |
| L08-04 | Containment, eradication, recovery, and verification | 90 min | LO-08-05 | Response decision matrix |
| L08-05 | Escalation, communications, closure, and improvement | 60 min | LO-08-06 | Situation report and incident record |
| L08-06 | Suspicious Web Server Activity tabletop and debrief | 120 min | LO-08-01–LO-08-06 | Team tabletop submission and individual after-action reflection |
| **Total** | | **480 min / 8 hours** | | |

Timing is provisional and aligned to the Module 08 detailed curriculum v0.3. Confirm against the approved course schedule. The tabletop debrief is included within L08-06; it is not an additional 30-minute block.

## Lesson details

### L08-01 — Foundations and authority (60 min)
- 0–10: Opening case — an alert is not automatically a confirmed incident.
- 10–25: Events, alerts, investigations, suspected incidents, confirmed incidents, benign activity.
- 25–40: NIST CSF 2.0 and SP 800-61 Rev. 3 conceptual model.
- 40–50: Classroom roles and decision authority.
- 50–60: Knowledge check.
- **Exit evidence:** classify five examples and identify who may authorize a disruptive action.

### L08-02 — Intake, triage, and severity (75 min)
- 0–10: Recap and initial report.
- 10–25: Intake fields; facts versus hypotheses.
- 25–40: Scope, impact, exposure, urgency, confidence, alternatives.
- 40–55: Apply the proposed P1–P4 educational model.
- 55–70: Individual triage note.
- 70–75: Peer review.
- **Exit evidence:** triage note with rationale, unknowns, owner, and next checkpoint.

### L08-03 — Evidence and timeline (75 min)
- 0–10: Provenance and time zones.
- 10–25: Source reliability, event time, ingestion time, clock skew, gaps.
- 25–45: Correlate supplied synthetic web, firewall, and endpoint evidence.
- 45–60: Build evidence matrix and timeline.
- 60–75: Explain confidence and alternative hypotheses.
- **Exit evidence:** source-referenced timeline with explicit uncertainty.

### L08-04 — Response decisions (90 min)
- 0–15: Containment objectives and trade-offs.
- 15–30: Compare restriction, isolation, service degradation, and monitoring conceptually.
- 30–50: Eradication/remediation versus containment.
- 50–70: Recovery verification and rollback.
- 70–90: Decision matrix, approval gate, and verification criteria.
- **Exit evidence:** two options compared with impact, authority, rollback, and verification.

### L08-05 — Communications and closure (60 min)
- 0–10: Incident lead, technical owner, recorder, decision authority.
- 10–25: Situation reports and escalation triggers.
- 25–40: Incident record and decision/action log.
- 40–50: Closure, monitoring, lessons learned.
- 50–60: Status update exercise.
- **Exit evidence:** situation report, incident record, and two improvement actions.

### L08-06 — Tabletop and debrief (120 min)
- 0–10: Scope, roles, rules, starting report.
- 10–25: Inject 1 — initial web-server anomaly.
- 25–45: Inject 2 — corroborating network/IDS context.
- 45–65: Inject 3 — scope and uncertainty challenge.
- 65–85: Inject 4 — containment decision and business impact.
- 85–100: Inject 5 — recovery and monitoring decision.
- 100–112: Situation report and incident record.
- 112–120: Initial debrief, unresolved questions, and individual reflection prompt.
- **Exit evidence:** team incident record and response decision log, plus individual after-action reflection.

## Instructor preparation

1. Review shared procedures in `incident-response/`.
2. Confirm lab state and which telemetry sources are actually verified.
3. If using Splunk, verify indexes, sourcetypes, fields, time ranges, and data quality from observed events. Do not publish unverified SPL as guaranteed.
4. Prepare synthetic evidence if live telemetry is unavailable; label it clearly.
5. Confirm group roles, inject release method, and answer-key separation.
6. Keep disruptive actions discussion-only unless explicitly authorized and reversible.
7. Confirm snapshot/reset procedures before any state change.

## Required learner artifacts

Knowledge check; triage note; timeline/evidence matrix; response decision log; situation report; incident record; after-action review.

## Adaptation

If telemetry is incomplete, use the synthetic evidence pack. Do not imply that synthetic artifacts came from a live lab. If time is constrained, shorten discussion rather than removing authority and evidence-integrity exercises.

## References

- NIST SP 800-61 Rev. 3: https://doi.org/10.6028/NIST.SP.800-61r3
- NIST CSF 2.0: https://doi.org/10.6028/NIST.CSWP.29
