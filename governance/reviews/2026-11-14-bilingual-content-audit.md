# Bilingual Content Audit — Initial Inventory and Parity Review

> **Status:** draft — initial structural audit; semantic review and remediation in progress  
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

The 81 missing counterparts are not all learner-facing translation gaps. They comprise 16 active instructional documents, 24 agent/developer support documents, and 41 archived/historical documents. The latter two groups are treated separately below.

## 2. Audit method and limits

- Enumerated tracked repository paths from the recursive Git tree for `arabic-content`.
- Matched Arabic files ending in `-ar.md` to English files with the same basename.
- Identified English Markdown files without a matching Arabic counterpart.
- Classified gaps by repository area and instructional relevance.
- Compared selected English/Arabic pairs for document length, heading count, table count, link count, and stable identifiers.
- Spot-checked the curriculum overview/index and Module 01 package navigation and status metadata.

This is an initial structural and targeted parity audit. It is **not** a line-by-line semantic review of all 113 Arabic files. Character-count and heading/table comparisons are triage signals, not proof of translation quality. No classroom, runtime lab, or learner usability validation was performed.

## 3. Missing Arabic counterparts — active instructional content

Sixteen active learner-facing or instructor-facing documents currently lack the expected Arabic `-ar.md` counterpart.

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

The module has Arabic counterparts for its README, detailed curriculum, and the first four lesson-content files. The missing items above mean that the Arabic package index currently points to several English-only resources without clearly distinguishing them as temporary English references.

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

The English and Arabic README files have the same 15 heading sections and five tables. Their package navigation is not fully bilingual yet: the Arabic README currently links several items to English filenames where Arabic counterparts are absent. The README also reports package version 0.2 while its change history includes version 0.3 for the addition of the independent review record. The historical review itself correctly identifies the reviewed initial package as v0.2; it must not be rewritten to claim that it reviewed v0.3.

### 5.3 Curriculum index and status metadata

- `curriculum/README.md` still says the curriculum is awaiting re-review even though the v0.3 re-review report exists and records **PASS WITH NOTES**.
- `curriculum/detailed-curriculum-design.md` and its Arabic counterpart carry the same stale status wording.
- The Arabic curriculum README says several documents are still available only in English, although corresponding Arabic files now exist. Its document navigation is incomplete compared with the English index.
- The Arabic and English versions should report the same review result and approval boundary.

### 5.4 Module 01 lesson plan review status

The lesson plan says independent review is pending. The package-level independent review has already been completed with **PASS WITH NOTES** and explicitly checked the plan's timing and package links. The plan should describe this accurately as a package-level review, not imply a separate standalone review.

## 6. Required remediation order

1. Correct stale curriculum status and bilingual index links.
2. Correct Module 01 package version metadata while preserving the historical v0.2 review scope.
3. Complete the nine missing Arabic counterparts in Module 01.
4. Run an independent Arabic/English parity review of the complete Module 01 package.
5. Complete the seven missing Arabic counterparts in Module 08.
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

**Structural pairing:** strong but incomplete. All 113 Arabic `-ar.md` files have an English basename counterpart.

**Learner-facing bilingual completeness:** not achieved. Sixteen active instructional documents remain without Arabic counterparts, concentrated in Modules 01 and 08.

**Semantic parity:** partially spot-checked only; not yet established across the repository.

**Approval:** this report is a draft audit artifact. It does not approve the bilingual policy, curriculum, modules, or release of course materials.
