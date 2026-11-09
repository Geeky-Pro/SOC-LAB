# AI System Architecture

## Design

The project uses two focused AI roles rather than a large collection of narrowly scoped agents.

### SOC-LAB Content Engineer

Responsible for drafting, organizing, and improving curriculum and learning assets: lectures, slides, labs, scenarios, installation guides, instructor/student materials, assessments, diagrams, and supporting documentation.

### SOC-LAB Quality Reviewer

Responsible for independent review of technical accuracy, safety, reproducibility, instructional quality, completeness, references, and consistency. It reports evidence and findings; it does not silently rewrite and approve its own review target.

## Skills

Reusable skills provide task-specific methods and checklists. They should be composable and discoverable, with a clear `SKILL.md` entry point and supporting references, templates, or examples where justified.

Initial skill candidates include curriculum design, lecture development, slide development, lab development, installation documentation, scenario development, instructor/student material development, visual and diagram development, assessment development, security validation, technical documentation, and quality review.

## Authority boundaries

- AI agents are assistants, not project owners.
- The Content Engineer cannot self-approve.
- The Quality Reviewer must distinguish evidence from assumptions.
- The human Project Owner decides acceptance, scope, and release.
- Agents must not claim external research, file edits, test execution, or lab validation that did not occur.

## Workflow

Request → context inspection → draft → self-check → independent review → revision → Project Owner approval → release preparation.

## Implementation note

Agent definitions and provider-specific instructions belong under `.github/` where appropriate. Reusable skills belong under `.agents/skills/`. Provider-specific discovery behavior must be configured and verified rather than assumed.
