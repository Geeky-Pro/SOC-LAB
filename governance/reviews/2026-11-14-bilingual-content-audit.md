# Bilingual Content Audit — Initial Inventory and Parity Review

> **Status:** draft — initial inventory completed; Module 01 translation remediation completed; Module 08 translation remediation pending  
> **Branch:** `arabic-content`  
> **Audit scope:** Markdown inventory, language-pair coverage, priority learner-facing documents, and selected structural parity checks  
> **Audit date:** 2026-11-14

## 1. Executive summary

The repository contains a substantial Arabic counterpart set, but bilingual coverage is not yet complete.

| Measure | Result |
|---|---:|
| Repository files in recursive tree | 338 |
| Markdown files | 307 |
| English-named Markdown files (excluding `-ar.md`) | 194 |
| Arabic Markdown files using `-ar.md` | 113 |
| Arabic files without an English basename counterpart | 0 |
| English files without an `-ar.md` counterpart | 81 |

At the initial audit snapshot, 81 English files lacked a `-ar.md` counterpart: 16 active instructional documents, 24 agent/developer support documents, and 41 archived/historical documents. After remediation, the current snapshot is 325 Markdown files: 195 English-named files and 130 Arabic files. Sixty-five English files still have no `-ar.md` counterpart: 24 agent/developer support documents and 41 archived/historical documents; no active module teaching documents remain unmatched.

## 2. Audit method and limits

- Enumerated tracked repository paths from the recursive Git tree for `arabic-content`.
- Matched Arabic files ending in `-ar.md` to English files with the same basename.
- Identified English Markdown files without a matching Arabic counterpart.
- Classified gaps by repository area and instructional relevance.
- Compared selected English/Arabic pairs for document length, heading count, table count, link count, and stable identifiers.
- Spot-checked the curriculum overview/index and Module 01 package navigation and status metadata.

This is an initial structural and targeted parity audit. It is **not** a line-by-line semantic review of all 113 Arabic files in the initial audit snapshot. Character-count and heading/table comparisons are triage signals, not proof of translation quality. No classroom, runtime lab, or learner usability validation was performed.

## 3. Missing Arabic counterparts — active instructional content

At the initial audit snapshot, 16 active learner-facing or instructor-facing documents lacked the expected Arabic `-ar.md` counterpart: nine in Module 01 and seven in Module 08. All 16 have since been translated. The lists below are retained as a record of discovered and remediated gaps.

### Module 01 — SOC Fundamentals (9 files)

1. `lectures/01-soc-fundamentals/planning/lesson-plan.md`
2. `lectures/01-soc-fundamentals/content/l01-05-analyst-documentation-and-evidence-discipline.md`
3. `lectures/01-soc-fundamentals/content/l01-06-integrated-triage-workshop.md`
4. `lectures/01-soc-fundamentals/instructor/instructor-guide.md`
5. `lectures/01-soc-fundamentals/student/student-guide.md`
6. `lectures/01-soc-fundamentals/labs/lab-01-a-alert-triage.md`
7. `lectures/01-soc-fundamentals/labs/lab-01-b-queue-prioritization-and-handoff.md`
8. `lectures/01-soc-fundamentals/assessments/module-01-practical-assessment.md`
9. `lectures/01-soc-fundamentals/validation/2026-11-10-module-01-content-quality-review.md`

Remediation completed: Arabic counterparts were added for the lesson plan, L01-05, L01-06, instructor guide, student guide, LAB-01-A, LAB-01-B, practical assessment, and the quality review report. The Arabic Module 01 README was updated to link to those counterparts. The English README package version was corrected to 0.3 while preserving the historical v0.2 review scope.

### Module 08 — Incident Response (7 files)

1. `lectures/08-incident-response/assessments/incident-response-assessment.md`
2. `lectures/08-incident-response/instructor/instructor-guide.md`
3. `lectures/08-incident-response/learning-outcomes.md`
4. `lectures/08-incident-response/lesson-plan.md`
5. `lectures/08-incident-response/scenarios/student-brief.md`
6. `lectures/08-incident-response/scenarios/tabletop-suspicious-web-server-compromise.md`
7. `lectures/08-incident-response/student/student-guide.md`

The Module 08 charter and detailed curriculum already have Arabic counterparts. The operational teaching package does not yet have complete Arabic coverage.

## 4. Other English-only files

### Agent and developer support — 24 files

These include the agent skill definitions, agent profiles, Copilot instructions, path-scoped instructions, and prompt files under `.agents/` and `.github/`. They are currently treated as machine-facing project configuration and authoring guidance rather than learner-facing course materials. English-only status is acceptable for this audit phase, but their intended audience should remain explicit. A future Arabic operator guide may be useful; duplicating executable agent instructions is not recommended unless a tested bilingual workflow requires it.

### Archive — 41 files

The archive contains historical documents, including legacy Arabic files that use older suffix conventions such as `_AR.md` rather than the current `-ar.md` convention. These are not counted as active bilingual gaps. Do not rename or translate archived materials automatically; review them only when a specific item is selected for reuse.

## 5. Targeted parity observations

### 5.1 Module 01 lesson content

The four existing lesson pairs (L01-01 through L01-04) have matching heading counts and table counts in the sampled structural comparison. Stable lesson and outcome identifiers checked in those pairs were preserved. Arabic text length ranged from approximately 78% to 84% of the English source; this is not inherently a defect because Arabic phrasing and typography differ. Full semantic review is still required.

