# Instructor Guide — Module 01: SOC Fundamentals & Security Operations

> **Status:** draft — instructor-facing material  
> **Audience:** Instructor only  
> **Related assets:** [Lecture Plan](../planning/lesson-plan.md), [Student Guide](../student/student-guide.md)  
> **Proposed contact time:** 6 hours  
> **Version:** 0.1

## 1. Teaching purpose

Help learners develop a disciplined SOC analyst mindset before introducing tools. The module emphasizes evidence-based triage, uncertainty, proportionate prioritization, authority boundaries, and clear communication.

The most important learning shift is from “an alert tells me what happened” to “an alert gives me a question to investigate.”

## 2. Delivery principles

- Explain the operational reason behind every concept.
- Use plain language before introducing specialist terms.
- Ask learners to state what the evidence proves and what it does not prove.
- Reward transparent uncertainty and good evidence references.
- Do not reward confident but unsupported conclusions.
- Distinguish analyst recommendation from authority to execute a disruptive action.
- Keep student-facing evidence separate from instructor expected reasoning.

## 3. Preparation checklist

- [ ] Read the six lesson content files.
- [ ] Read the student guide and verify that no instructor answer key is included there.
- [ ] Prepare one copy of the synthetic alert bundle per learner/team.
- [ ] Prepare blank triage records, queue sheets, and handoff worksheets.
- [ ] Confirm that all exercise identifiers are clearly synthetic.
- [ ] Set team roles (triage analyst, evidence recorder, queue lead, presenter) and rotate if possible.
- [ ] Prepare the debrief and remediation prompts.
- [ ] Confirm the cohort's language and foundational networking/OS support needs.

No virtual machines, Splunk, or live systems are needed for Module 01.

## 4. Delivery plan

| Lesson | Instructor emphasis | Expected learner activity | Time |
|---|---|---|---:|
| L01-01 | SOC is a capability, not a product; role boundaries | Map tasks and escalation authority | 45 min |
| L01-02 | Signal is not conclusion; terms differ | Classify sample records | 45 min |
| L01-03 | Facts/hypotheses/unknowns; confidence/impact/urgency | Triage synthetic alert | 60 min |
| L01-04 | Priority and severity differ; handoff quality | Prioritize queue and write handoff | 60 min |
| L01-05 | Reproducibility and evidence provenance | Rewrite weak case note | 60 min |
| L01-06 | Independent reasoning and evidence-backed decisions | Integrated team and individual exercise | 90 min |

## 5. Instructor notes by lesson

### L01-01 — SOC mission and roles

**Emphasize**
- SOC functions vary by organization and operating model.
- Tier labels are illustrative and not universal.
- Analysts should understand their authority and service boundaries.

**Discussion prompt:** “If you identify suspicious activity on a critical server, what can you do immediately, and what must be approved?”

**Look for:** distinction between collecting permitted evidence, escalating, recommending, and executing an action.

### L01-02 — Events, alerts, incidents

**Emphasize**
- A real event can trigger a poor alert.
- A correct alert can describe benign authorized behavior.
- An indicator is contextual evidence, not a verdict.
- A case tracks work; an incident is classified under organizational policy.

**Misconception to challenge:** learners calling every suspicious alert an incident.

### L01-03 — Triage and reasoning

**Emphasize**
- Ask “what do we know?” before “what do we think?”
- Require an alternative hypothesis.
- Confidence, impact, and urgency are separate.
- Avoid invented numeric scoring systems unless the organization provides one.

**Facilitation:** model a short think-aloud using the failed-sign-in example. Explicitly say what remains unknown.

### L01-04 — Workflow and escalation

**Emphasize**
- Queue ownership and case documentation serve different purposes.
- Prioritization depends on context, not just alert severity.
- Escalation should state why, what is known, what is unknown, and what is needed.

**Facilitation:** accept multiple defensible priority orders if learners explain assumptions and escalation triggers.

### L01-05 — Documentation

**Emphasize**
- Another analyst must be able to continue the work.
- Record source, timestamp, locator, action, and result.
- A hash can help identify a file but does not prove collection provenance by itself.
- This is operational evidence discipline, not legal-forensics training.

**Remediation:** ask learners to rewrite “user hacked” as an evidence-backed statement.

### L01-06 — Integrated workshop

Use the scenario's intended reasoning boundaries in the student guide and lesson file. Do not reveal the answer guidance before learners submit their individual work.

**Expected reasoning**
- A-01: validate the success and source context; do not claim compromise.
- A-02/A-06: the change record is relevant context but does not verify all task details.
- A-03: 404 volume alone does not establish exploitation.
- A-04: a denied connection is not proof of successful access.
- A-05: known training file context is relevant; verify host and exercise alignment.

## 6. Assessment guidance

Use the common rubric in [curriculum/assessment-rubric.md](../../../curriculum/assessment-rubric.md). Assess only criteria relevant to Module 01:
- Evidence provenance.
- Technical interpretation of the supplied records.
- Hypothesis testing.
- Prioritization and response reasoning.
- Communication and records.
- Scope and safety.

Do not assign official grade weights or pass thresholds until the Project Owner approves them. Team products must be paired with individual triage rationale to establish individual understanding.

## 7. Common misconceptions and remediation

| Misconception | How to identify it | Remediation |
|---|---|---|
| Every alert is an incident | Student labels all queue items “incident” | Revisit event → alert → case → incident distinctions |
| Unusual means malicious | Student ignores change/user context | Ask for benign alternatives and validation evidence |
| Severity equals priority | Student ranks only by alert label | Separate impact, urgency, confidence, and context |
| A successful login proves compromise | Student ignores identity/device context | Ask what validates the source and user |
| A blocked connection proves access | Student treats denied attempt as successful | Revisit firewall action and evidence limits |
| A hash proves chain of custody | Student overstates file-hash value | Explain integrity identifier versus provenance record |
| A SOC analyst can isolate any host | Student proposes disruption without authority | Review role boundaries, approval, impact, and rollback |

## 8. Debrief questions

1. Which alert was easiest to misinterpret, and why?
2. What fact most changed your initial assessment?
3. Which unknown would you investigate first?
4. Which decision required escalation rather than direct action?
5. How did your team separate confidence from impact?
6. What would you put in a handoff so the next analyst does not repeat your work?

## 9. Accessibility and learner support

- Define acronyms at first use.
- Provide a glossary and worked example before independent work.
- Allow learners to annotate printed or digital copies.
- Offer additional time or an equivalent format where approved accommodations require it.
- Use the readiness checklist to plan support, not to shame or exclude learners.

## 10. Validation and revision record

- Content alignment: mapped to Module 01 outcomes and proposed 6-hour duration.
- Synthetic data: authored for training; no real organizational data used.
- Runtime lab execution: not applicable.
- Classroom pilot: not performed.
- Independent review: pending.
- Project Owner approval: pending.

Record instructor observations after the first delivery before changing the approved learning outcomes or assessment policy.
