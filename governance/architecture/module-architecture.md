# Module Architecture

## Module design

Each module is a coherent learning package with explicit outcomes, prerequisites, teaching content, practice, assessment, and review evidence.

## Recommended contents

Create only what the module needs:

- `README.md`: purpose, scope, outcomes, prerequisites, status, and contents.
- `planning/`: lesson plan, content outline, objectives, dependencies.
- `content/`: lecture notes and concept explanations.
- `instructor/`: delivery guide, teaching notes, discussion prompts, and protected answer keys.
- `student/`: student guide, worksheets, and quick references.
- `slides/`: slide outline, presentation source, and assets.
- `labs/`: setup, execution, expected evidence, troubleshooting, cleanup, and validation.
- `scenarios/`: brief, scope, storyline, evidence, investigation tasks, detections, and debrief.
- `detections/`: module-specific rules, queries, dashboards, and validation.
- `assessments/`: exercises, practical assessments, rubrics, and solutions.
- `media/`: images, diagrams, animations, and video assets.
- `references/`: authoritative sources and further reading.
- `validation/`: technical, instructional, lab, and release reviews.

## Required quality

Every practical activity must define learning purpose, prerequisites, authorized scope, steps, expected results, cleanup, and troubleshooting. Include a validation record or explicitly mark it as not validated.

## Audience separation

Student-facing materials must not accidentally expose instructor answer keys or assessment solutions. Apply repository visibility and release packaging decisions accordingly.


## Bilingual module documents

Do not create separate Arabic and English module trees. Keep paired documents in the same module subdirectory, for example `README.md` / `README-ar.md`, `lesson-plan.md` / `lesson-plan-ar.md`, and `student-guide.md` / `student-guide-ar.md`. Keep module, lesson, LO, lab, scenario, assessment, and evidence IDs identical. Both variants must describe the same scope, steps, expected evidence, safety controls, cleanup, and assessment requirements. Missing counterparts must be explicitly marked pending. See the Bilingual Content Policy.
