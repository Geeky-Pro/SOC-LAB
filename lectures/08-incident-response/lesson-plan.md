# Module 08 — Lesson Sequence and Teaching Plan

> **Status:** draft — proposed delivery plan  
> **Version:** 0.1  
> **Estimated contact time:** 6 hours teaching + 2 hours tabletop + 30-minute debrief (adjustable)  
> **Validation:** NOT VALIDATED

## Delivery sequence

| Lesson | Topic | Duration | Outcomes | Learner output |
|---|---|---:|---|---|
| L08-01 | Foundations, terminology, and authority | 60 min | LO-01, LO-05 | Classification check and authority map |
| L08-02 | Intake, triage, and severity | 75 min | LO-02, LO-04 | Triage note and provisional priority |
| L08-03 | Investigation scope, evidence, and timeline | 75 min | LO-03, LO-07 | Evidence matrix and timeline |
| L08-04 | Containment, eradication, recovery, and verification | 75 min | LO-05 | Response decision matrix |
| L08-05 | Escalation, communications, closure, and improvement | 75 min | LO-06, LO-07, LO-08 | Situation report and incident record |
| L08-06 | Suspicious Web Server Compromise tabletop | 120 min | LO-01–LO-08 | Team tabletop submission |
| Debrief | Reflection and feedback | 30 min | LO-08 | Individual reflection and improvements |

Timing is provisional; confirm against the approved course schedule.

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

### L08-04 — Response decisions (75 min)
- 0–15: Containment objectives and trade-offs.
- 15–30: Compare restriction, isolation, service degradation, and monitoring conceptually.
- 30–45: Eradication/remediation versus containment.
- 45–60: Recovery verification and rollback.
- 60–75: Decision matrix and approval gate.
- **Exit evidence:** two options compared with impact, authority, rollback, and verification.

### L08-05 — Communications and closure (75 min)
- 0–15: Incident lead, technical owner, recorder, decision authority.
- 15–30: Situation reports and escalation triggers.
- 30–45: Incident record and decision/action log.
- 45–60: Closure, monitoring, lessons learned.
- 60–75: Status update exercise.
- **Exit evidence:** situation report, incident record, and two improvement actions.

### L08-06 — Tabletop (120 min)
- 0–10: Scope, roles, rules, starting report.
- 10–25: Inject 1 — initial web-server anomaly.
- 25–45: Inject 2 — corroborating network/IDS context.
- 45–65: Inject 3 — scope and uncertainty challenge.
- 65–85: Inject 4 — containment decision and business impact.
- 85–100: Inject 5 — recovery and monitoring decision.
- 100–115: Situation report and incident record.
- 115–120: Capture unresolved questions; full debrief follows.

## Instructor preparation

1. Review shared procedures in incident-response/.
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
