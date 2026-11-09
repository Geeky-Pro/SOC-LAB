# SOC-LAB

A structured, hands-on Security Operations Center (SOC) learning environment and curriculum.

## Project direction

SOC-LAB is being reorganized around a competency-based curriculum, reproducible practical labs, realistic investigation scenarios, and independently reviewed learning materials. The repository is tool-aware but not tool-dependent: module titles describe security capabilities and investigative skills rather than vendor products.

## Current architecture

- [Project charter](governance/project-charter.md)
- [Repository architecture](governance/architecture/repository-architecture.md)
- [AI system architecture](governance/architecture/ai-system-architecture.md)
- [Archive](Archive/README.md) — historical material retained for review and controlled reuse

## AI-assisted content workflow

The project is designed around two complementary AI roles:

1. **SOC-LAB Content Engineer** — drafts and improves instructional and technical materials.
2. **SOC-LAB Quality Reviewer** — independently reviews accuracy, safety, reproducibility, and instructional quality.

AI-generated content is not automatically approved. The Project Owner retains final approval authority.

## Content lifecycle

Content moves through: `planned` → `draft` → `in-review` → `approved` → `released`. It may also be marked `deprecated`. A review status is not proof that a lab was executed; practical validation evidence must be recorded separately.

## Repository conventions

- Use English, lowercase `kebab-case` for paths and filenames unless a proper name or upstream filename must be preserved.
- Keep shared lab infrastructure in `lab-environment/`; unit-specific exercises belong inside their module.
- Keep reusable project-wide templates in `templates/`.
- Keep historical source material in `Archive/` until it has been reviewed.
- Never commit credentials, tokens, private keys, student personal data, or large VM images.

## Project status

The repository foundation is being established on the `architecture/v2-foundation` branch. Curriculum, AI agent definitions, skills, templates, and module content will be introduced in subsequent phases.

## Contributing

Read [CONTRIBUTING.md](CONTRIBUTING.md), the governance policies, and the applicable quality standards before proposing changes.
