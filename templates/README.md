# Canonical Templates

This directory is the single source of truth for reusable SOC-LAB deliverable structures.

## Template catalog

| Template | Use |
|---|---|
| [Module README](module-readme.template.md) | Entry point for a learning module |
| [Lecture](lecture.template.md) | Lecture plan and learning package |
| [Lab Guide](lab-guide.template.md) | Student-facing practical exercise |
| [Scenario](scenario.template.md) | SOC investigation scenario and evidence design |
| [Installation Guide](installation-guide.template.md) | Tool/VM installation and configuration |
| [Instructor Guide](instructor-guide.template.md) | Instructor delivery notes and protected solutions |
| [Student Guide](student-guide.template.md) | Learner-facing module or activity guide |
| [Assessment](assessment.template.md) | Knowledge/practical assessment and rubric |
| [Quality Review Report](quality-review-report.template.md) | Independent review evidence and findings |
| [Diagram and Visual Brief](diagram-visual-brief.template.md) | Requirements for diagrams, illustrations, and animations |

## How to use

1. Copy the relevant template into the target module or project section.
2. Replace every bracketed placeholder with verified project-specific content.
3. Remove optional sections that genuinely do not apply; do not leave empty headings.
4. Keep the template's required safety, validation, and evidence fields where applicable.
5. Update the template when a reusable structure needs to change; do not fork competing variants without a documented reason.

## Conventions

- New files use English `kebab-case`; Arabic counterparts append `-ar` before the extension.
- Reusable learner-facing templates must support equivalent Arabic and English content and include counterpart/language metadata where appropriate.
- Use lifecycle status values: `planned`, `draft`, `in-review`, `approved`, `released`, `deprecated`.
- Templates are starting structures, not evidence that a deliverable is complete or validated.
- Approval and release require explicit Project Owner authorization.
- Student and instructor materials must be separated where answers, hints, or assessment solutions are sensitive.


## Bilingual authoring requirements

- Arabic and English are first-class project languages. Follow `governance/policies/bilingual-content-policy.md`.
- Keep paired documents in the same directory; English uses the canonical filename and Arabic appends `-ar` before the extension.
- Preserve stable IDs, technical meaning, commands, code, SPL, field names, configuration keys, numeric values, safety boundaries, evidence, and assessment requirements.
- Update both language variants together when meaning changes, or mark the counterpart `needs-update`/pending. Do not claim parity without reviewing both.
