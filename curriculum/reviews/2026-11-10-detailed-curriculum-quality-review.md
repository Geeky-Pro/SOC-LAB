# Quality Review — Detailed Curriculum Design (All 11 Modules)

- **Review date:** 2026-11-10
- **Reviewer:** SOC-LAB Quality Reviewer (AI-assisted independent document review)
- **Branch:** `architecture/v2-foundation`
- **Scope:** Program-level detailed curriculum and all 11 module `detailed-curriculum.md` files; relevant competency, prerequisite, assessment, lab-dependency, ATT&CK, governance, and quality-standard documents.
- **Overall status:** **NEEDS REVISION**
- **Review limitations:** Static document review only. No classroom pilot, learner usability test, lab deployment, event-generation test, Splunk search execution, detection runtime validation, or external-reference verification was performed. This report is a review recommendation, not Project Owner approval.

## Summary

The 11-module structure is coherent at a high level and follows the intended progression from SOC foundations and lab setup through focused investigations, incident response, controlled simulation, integrated investigation, and capstone. The proposed total of **89 contact hours is arithmetically consistent**: all 11 module lesson-duration sums match their stated module durations.

The curriculum is not yet ready for approval because outcome-to-lesson mapping is too broad to demonstrate traceability, assessment evidence is mostly generic, module-level references are not actually supplied, and some cross-module capability coverage needs to be made explicit. The documents are useful detailed-design drafts, but they are not yet instructional blueprints ready for lesson/lab production without revision.

## Findings

### Q-01 — Learning-outcome alignment is not sufficiently discriminating

- **Severity:** High
- **Files:** All `lectures/*/detailed-curriculum.md` files; section 3, “Measurable learning outcomes”.
- **Evidence:** In every reviewed module, most or all learning outcomes are mapped to every lesson in that module. For example, all six Module 10 outcomes are mapped to L10-01 through L10-07, despite lessons having distinct purposes such as endpoint evidence analysis, web reconstruction, response briefing, and detection gap analysis.
- **Why it matters:** This mapping does not show where an outcome is introduced, practiced, and demonstrated. It prevents instructors and reviewers from identifying missing instruction, redundant lessons, or assessment gaps.
- **Required correction:** Replace broad all-lessons mappings with a defensible outcome-to-lesson matrix. Identify for each outcome the lesson(s) where it is introduced, practiced, and assessed (for example: I/P/A or equivalent). Ensure each outcome has at least one explicit assessment point and that lesson content actually supports the mapped outcome.

### Q-02 — Assessment evidence is generic and lacks observable performance criteria

- **Severity:** High
- **Files:** All `lectures/*/detailed-curriculum.md` files; sections 3, 4, and 6.
- **Evidence:** Outcome evidence cells frequently use phrases such as “Mapped lesson activity and assessment evidence”; lesson evidence repeatedly says “learner worksheet, notes, or practical artifact aligned to the lesson outcomes.” The module assessment section lists broad deliverables but does not specify success criteria or performance descriptors.
- **Why it matters:** Students and instructors cannot consistently determine what a satisfactory submission looks like, and reviewers cannot verify that each outcome is genuinely assessed. The current detail is insufficient to support fair, repeatable assessment.
- **Required correction:** For each module, specify concrete artifacts and observable criteria linked to LO IDs. Add a compact rubric or reference the canonical assessment rubric once established. Define minimum evidence quality (source attribution, timestamps where applicable, reasoning, alternative explanations, uncertainty, and safe handling) and identify individual versus group evidence. Keep weights and pass thresholds explicitly provisional until Project Owner decision.

### Q-03 — Technical and instructional references are not provided at module level

- **Severity:** High
- **Files:** All `lectures/*/detailed-curriculum.md` files; section 11, “References”.
- **Evidence:** Every module contains only the instruction “Use authoritative, versioned sources appropriate to the lesson” rather than actual references. No source list is supplied to substantiate technical concepts, standards, or tool-specific claims.
- **Why it matters:** Instructors cannot trace claims to authoritative sources or check version currency. This is especially important for Windows/Sysmon event semantics, email authentication, protocol analysis, Suricata/pfSense behavior, Splunk Enterprise capabilities, incident response guidance, and attack emulation.
- **Required correction:** Add a concise, lesson-mapped reference list per module. Prefer primary vendor documentation and authoritative standards. Record title, publisher, version/revision, URL, and access date where applicable. Do not cite sources that have not actually been consulted; mark unresolved references as pending research rather than implying verification.

### Q-04 — Integrated Operation Shadow Access does not explicitly integrate email evidence

- **Severity:** Medium
- **Files:** `lectures/10-operation-shadow-access/detailed-curriculum.md`; sections 2, 3, 4, and 5; `curriculum/lab-dependency-map.md`.
- **Evidence:** Module 10 is described as a multi-source integrated investigation and depends on Modules 03–09, but its outcomes and lesson sequence explicitly cover endpoint, network, IDS, web, and SIEM evidence without an email/phishing evidence stream. Module 04 is otherwise part of the core sequence and the lab dependency map lists Mailpit as an optional source for Modules 04, 10, and 11.
- **Why it matters:** The integrated exercise may not assess transfer of the email-investigation capability into a cross-domain case, despite the broad dependency claim. This can leave an unexplained gap between the taught capability and integrated assessment.
- **Required correction:** Decide explicitly whether email evidence is part of Operation Shadow Access. If yes, add a bounded email artifact/investigation inject and map it to Module 04 outcomes. If no, narrow the stated integration/dependency claims and explain why email is excluded from this scenario. Keep Mailpit optional by allowing a clearly labeled sanitized email artifact when the service is not deployed.

### Q-05 — “Prevention” is underrepresented in the Network Intrusion Detection & Prevention module