### 5.2 Module 01 README

At the initial audit snapshot, the English and Arabic README files had the same 15 heading sections and five tables, but the Arabic package navigation pointed to some English-only files. The package version in the README was also 0.2 while its change history included 0.3. Both issues were corrected: the Arabic README now links to available Arabic counterparts and the package version is 0.3. The historical review remains correctly scoped to the initial v0.2 package and must not be rewritten to imply it reviewed v0.3.

### 5.3 Curriculum index and status metadata

At the initial audit snapshot, the curriculum index and detailed design carried stale status wording and did not reflect the v0.3 re-review report's **PASS WITH NOTES** result. The Arabic curriculum README also described several documents as English-only despite existing Arabic counterparts. These issues were corrected by updating both status fields and completing the Arabic index and links. Project Owner approval remains pending.

### 5.4 Module 01 lesson plan review status

At the initial audit snapshot, the lesson plan said independent review was pending. Its status was corrected to state that it was included in the Module 01 package review (**PASS WITH NOTES**), without claiming a separate standalone review of the plan.

## 6. Required remediation order

1. **Completed:** Corrected stale curriculum status and bilingual index links.
2. **Completed:** Corrected Module 01 package version metadata while preserving the historical v0.2 review scope.
3. **Completed:** Added the nine missing Arabic counterparts in Module 01.
4. **Completed:** Added the seven missing Arabic counterparts in Module 08 and updated its index and links.
5. **Next:** Conduct an independent Arabic/English parity review of the complete Module 01 and Module 08 packages.
6. Review the remaining paired governance, curriculum, lab-environment, detection-engineering, incident-response, and template documents in risk-prioritized batches.
7. Keep agent configuration and archived material out of learner-facing translation scope unless the Project Owner requests otherwise.

## 7. Acceptance criteria for a synchronized pair

- Same learning outcomes, stable IDs, scope, prerequisites, and audience.
- Same procedural steps, ordering, decision points, and expected results.
- Same safety boundaries, warnings, cleanup, rollback, and evidence requirements.
- Same assessment criteria, scoring references, and limitations.
- Technical strings and identifiers preserved.
- Reciprocal links and accurate translation status.
- Natural, technically accurate Arabic; no silent omissions or shortened replacement.
- Independent review findings recorded; translation parity does not imply technical validation, lab execution, approval, or release.

## 8. Current conclusion

**Structural pairing:** strong but incomplete. At the initial audit snapshot, all 113 Arabic `-ar.md` files had an English basename counterpart.

**Learner-facing bilingual completeness:** structural coverage is complete for active Markdown teaching assets in the modules; all active instructional files in the `lectures/` tree now have Arabic counterparts.

**Semantic parity:** partially spot-checked only; not yet established across the repository.

**Approval:** this report is a draft audit artifact. It does not approve the bilingual policy, curriculum, modules, or release of course materials.


## 9. Remediation progress after the initial snapshot

- Added nine Arabic counterparts for the Module 01 lecture plan, two remaining lessons, instructor guide, student guide, two labs, practical assessment, and quality review report.
- Updated the English source files with reciprocal Arabic links.
- Updated the Arabic Module 01 README to link to the new Arabic assets and identify the remaining English-only assets accurately.
- Corrected the Module 01 package version to 0.3 in both README variants. The historical quality review remains explicitly scoped to the initial v0.2 package.
- Updated the curriculum index and detailed curriculum status to reflect the existing v0.3 re-review result: PASS WITH NOTES, pending Project Owner decisions and approval.
- Created an Arabic curriculum index that links to all 11 Arabic detailed-curriculum files.

**Current inventory after remediation:** 356 repository files, 325 Markdown files, 195 English-named Markdown files, 130 Arabic `-ar.md` files, and 65 English Markdown files without a `-ar.md` counterpart. No active module teaching documents remain unmatched; the remaining unmatched files are 24 agent/developer support documents and 41 archived documents.

The new Arabic translations are draft assets. They have not yet received independent bilingual parity review. The initial 16-gap count remains as a historical baseline; all 16 have been remediated.


## 10. Module 08 remediation and metadata harmonization

The seven missing Arabic Module 08 counterparts were added: lesson plan, learning outcomes, instructor guide, student guide, student brief, tabletop scenario design, and assessment. Reciprocal links were added and the Arabic module index was updated.

Translation work exposed and remediated two internal inconsistencies in the English and Arabic Module 08 drafts:
- `learning-outcomes.md` used LO-01 through LO-08 while the detailed curriculum defines canonical LO-08-01 through LO-08-06. The outcomes file was aligned to the six canonical outcomes and given operational success criteria.
- The lesson plan and some delivery guides described 8.5 hours while the detailed curriculum specifies 8 hours. The lesson plan, instructor guide, student guide, scenario, and assessment were aligned to 480 minutes, with the debrief included in the tabletop.
- Some instructor materials were labeled instructor-only despite residing in a public repository. Public-repository boundaries were clarified and detailed expected analyst reasoning was removed from the public scenario design. The inject sequence itself remains visible in the public repository; use a private access-controlled copy if concealment is required.

No independent bilingual content review, tabletop delivery, or operational lab validation has yet been performed.
