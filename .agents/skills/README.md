# SOC-LAB Skills Registry

This directory contains reusable, task-focused Agent Skills. Skills define repeatable methods and checklists; they do not create new agents or override repository governance.

## Usage

1. Select a skill only when its stated trigger matches the task.
2. Read its complete `SKILL.md` before applying it.
3. Follow root `AGENTS.md`, the Project Charter, relevant architecture, policies, path-scoped instructions, and canonical templates.
4. Use the Content Engineer for authoring and the Quality Reviewer for independent review.
5. Do not treat skill execution as approval or evidence of lab execution.

## Initial skills

| Skill | Primary use | Primary owner |
|---|---|---|
| `soc-curriculum-design` | Curriculum structure, outcomes, mapping, sequencing | Content Engineer |
| `soc-lecture-development` | Lecture plans, teaching sequence, learning assets | Content Engineer |
| `soc-lab-development` | Reproducible hands-on exercises | Content Engineer |
| `soc-scenario-development` | Investigation scenarios and evidence design | Content Engineer |
| `soc-quality-review` | Independent evidence-based quality review | Quality Reviewer |

## Boundaries

- Keep skills small, reusable, and non-overlapping.
- Keep canonical deliverable formats in `templates/`; do not embed competing full templates in skills.
- Keep project authority and role boundaries in `.github/agents/` and governance documents.
- Keep task-specific prompt scaffolds in `.github/prompts/`.
- Add supporting `references/`, `examples/`, or `scripts/` only when they materially improve the skill.
- Verify skill discovery and invocation in the intended agent runtime; repository presence alone does not guarantee automatic discovery.
