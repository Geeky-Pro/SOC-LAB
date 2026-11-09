# Detailed Curriculum — Module 11: SOC Capstone Project

> **Status:** draft — pending independent review and Project Owner approval  
> **Module ID:** 11-soc-capstone  
> **Curriculum version:** 0.3  
> **Proposed contact time:** 12 hours

## 1. Module purpose

SOC Capstone Project develops the capability to perform the domain-specific work expected of a SOC analyst. Instruction is capability-led; tools are used as supporting instruments, not as learning outcomes.

## 2. Prerequisites

Successful completion of Modules 01–10 or documented instructor-approved equivalency.

## 3. Measurable learning outcomes

By the end of this module, learners should be able to:

| ID | Learning outcome | Lesson alignment | Evidence |
|---|---|---|---|
| LO-11-01 | Independently scope an assigned SOC case and develop a defensible investigation plan. | L11-01, L11-02 | Investigation plan and scope statement, including permitted sources, boundaries, and initial hypotheses. |
| LO-11-02 | Collect, preserve, interpret, and correlate evidence from the sources made available. | L11-02 | Individual evidence matrix and journal with source identifiers, timestamps, provenance, and interpretation. |
| LO-11-03 | Prioritize the case and test competing hypotheses with explicit uncertainty. | L11-02 | Hypothesis register showing supporting/contradicting evidence, alternatives, confidence, and priority rationale. |
| LO-11-04 | Evaluate relevant telemetry and detection behavior without overstating coverage. | L11-03 | Detection/telemetry assessment separating source visibility, parsing, search/detection behavior, and unvalidated gaps. |
| LO-11-05 | Recommend proportionate response and recovery actions with approval and verification criteria. | L11-03, L11-04 | Response/recovery decision log with authority, impact, rollback, verification, and residual risk. |
| LO-11-06 | Deliver a complete incident package and concise technical/stakeholder briefing. | L11-04, L11-05 | Complete incident package, oral briefing, Q&A response, and individual reflection. |

## 4. Detailed lesson sequence

### L11-01 — Capstone briefing, rules, and scenario assignment

- **Duration:** 60 minutes
- **Core content:** Assessment scope; permitted tools; evidence handling; submission requirements; fairness.
- **Learning activity:** Confirm scope and submit investigation plan.
- **Evidence:** Completed confirm scope and submit investigation plan artifact with source/time references, the learner's reasoning, and at least one stated limitation or uncertainty.

### L11-02 — Independent investigation work period

- **Duration:** 240 minutes
- **Core content:** Student-led triage, collection, analysis, correlation, and hypothesis testing.
- **Learning activity:** Maintain investigation journal and evidence matrix.
- **Evidence:** Completed maintain investigation journal and evidence matrix artifact with source/time references, the learner's reasoning, and at least one stated limitation or uncertainty.

### L11-03 — Response planning and detection assessment

- **Duration:** 120 minutes
- **Core content:** Severity; decision options; detection gaps; remediation and recovery verification.
- **Learning activity:** Submit response plan and detection assessment.
- **Evidence:** Completed submit response plan and detection assessment artifact with source/time references, the learner's reasoning, and at least one stated limitation or uncertainty.

### L11-04 — Final report and technical briefing

- **Duration:** 120 minutes
- **Core content:** Executive summary; timeline; evidence; limitations; recommendations; Q&A.
- **Learning activity:** Submit case package and deliver briefing.
- **Evidence:** Completed submit case package and deliver briefing artifact with source/time references, the learner's reasoning, and at least one stated limitation or uncertainty.

### L11-05 — Review, reflection, and remediation

- **Duration:** 180 minutes
- **Core content:** Rubric feedback; self-assessment; remediation planning; portfolio evidence.
- **Learning activity:** Complete individual reflection and improvement plan.
- **Evidence:** Completed complete individual reflection and improvement plan artifact with source/time references, the learner's reasoning, and at least one stated limitation or uncertainty.

## 5. Practical learning activities

The capstone is an independently assessed case, not a guided demonstration. The instructor assigns a case variant and provides a source-availability manifest, permitted-resource list, rules of engagement, submission brief, and common rubric.

