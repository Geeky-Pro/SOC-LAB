# Quality Re-Review — Detailed Curriculum Revision 0.3

- **Review date:** 2026-11-10
- **Reviewer:** SOC-LAB Quality Reviewer (AI-assisted independent document re-review)
- **Branch:** `architecture/v2-foundation`
- **Scope:** Revised program curriculum, all 11 module detailed curricula, assessment rubric/framework, learner readiness checklist, prerequisite map, competency matrix, lab dependency map, and module reference catalog.
- **Overall status:** **PASS WITH NOTES**
- **Approval status:** Project Owner approval remains pending.
- **Review limitations:** Static document review and public-source spot checks only. No classroom pilot, student usability test, lab deployment, VM validation, telemetry ingestion, Splunk search execution, prevention test, or end-to-end scenario execution was performed.

## Summary

Revision 0.3 materially addresses the seven findings from the initial review. Outcome-to-lesson mapping is now more discriminating and explicitly labels introduction, practice, and assessment (I/P/A). Lesson evidence statements and module assessment tables identify concrete artifacts. A common performance rubric, learner readiness proposal, reference catalog, and curriculum-level activity blueprints have been added.

The integrated Operation Shadow Access design now includes sanitized email evidence without making Mailpit mandatory. Module 06 now includes an explicit prevention-control outcome while avoiding an assumption that inline Suricata IPS is already supported or enabled in the deployed pfSense environment.

The proposed schedule remains **89 contact hours**. Static checks confirmed that all 11 modules' lesson durations still match their stated hours.

## Prior finding disposition

### Q-01 — Learning-outcome alignment is not sufficiently discriminating

- **Disposition:** RESOLVED
- **Evidence:** All 11 module assessment tables now map each LO to a limited set of lessons using I/P/A labels. Lesson-level evidence statements are no longer generic placeholders.
- **Remaining note:** Confirm the proposed I/P/A progression when detailed lecture and lab assets are authored; a curriculum mapping is not proof of actual instruction or assessment delivery.

### Q-02 — Assessment evidence is generic and lacks observable performance criteria

- **Disposition:** RESOLVED WITH OWNER DECISIONS PENDING
- **Evidence:** Added `curriculum/assessment-rubric.md`, revised `curriculum/assessment-framework.md`, and replaced generic evidence labels with concrete artifacts and observable submissions across all modules.
- **Remaining note:** Assessment weights, pass threshold, retake/remediation, accommodations, and evidence retention remain explicit Project Owner decisions. The common rubric remains draft.

### Q-03 — Technical and instructional references are not provided at module level

- **Disposition:** PARTIALLY RESOLVED
- **Evidence:** Added `curriculum/references/module-reference-catalog.md` with module-relevant standards and primary vendor/project documentation. Official-source spot checks were performed for NIST CSF 2.0, NIST SP 800-61 Rev. 3, NIST NICE, Microsoft Sysmon, Splunk Search Tutorial, Wireshark, Suricata, Netgate pfSense package documentation, VMware Workstation installation guidance, OWASP Logging, Mailpit, MITRE ATT&CK, Atomic Red Team, Caldera, and selected IETF RFCs.
- **Important correction:** The catalog now references RFC 9989 and RFC 9990/9991 for DMARC rather than obsolete RFC 7489. RFC 9989 explicitly supersedes RFC 7489 and describes the DMARC protocol; RFC 9991 covers failure reporting.
- **Remaining note:** During lesson production, cite the exact page/edition supporting each claim and pin documentation to the installed software versions. The catalog is a starting point, not a substitute for lesson-level citations or configuration validation. The current Suricata “latest” documentation may track a development release; use the documentation matching the installed stable version.

### Q-04 — Integrated Operation Shadow Access does not explicitly integrate email evidence

- **Disposition:** RESOLVED
- **Evidence:** Module 10 now includes LO-10-07 for sanitized email evidence, adds email to cross-source collection and timeline analysis, and identifies a sanitized `.eml` artifact as the default evidence option. Mailpit remains optional. The prerequisite map, module map, competency matrix, and lab dependency map reflect this integration.

### Q-05 — “Prevention” is underrepresented in Network Intrusion Detection & Prevention

