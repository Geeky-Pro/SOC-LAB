# SOC-LAB

A structured, hands-on Security Operations Center (SOC) learning environment and curriculum.

## Project direction

SOC-LAB is organized around a competency-based curriculum, reproducible practical labs, realistic investigation scenarios, and independently reviewed learning materials. The repository is tool-aware but not tool-dependent: module titles describe security capabilities and investigative skills rather than vendor products.

## Current architecture

- [Project charter](governance/project-charter.md)
- [Repository architecture](governance/architecture/repository-architecture.md)
- [AI system architecture](governance/architecture/ai-system-architecture.md)
- [Curriculum overview](curriculum/curriculum-overview.md)
- [Module map](curriculum/module-map.md)
- [Canonical templates](templates/README.md)
- [Reusable agent skills](.agents/skills/README.md)
- [Archive](Archive/README.md) — historical material retained for review and controlled reuse

## Curriculum

The proposed curriculum contains 11 capability-based modules, from SOC fundamentals through an integrated investigation and capstone. All module charters and curriculum maps are currently drafts pending Project Owner approval.

Detailed module entry points are under `lectures/`. See [curriculum/README.md](curriculum/README.md) for the curriculum documents and [module architecture](governance/architecture/module-architecture.md) for module package conventions.

## AI-assisted content workflow

The project uses two complementary AI roles:

1. **SOC-LAB Content Engineer** — drafts and improves instructional and technical materials.
2. **SOC-LAB Quality Reviewer** — independently reviews accuracy, safety, reproducibility, and instructional quality.

See [AI system architecture](governance/architecture/ai-system-architecture.md). AI-generated content is not automatically approved. The Project Owner retains final approval authority.

## Content lifecycle

Content moves through: `planned` → `draft` → `in-review` → `approved` → `released`. It may also be marked `deprecated`. A review status is not proof that a lab was executed; practical validation evidence must be recorded separately.

## Repository conventions

- Use English, lowercase `kebab-case` for paths and filenames unless a proper name or upstream filename must be preserved.
- Keep shared lab infrastructure in `lab-environment/`; unit-specific exercises belong inside their module.
- Keep reusable project-wide templates in `templates/`.
- Keep reusable agent procedures in `.agents/skills/`.
- Keep historical source material in `Archive/` until it has been reviewed.
- Never commit credentials, tokens, private keys, student personal data, or large VM images.

## Project status

The repository foundation, AI workflow, initial reusable skills, canonical templates, curriculum baseline, and 11 module charters are being established on the `architecture/v2-foundation` branch. The curriculum and module charters remain drafts; no release or Project Owner approval is implied.

## Contributing

Read [CONTRIBUTING.md](CONTRIBUTING.md), the governance policies, and the applicable quality standards before proposing changes.
