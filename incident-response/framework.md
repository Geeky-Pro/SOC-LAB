# Incident Response Framework

> **Status:** draft  
> **Validation:** NOT VALIDATED

## 1. Purpose and scope

This framework gives SOC-LAB learners a consistent way to reason about suspected and confirmed cybersecurity incidents. It covers operational coordination from initial signal through response, recovery, and improvement. It is educational guidance, not a substitute for an organization's approved policy, legal advice, contractual obligations, or regulator-specific reporting requirements.

## 2. Reference model

Use NIST Cybersecurity Framework (CSF) 2.0 and NIST SP 800-61 Rev. 3 as the primary conceptual baseline:

- **Govern, Identify, Protect** support preparation and ongoing risk management.
- **Detect** identifies and analyzes potentially adverse events.
- **Respond** coordinates analysis, containment, mitigation, and communications.
- **Recover** restores affected services and operations.
- **Improvement** is continuous; lessons from all functions inform future capability.

NIST SP 800-61r3 was finalized in April 2025 and supersedes Rev. 2. Do not present the older Rev. 2 lifecycle diagram as the current NIST model.

## 3. Working principles

1. **Safety and authority first:** know who may authorize containment, service interruption, account disablement, evidence access, and external notification.
2. **Evidence before assumptions:** distinguish observed facts, analyst hypotheses, and confirmed conclusions.
3. **Impact-driven prioritization:** consider business/service impact, affected assets and data, exposure, urgency, and confidence.
4. **Proportionate response:** choose the least disruptive action that adequately reduces risk, subject to authorized decision-making.
5. **Preserve context:** record timestamps, time zones, sources, actions, decisions, and responsible persons.
6. **Coordinate deliberately:** use defined incident ownership, escalation paths, and communication channels.
7. **Recover safely:** verify the threat is addressed, restore from trusted state, and monitor for recurrence.
8. **Improve continuously:** capture lessons, control gaps, and follow-up actions.

## 4. Roles and responsibilities

Actual role names vary by organization. For classroom exercises, use these functional responsibilities:

| Role | Responsibility |
|---|---|
| Incident lead | Coordinates the response, maintains priorities, decisions, and status |
| SOC analyst | Validates alerts, gathers authorized evidence, scopes activity, and recommends actions |
| Technical owner | Explains asset/service dependencies and implements approved technical changes |
| Incident decision authority | Approves disruptive containment, business-impact trade-offs, and closure |
| Communications/privacy/legal contacts | Advise on internal/external communications, privacy, contractual, and legal obligations |
| Recorder | Maintains the incident timeline, decisions, action owners, and evidence references |

One person may perform multiple roles in a small exercise, but decision authority must remain explicit.

## 5. Authority boundaries

SOC analysts may recommend actions; they must not assume authority to:
- shut down or isolate production systems;
- disable user or service accounts;
- collect or disclose sensitive data;
- contact customers, media, law enforcement, regulators, or external providers;
- delete artifacts or rebuild systems;
- make legal, privacy, or breach-notification determinations.

In SOC-LAB, the instructor is the decision authority for disruptive lab actions unless the exercise explicitly defines another role.

## 6. Events, alerts, investigations, and incidents

Use terms consistently:
- **Event:** an observable occurrence in a system or network.
- **Alert:** a notification that an event or pattern may require review.
- **Investigation:** an authorized analytical activity to determine what happened.
- **Suspected incident:** credible indications of a security incident that have not yet been confirmed or ruled out.
- **Confirmed incident:** an occurrence meeting the applicable incident definition or organizational threshold.
- **False positive / benign activity:** activity assessed as non-malicious or not an incident, with rationale recorded.

Do not equate every alert, indicator, vulnerability, or policy violation with a confirmed incident.

## 7. Relationship to local policy

Organizations must define their own incident thresholds, severity levels, authorities, retention rules, reporting timelines, and external obligations. SOC-LAB's proposed P1–P4 model is a teaching aid only and must not be treated as a real organization's policy.

## 8. References

- NIST, *SP 800-61 Rev. 3*, April 2025: https://doi.org/10.6028/NIST.SP.800-61r3
- NIST CSF 2.0: https://doi.org/10.6028/NIST.CSWP.29
- NIST Incident Response project: https://csrc.nist.gov/projects/incident-response
