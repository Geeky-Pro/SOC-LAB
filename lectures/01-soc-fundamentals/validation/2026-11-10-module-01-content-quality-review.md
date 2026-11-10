# Quality Review — Module 01 Teaching Package

> **Review status:** PASS WITH NOTES  
> **Review date:** 2026-11-10  
> **Reviewer:** SOC-LAB Quality Reviewer  
> **Artifact/version:** Module 01 initial teaching package v0.2

## 1. Review scope

Reviewed the Module 01 package on branch architecture/v2-foundation:
- Module README and detailed curriculum
- Six lesson content files (L01-01 through L01-06)
- Six-hour lesson plan
- Instructor guide and student guide
- LAB-01-A and LAB-01-B
- Module 01 practical assessment
- Relevant curriculum outcomes, assessment rubric, learner readiness checklist, module architecture, content policy, safety policy, instructional quality standard, and lab quality standard

The review evaluates technical and instructional accuracy within the introductory, tool-neutral scope; safety; package completeness; outcome alignment; evidence expectations; student/instructor separation; references; and repository consistency.

## 2. Review limitations

- The GitHub repository is public. Folder names do not restrict access.
- No classroom pilot or learner usability test has been performed.
- No live SOC platform or lab is required for Module 01; all practical exercises are synthetic tabletop activities.
- Assessment timing and learner workload have not been validated in a classroom.
- The review spot-checked the authoritative NIST references relevant to this module. It did not independently verify every linked page or every claim in all future lesson revisions.
- Project Owner approval, assessment weighting, pass threshold, grade boundaries, and remediation policy remain pending.

## 3. Summary

The initial Module 01 teaching package is coherent and aligned with the existing five measurable learning outcomes. The six-lesson sequence totals exactly 360 minutes. The lesson content progresses from SOC mission and terminology to triage, prioritization, documentation, and an integrated exercise. The practical activities use synthetic evidence and do not require live infrastructure or external targets.

The package is suitable to proceed to Project Owner review as a draft, with the notes below. It is not approved for release or classroom delivery.

## 4. Findings

| ID | Severity | File/section | Evidence | Impact | Required action |
|---|---|---|---|---|---|
| Q-01 | Medium | Repository visibility; instructor/ | Repository visibility is public. The guide correctly warns that folder placement does not provide access control; protected answer keys are excluded from the public files. | Any future instructor key or unreleased solution committed here would be publicly accessible. | Before student distribution, store answer keys, scoring solutions, and protected instructor materials in a private repository or access-controlled distribution. |
| Q-02 | Medium | planning/lesson-plan.md; L01-06; assessments/ | Assessment is suggested for 60 minutes within a 90-minute workshop. The workload has not been tested with the target cohort. | Learners may need more time for two triage records, queue prioritization, handoff, and reflection. | Pilot with representative learners; adjust timing or split formative and summative tasks without changing outcomes unless owner-approved. |
| Q-03 | Low | assessments/module-01-practical-assessment.md; curriculum/assessment-rubric.md | Outcomes and observable evidence are mapped, but weighting, pass threshold, and grade boundaries are intentionally unset. | Instructors cannot apply a uniform numeric grading policy yet. | Project Owner to approve assessment policy before formal grading or certification claims. |
| Q-04 | Low | Lesson references | Lessons link to NIST CSF 2.0, NICE, and NIST SP 800-61 Rev. 3. The catalog is a starting point; exact claim-level page references and access dates are not consistently recorded in the lesson files. | Future revisions may weaken source traceability if claims are expanded without precise citations. | During slide/lesson finalization, add claim-level citations, exact edition/page where relevant, and access dates. |
| Q-05 | Low | Student/instructor package separation | Public lesson files contain learning prompts and debrief boundaries, while detailed answer keys are excluded. The guide explains the access limitation. | The public repository is not a secure instructor/student content delivery system. | Keep protected solutions private and create a sanitized student release bundle when the course is ready. |

## 5. Acceptance criteria checklist

| Criterion | Result | Evidence/notes |
|---|---|---|
| Technical correctness | Pass with notes | Introductory concepts are tool-neutral and avoid asserting that an alert proves an incident. Organization-specific definitions and policies are explicitly acknowledged. |
| Safety and authorization | Pass | LAB-01-A/B use synthetic records only, exclude real systems, state scope, and require no disruptive actions. |
| Reproducibility | Pass for tabletop scope | Exercises define inputs, ordered steps, outputs, troubleshooting, cleanup/reset, and validation status. They are not runtime labs. |
| Instructional quality | Pass with notes | Six progressive lessons map to outcomes and include teaching content, examples, misconceptions, and formative questions. Cohort pilot remains outstanding. |
| Completeness and structure | Pass | Lecture plan, six lessons, instructor guide, student guide, two practical activities, assessment brief, and module navigation are present. |
| References and licensing | Pass with notes | Primary NIST sources are linked; exact claim-level citation work remains for final production. No third-party courseware or copied proprietary assets were added. |
| Privacy and security hygiene | Pass | Synthetic names and identifiers are used; no credentials or real personal data are included. Public visibility limitation is disclosed. |

## 6. Validation evidence

Static checks performed:
- Confirmed six lesson content files exist and each includes learning outcomes.
- Confirmed all five Module 01 outcome IDs appear in the lesson content.
- Parsed the lesson plan durations: 45 + 45 + 60 + 60 + 60 + 90 = 360 minutes.
- Confirmed the module package links to the lesson plan, six lessons, guides, labs, and assessment.
- Inspected LAB-01-A/B for scope, prerequisites, procedure, evidence, cleanup/reset, and validation sections.
- Confirmed the public-facing lab files do not contain detailed expected-answer sections.
- Confirmed the assessment maps to LO-01-02 through LO-01-05 and refers to the common rubric.
- Spot-checked NIST SP 800-61 Rev. 3 as the current revision, published April 2025, superseding Rev. 2; checked NIST CSF 2.0 and the NIST NICE Framework resource pages.

## 7. Not validated

- No classroom delivery, timing observation, learner feedback, or usability test.
- No runtime lab execution; no live telemetry is generated by this module.
- No grading reliability study or inter-rater scoring exercise.
- No protected instructor answer key is stored in this public repository.
- No Project Owner approval or release authorization.

## 8. Revision follow-up

| Finding ID | Author response/change | Re-review result |
|---|---|---|
| Q-01 | Public-safe instructor guide explicitly warns that this repository is public; detailed answer keys are excluded. | Addressed for current public draft; private instructor distribution remains required before delivery. |
| Q-02 | Timing remains explicitly provisional and is identified as requiring a cohort pilot. | Open — requires classroom evidence. |
| Q-03 | Assessment document records owner decisions as pending and avoids invented grade thresholds. | Addressed as a documented governance dependency. |
| Q-04 | Official references are linked; exact claim-level citations are reserved for final lesson/slide production. | Open — low-risk follow-up. |
| Q-05 | Instructor guide and lab files exclude protected answer keys and describe the public visibility boundary. | Addressed for current public draft; private distribution remains required before delivery. |

## 9. Recommended next action

Submit this draft package to the Project Owner for content and scope feedback. Before student release, prepare an access-controlled instructor answer-key pack, confirm assessment policy, and pilot the 90-minute integrated workshop with representative learners.

> PASS WITH NOTES is an independent review recommendation only. It is not Project Owner approval or release authorization.