- **Severity:** Medium
- **Files:** `lectures/06-network-intrusion-detection/detailed-curriculum.md`; module title, outcomes, and lessons.
- **Evidence:** The module title includes Intrusion Detection & Prevention and one lesson introduces inline versus passive deployment, but the outcomes and practical sequence focus mainly on interpreting alerts, packet validation, tuning, and detection validation. No explicit outcome or practical assessment demonstrates prevention-policy reasoning or safe validation of a prevention control.
- **Why it matters:** The title may promise a capability that the module does not teach or assess. Learners may conflate passive detection with active blocking.
- **Required correction:** Either (a) add an explicit, safe prevention learning outcome and instructor-controlled lab activity that distinguishes detection from prevention, tests an approved block action, verifies impact, and provides rollback; or (b) narrow the title and scope to Network Intrusion Detection. Do not enable inline blocking on student systems without explicit lab authorization and recovery controls.

### Q-06 — Learner entry profile and prerequisite proficiency are not operationalized

- **Severity:** Medium
- **Files:** `curriculum/curriculum-overview.md`; all module detailed curricula; `curriculum/prerequisite-map.md`.
- **Evidence:** The program overview says entry requirements remain to be confirmed. Module prerequisites use broad phrases such as “basic Windows/Linux and networking familiarity” and “basic email, DNS, URL, and file concepts” without defining the minimum knowledge or how gaps will be identified.
- **Why it matters:** The proposed 89-hour schedule and lab pace cannot be evaluated reliably without a learner baseline. Students may encounter avoidable blockers in networking, Windows logs, command-line use, or protocol fundamentals.
- **Required correction:** Define a proposed entry profile and a short diagnostic/prerequisite checklist. For each prerequisite, specify the expected observable baseline and a remediation path or pre-course primer. Keep the profile provisional until the Project Owner confirms the cohort.

### Q-07 — Practical activities are curriculum summaries, not yet executable lab specifications

- **Severity:** Medium
- **Files:** All `lectures/*/detailed-curriculum.md` files; section 5.
- **Evidence:** Practical activities are generally one-line summaries. They do not yet identify the exact learner task sequence, provided dataset/artifact, expected observations, evidence capture format, cleanup/reset, or instructor preparation.
- **Why it matters:** The current documents can guide future lab design but cannot be used as student lab instructions or as proof that the activities are reproducible.
- **Required correction:** Keep the curriculum concise, but create a traceable lab/scenario specification for every practical activity before producing student-facing lab guides. Each specification must define objectives, prerequisites, scope, environment/dataset, steps, expected evidence, assessment mapping, safety, cleanup/reset, and instructor-only notes. Clearly label activities that use synthetic or pre-captured evidence.

## Acceptance criteria checklist

| Criterion | Result | Notes |
|---|---|---|
| Purpose and high-level 11-module progression are clear | PASS | Capability-led progression is coherent. |
| Proposed duration arithmetic is consistent | PASS | 89 hours total; each module's lesson minutes match its stated hours. |
| Prerequisite sequence is broadly coherent | PASS WITH NOTES | Needs entry-level definition and clearer proficiency gates. |
| Outcomes are measurable in wording | PASS WITH NOTES | Most are observable, but several need tighter scope and explicit performance conditions. |
| Outcomes map to lessons and assessment evidence | NEEDS REVISION | Current mappings are overly broad and evidence labels generic. |
| Assessment criteria and rubrics are actionable | NEEDS REVISION | Concrete artifacts exist, but performance descriptors and scoring guidance are missing. |
| Technical references are traceable | NEEDS REVISION | Module reference sections contain instructions, not references. |
| Lab dependencies reflect the current baseline | PASS WITH NOTES | Logical mapping exists; runtime source readiness is not validated. |
| Safety boundaries are documented | PASS WITH NOTES | Good high-level guardrails; activity-specific controls must be specified in lab assets. |
| Student/instructor separation is designed | NEEDS REVISION | The curriculum calls for separation but does not yet define per-module instructor keys/materials. |
| Technical execution and classroom delivery are validated | NOT VALIDATED | No deployment or pilot evidence reviewed. |
| Project Owner approval | PENDING | Human approval required. |

## Validation evidence

- Read the Quality Reviewer agent instructions, repository operating instructions, Project Charter, curriculum instructions, and applicable governance quality standards.
- Read the program-level detailed curriculum, competency matrix, prerequisite map, assessment framework, lab dependency map, and ATT&CK coverage plan.
- Read all 11 module detailed-curriculum files.
- Recomputed lesson-duration totals for every module. Results: M01 360 min; M02 480 min; M03 480 min; M04 420 min; M05 480 min; M06 420 min; M07 420 min; M08 480 min; M09 480 min; M10 600 min; M11 720 min. These sum to 5,340 minutes (89 hours).
- Confirmed that the program-level total and per-module declared contact hours match those totals.
- Static inspection only; no automated link checker, Markdown linter, curriculum validator, lab execution, or classroom pilot was run.

## Not validated

- Accuracy and currentness of technical claims against external primary sources.
- Tool-version compatibility and actual Splunk/pfSense/Suricata/Sysmon telemetry behavior.
- VM sizing and whether each activity fits the proposed instructional time in the student environment.
- Actual reproducibility of labs and scenarios.
- Learner accessibility, cognitive load, and classroom pacing.
- Assessment fairness, rubric reliability, and capstone scoring.
- Any runtime detection or prevention effectiveness.

## Recommended next action

Return the curriculum to the Content Engineer for a focused revision addressing Q-01 through Q-07. Prioritize outcome-to-lesson traceability, concrete assessment evidence/rubrics, and authoritative references. Then re-review the revised curriculum before Project Owner approval. Do not mark any module approved or begin final student-facing material production until the review findings and Project Owner decisions are addressed.