- **Disposition:** RESOLVED WITH SAFETY LIMITATION
- **Evidence:** Module 06 now includes LO-06-07 and a practical activity for prevention-policy evaluation, allowed/denied flow verification, impact assessment, and rollback.
- **Safety limitation:** The curriculum does not assume inline Suricata IPS is enabled or available. The learner exercise may use a reversible isolated pfSense firewall policy or a tabletop simulation. Inline IPS demonstration requires exact-version/package support verification and explicit instructor authorization.

### Q-06 — Learner entry profile and prerequisite proficiency are not operationalized

- **Disposition:** PARTIALLY RESOLVED
- **Evidence:** Added `curriculum/learner-readiness-checklist.md` and revised `curriculum/prerequisite-map.md` with observable baseline skills, diagnostic evidence, readiness states, and remediation suggestions.
- **Remaining note:** The proposed entry profile and whether refresher content is pre-course or included in the 89 contact hours require Project Owner/Instructor confirmation for the actual cohort.

### Q-07 — Practical activities are curriculum summaries, not executable lab specifications

- **Disposition:** PARTIALLY RESOLVED AT CURRICULUM-DESIGN LEVEL
- **Evidence:** All 11 modules now include activity blueprints identifying learner task, required input/environment, expected output, and safety/cleanup/recovery expectations.
- **Remaining note:** These blueprints are not final student lab instructions. Exact commands/steps, tested versions, troubleshooting, instructor preparation, reset procedure, and runtime evidence must be created and validated in the module-specific lab/scenario assets before delivery.

## Acceptance criteria checklist

| Criterion | Result | Notes |
|---|---|---|
| 11-module progression and scope consistency | PASS | Existing module order and core exclusions preserved. |
| Duration arithmetic | PASS | 89 hours; all module lesson totals match. |
| LO-to-lesson traceability | PASS WITH NOTES | Explicit I/P/A mappings across all modules. |
| Concrete lesson and assessment evidence | PASS | Specific artifacts and common rubric added. |
| Rubric and grading governance | PASS WITH NOTES | Rubric exists; weights and pass threshold remain owner decisions. |
| Module reference starting points | PASS WITH NOTES | Catalog added; exact lesson citations and installed-version pinning remain production tasks. |
| Email integration in Module 10 | PASS | Sanitized .eml path; Mailpit optional. |
| Detection/prevention distinction in Module 06 | PASS WITH NOTES | Safe policy evaluation; inline IPS remains conditional. |
| Learner entry profile and progression gates | PASS WITH NOTES | Proposed profile awaits cohort confirmation. |
| Practical activity design | PASS WITH NOTES | Blueprints exist; final lab specifications and execution validation remain outstanding. |
| Technical lab execution and classroom pilot | NOT VALIDATED | Not performed. |
| Project Owner approval | PENDING | Human approval required. |

## Validation evidence

- Reviewed all 11 revised module detailed-curriculum files.
- Confirmed each module assessment table has one mapping row per module LO and includes the I/P/A legend.
- Confirmed no module retains the generic “Mapped lesson activity and assessment evidence” or generic “learner worksheet, notes, or practical artifact aligned” placeholders.
- Confirmed each module contains a practical activity blueprint, common rubric link, and reference catalog link.
- Recomputed lesson durations:
  - M01: 360 minutes
  - M02: 480 minutes
  - M03: 480 minutes
  - M04: 420 minutes
  - M05: 480 minutes
  - M06: 420 minutes
  - M07: 420 minutes
  - M08: 480 minutes
  - M09: 480 minutes
  - M10: 600 minutes
  - M11: 720 minutes
  - **Total: 5,340 minutes = 89 hours**
- Spot-checked official source pages. Not every catalog URL or every lesson claim was independently validated.
- Static document review only; no Markdown/link-check workflow or lab runtime test was run.

## Not validated

- Final technical correctness of all lesson claims against exact deployed versions.
- Student hardware capacity and installation-time feasibility.
- Splunk ingestion/search behavior and actual source fields.
- pfSense/Suricata package support and prevention/inline behavior in the target lab release.
- Reproducibility and runtime outcomes of practical activities.
- Classroom pacing, accessibility, cognitive load, and assessment reliability.
- Whether the proposed entry profile fits the actual cohort.

## Recommended next action

The curriculum design may proceed to Project Owner review as a **draft with notes**. Before creating final student-facing materials, confirm the learner entry profile, 89-hour schedule, grading policy, and Mailpit decision. Then develop and validate the detailed module labs/scenarios from the activity blueprints. Do not mark the curriculum approved or released without explicit Project Owner authorization.
