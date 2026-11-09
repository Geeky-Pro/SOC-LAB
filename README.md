# SOC-LAB

A structured, hands-on Security Operations Center (SOC) learning environment and curriculum.

## Project direction
SOC-LAB is organized around a competency-based curriculum, reproducible practical labs, realistic investigation scenarios, and independently reviewed learning materials. The repository is tool-aware but not tool-dependent: module titles describe security capabilities and investigative skills rather than vendor products.

## Project architecture
- [Project charter](governance/project-charter.md)
- [Repository architecture](governance/architecture/repository-architecture.md)
- [AI system architecture](governance/architecture/ai-system-architecture.md)
- [Curriculum overview](curriculum/curriculum-overview.md)
- [Module map](curriculum/module-map.md)
- [SOC lab environment](lab-environment/README.md)
- [Detection engineering](detection-engineering/README.md)
- [Canonical templates](templates/README.md)
- [Reusable agent skills](.agents/skills/README.md)
- [Archive](Archive/README.md)

## Curriculum
The proposed curriculum contains 11 capability-based modules, from SOC fundamentals through an integrated investigation and capstone. Module charters and curriculum maps remain drafts pending Project Owner approval. See curriculum/README.md and lectures/.

## AI-assisted content workflow
The project uses two complementary AI roles:
1. **SOC-LAB Content Engineer** — drafts and improves instructional and technical materials.
2. **SOC-LAB Quality Reviewer** — independently reviews accuracy, safety, reproducibility, and instructional quality.

See governance/architecture/ai-system-architecture.md. AI-generated content is not automatically approved; the Project Owner retains final approval authority.

## Content lifecycle
Content moves through planned → draft → in-review → approved → released. It may also be deprecated. A review status is not proof that a lab was executed; practical validation evidence must be recorded separately.

## Repository conventions
- Use English and lowercase kebab-case for paths and filenames unless a proper name or upstream filename must be preserved.
- Keep shared lab infrastructure in lab-environment/; unit-specific exercises belong inside their module.
- Keep shared detection standards and reusable detections in detection-engineering/; module-specific detection exercises stay with their module.
- Keep canonical reusable templates in templates/ and reusable agent procedures in .agents/skills/.
- Keep historical source material in Archive/ until reviewed.
- Never commit credentials, tokens, private keys, student personal data, or large VM images.

## Current status
The repository foundation, AI workflow, initial skills, templates, curriculum baseline, module charters, lab environment architecture, and detection engineering foundation are being established on architecture/v2-foundation. Curriculum, lab, and detection documentation remain drafts. No release or Project Owner approval is implied.

## Contributing
Read CONTRIBUTING.md, governance policies, and applicable quality standards before proposing changes.
