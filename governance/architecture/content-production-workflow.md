# Content Production Workflow

## Standard lifecycle

1. **Intake:** identify audience, module, learning outcome, deliverable, constraints, dependencies, and intended status.
2. **Context review:** read project standards, existing module content, canonical templates, and authoritative references.
3. **Plan:** define structure, practical requirements, assets, dependencies, and acceptance criteria.
4. **Draft:** the Content Engineer creates the content using relevant path instructions, skills, and canonical templates.
5. **Author check:** the Content Engineer checks completeness, links, terminology, source quality, consistency, and safety.
6. **Independent review:** the Quality Reviewer evaluates the submitted artifact and returns an evidence-based report.
7. **Revision:** the Content Engineer addresses findings and provides a finding-by-finding resolution summary.
8. **Re-review:** the Quality Reviewer verifies material changes and identifies remaining issues.
9. **Owner approval:** the Project Owner explicitly accepts the deliverable and decides whether it may be marked approved.
10. **Release preparation:** validate packaging, access separation, version metadata, and release notes.
11. **Maintenance:** revisit content when tools, versions, references, or learning outcomes change.

## Required role separation

- Content Engineer: author and revise; cannot self-approve.
- Quality Reviewer: review independently; reports status and evidence but does not grant approval.
- Project Owner: decides acceptance, scope, and release.

## Review statuses

Use one of: `PASS`, `PASS WITH NOTES`, `NEEDS REVISION`, `BLOCKED`, or `NOT VALIDATED`. These describe review outcomes only. They do not change lifecycle status or authorize release.

## Evidence and validation

A content review is not a substitute for executing a lab. Practical validation must be performed and recorded separately. Every report must distinguish:
- Documented: described in repository content.
- Statically checked: inspected without executing the procedure.
- Executed: steps were performed in an identified environment.
- Tested: expected behavior was checked against defined criteria.
- Independently validated: another qualified reviewer reproduced or verified the behavior.

Do not use a stronger status than the available evidence supports.

## Reusable automation assets

- Agent definitions in `.github/agents/` define responsibilities and boundaries.
- Copilot repository/path instructions in `.github/` define context and authoring constraints.
- Prompt starters in `.github/prompts/` provide task-specific request scaffolds.
- Reusable Skills in `.agents/skills/` provide detailed repeatable methods and checklists.
- Canonical templates in `templates/` define deliverable structure.

Keep these layers complementary. Do not duplicate canonical templates or copy entire skill procedures into prompts.
