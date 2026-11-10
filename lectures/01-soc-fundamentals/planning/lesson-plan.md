# Module 01 — Lecture Plan

> **Status:** draft — content-engineer working draft; not approved for delivery  
> **Module:** 01-soc-fundamentals  
> **Proposed contact time:** 6 hours (360 minutes)  
> **Audience:** Entry-level SOC learners; diagnostic baseline only  
> **Delivery mode:** Instructor-led, discussion, synthetic case exercises  
> **Version:** 0.1

## 1. Purpose

Establish the operating mindset and foundational workflow of a SOC analyst: understand the SOC mission, distinguish security records and conclusions, triage alerts using evidence, prioritize work, communicate/escalate, and maintain clear case records.

This module is deliberately tool-neutral. No Splunk, endpoint agent, or deployed SOC lab is required. All practical work uses synthetic records and case cards.

## 2. Learning outcomes

| Outcome | By the end of the module, learners can… | Primary evidence |
|---|---|---|
| LO-01-01 | Explain SOC purpose, operating models, core functions, and analyst responsibilities. | Role-to-task map; prioritized queue and escalation message |
| LO-01-02 | Differentiate events, alerts, cases, incidents, indicators, and confirmed findings. | Classification worksheet with evidence and limitations |
| LO-01-03 | Apply a repeatable alert-triage workflow using scope, confidence, impact, and urgency. | Individual triage record and case disposition |
| LO-01-04 | Prioritize and route a case with a defensible rationale and escalation trigger. | Prioritized queue and handoff |
| LO-01-05 | Document observations, hypotheses, decisions, and uncertainty in an analyst handoff. | Evidence-referenced case record and handoff |

## 3. Lesson sequence and timing

| Lesson | Topic | Duration | Main method | Primary outcomes |
|---|---|---:|---|---|
| L01-01 | SOC mission, operating models, roles, and service boundaries | 45 min | Mini-lecture, role mapping | LO-01-01 |
| L01-02 | Security events, alerts, incidents, and the monitoring lifecycle | 45 min | Concept teaching, classification exercise | LO-01-02 |
| L01-03 | Alert triage and analytical reasoning | 60 min | Worked example, guided synthetic triage | LO-01-02, LO-01-03 |
| L01-04 | SOC workflow, escalation, and communication | 60 min | Queue simulation, handoff practice | LO-01-01, LO-01-04 |
| L01-05 | Analyst documentation and evidence discipline | 60 min | Case-note workshop | LO-01-05 |
| L01-06 | Integrated triage exercise | 90 min | Team investigation, individual assessment, debrief | LO-01-03, LO-01-04, LO-01-05 |
| **Total** | | **360 min / 6 hours** | | |

Breaks, pre-course diagnostic, and independent study are outside the proposed six contact hours.

## 4. Detailed teaching agenda

### L01-01 — 45 minutes
- 0–5: Opening question: what problem does a SOC solve?
- 5–15: Mission, outcomes, operating models, service boundaries.
- 15–25: SOC roles and responsibilities; tiers are illustrative, not universal.
- 25–35: Map common tasks to roles and authority.
- 35–42: Discuss authorization, escalation, and analyst limits.
- 42–45: Exit check.

### L01-02 — 45 minutes
- 0–8: Telemetry-to-decision pipeline.
- 8–20: Event, alert, indicator, case, incident, finding.
- 20–30: Worked examples and non-examples.
- 30–40: Learner classification exercise.
- 40–45: Misconception check.

### L01-03 — 60 minutes
- 0–10: Triage purpose and workflow.
- 10–25: Validate source, time, scope, and context.
- 25–40: Separate facts, hypotheses, unknowns, and confidence.
- 40–52: Guided triage of a synthetic alert.
- 52–60: Compare dispositions and explain uncertainty.

### L01-04 — 60 minutes
- 0–12: Queue ownership and case lifecycle.
- 12–25: Severity, priority, impact, urgency, confidence.
- 25–38: Escalation triggers and decision authority.
- 38–52: Prioritize a mixed queue.
- 52–60: Write and peer-review a shift handoff.

### L01-05 — 60 minutes
- 0–12: Why case records must be reproducible.
- 12–25: Facts vs assumptions; source and timestamp references.
- 25–38: Evidence provenance, handling, privacy, and uncertainty.
- 38–52: Improve a weak case note.
- 52–60: Documentation checklist and exit ticket.

### L01-06 — 90 minutes
- 0–10: Briefing, scope, roles, and evidence pack.
- 10–25: Individual initial review and classification.
- 25–50: Team triage and hypothesis testing.
- 50–65: Queue prioritization and escalation decision.
- 65–78: Individual case record and handoff.
- 78–90: Debrief, feedback, and self-reflection.

## 5. Teaching methods and materials

- Short concept explanations with plain-language definitions.
- Instructor think-aloud demonstrating how to avoid jumping from an alert to an incident conclusion.
- Synthetic alert bundle and queue cards.
- Blank triage worksheet, case record, and handoff template.
- Knowledge checks after each major concept.
- Instructor-only expected reasoning kept separate from student guide.

## 6. Assessment alignment

| Outcome | Formative check | Summative evidence |
|---|---|---|
| LO-01-01 | Role-to-task classification | Prioritized queue and escalation/handoff rationale |
| LO-01-02 | Event/alert/incident classification | Triage record correctly labels facts, signals, and conclusions |
| LO-01-03 | Guided triage walkthrough | Individual triage rationale and disposition |
| LO-01-04 | Queue-prioritization exercise | Priority order, escalation trigger, and decision rationale |
| LO-01-05 | Case-note critique | Complete, evidence-referenced case record and handoff |

Use the common rubric in [Assessment Rubric](../../../curriculum/assessment-rubric.md). Weighting, pass threshold, and grade boundaries remain Project Owner decisions.

## 7. Preparation checklist

### Instructor
- [ ] Review all six lesson content files and the instructor guide.
- [ ] Prepare the synthetic alert bundle and queue exercise.
- [ ] Print or distribute student worksheets and case-record template.
- [ ] Confirm learners understand the exercise is synthetic and not live incident response.
- [ ] Prepare the debrief and acceptable alternative explanations.

### Students
- [ ] Complete the learner readiness diagnostic or note areas needing support.
- [ ] Bring a way to take notes and complete the worksheet.
- [ ] No VM, Splunk instance, or external account is required.

## 8. Adaptation guidance

- If learners are new to networking or operating systems, pause to explain source, host, account, IP address, timestamp, and process at a high level.
- If time is constrained, preserve the triage and documentation practice; shorten role-model discussion before removing individual evidence production.
- For advanced learners, ask for competing hypotheses and explicit confidence/uncertainty rather than adding tool-specific content.

## 9. Validation and review

- **Curriculum alignment:** mapped to Module 01 outcomes and proposed lesson durations.
- **Static timing check:** 45 + 45 + 60 + 60 + 60 + 90 = 360 minutes.
- **Technical runtime:** not applicable; no live lab required.
- **Classroom pilot:** not performed.
- **Independent review:** pending.
- **Project Owner approval:** pending.