| Activity ID | Learner task | Required input / environment | Expected output | Safety, cleanup, and recovery |
|---|---|---|---|---|
| CAP-11-A | Complete an independently assigned case from scope through briefing. | Instructor-approved scenario pack, source manifest, published brief and rubric; isolated lab or sanitized evidence pack. | Individual journal, evidence matrix, timeline, report, response plan, detection assessment, oral briefing. | Authorized assets/datasets only; clarify individual/team boundaries; no disruptive actions without approval; preserve provenance. |

Before delivery, the instructor must verify that each case variant provides a fair opportunity to demonstrate all assessed outcomes. If a source is unavailable, supply a labeled alternative artifact and adjust the assessed outcome only through an approved accommodation.
## 6. Assessment plan

**Primary assessment evidence:** CAP-11-A — complete individual case package, scored with the [common SOC-LAB assessment rubric](../../curriculum/assessment-rubric.md).

| Learning outcome | Lesson(s) introducing/practicing/assessing | Observable assessment evidence |
|---|---|---|
| LO-11-01 | L11-01, L11-02 | Investigation plan and scope statement, including permitted sources, boundaries, and initial hypotheses. |
| LO-11-02 | L11-02 | Individual evidence matrix and journal with source identifiers, timestamps, provenance, and interpretation. |
| LO-11-03 | L11-02 | Hypothesis register showing supporting/contradicting evidence, alternatives, confidence, and priority rationale. |
| LO-11-04 | L11-03 | Detection/telemetry assessment separating source visibility, parsing, search/detection behavior, and unvalidated gaps. |
| LO-11-05 | L11-03, L11-04 | Response/recovery decision log with authority, impact, rollback, verification, and residual risk. |
| LO-11-06 | L11-04, L11-05 | Complete incident package, oral briefing, Q&A response, and individual reflection. |

Assessment conditions:
- Individual competence must be evidenced separately even if learners discuss approaches in teams.
- Publish the case brief, source manifest, allowed tools/references, time limits, submission format, and rubric before assessment.
- Score only criteria relevant to the case's available evidence. If a source is absent, do not penalize the learner for unavailable telemetry; record the limitation.
- Project Owner decisions on weighting, pass threshold, retake/remediation, and accommodations remain pending.
- Keep instructor case keys and expected evidence separate from student materials.
## 7. Lab and resource dependencies

Refer to [Lab Dependency Map](../../curriculum/lab-dependency-map.md) and the shared [Lab Environment](../../lab-environment/README.md). Exact indexes, sourcetypes, fields, ports, versions, export methods, and collection paths must be verified against the deployed lab before being taught as facts.

## 8. Safety and operational boundaries

- Use only authorized, isolated lab assets and approved datasets.
- No public targets, real-user accounts, uncontrolled malware, or unauthorized data collection.
- Disruptive actions require explicit instructor authorization, impact assessment, rollback, and verification.
- Preserve evidence provenance and label synthetic, simulated, captured, and inferred data distinctly.

## 9. Estimated workload

The proposed 12-hour allocation is a planning estimate. It must be checked against the actual lesson materials, learner skill level, lab setup time, and classroom pilot. Breaks and independent study are excluded.

## 10. Quality and validation gates

- [ ] Outcomes are observable and assessable.
- [ ] Every lesson maps to outcomes and evidence.
- [ ] Activities and assessment instructions are complete and accessible.
- [ ] Technical references and versions are checked.
- [ ] Lab dependencies and telemetry are verified or clearly marked unavailable.
- [ ] Safety, cleanup, and reset instructions are present for every hands-on activity.
- [ ] Instructor and student materials are separated.
- [ ] Independent Quality Reviewer review completed.
- [ ] Project Owner approval recorded.

**Current validation state:** NOT VALIDATED. No classroom pilot or end-to-end practical execution is claimed.

## 11. References

Use the [Module Reference Catalog](../../curriculum/references/module-reference-catalog.md), plus references specific to the evidence domains included in the assigned capstone case. The instructor must attach the actual source list to each case pack.

## 12. Change history

| Version | Change | Status |
|---|---|---|
| 0.3 | Revised outcome mapping, evidence expectations, activity blueprint, and lesson evidence following independent review | Draft |
| 0.2 | Initial detailed curriculum design for this module | Draft |
