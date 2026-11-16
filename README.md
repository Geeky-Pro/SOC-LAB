# SOC-LAB

> **Bilingual project | مشروع ثنائي اللغة**

> English and Arabic are first-class project languages. Technical identifiers, commands, code, product names, and standards remain in their canonical form where translation would reduce precision.

> العربية والإنجليزية لغتان أساسيتان للمشروع. تبقى المعرفات التقنية والأوامر والأكواد وأسماء المنتجات والمعايير بصيغتها الأصلية عندما تؤثر ترجمتها في الدقة.

A structured, hands-on Security Operations Center (SOC) learning environment and curriculum.
بيئة تعليمية ومنهج عملي منظم لتعلّم عمليات مراكز العمليات الأمنية (SOC).

## Start here | ابدأ من هنا

- [Arabic overview | النظرة العامة بالعربية](README-ar.md)
- [Bilingual Content Policy](governance/policies/bilingual-content-policy.md) · [سياسة المحتوى ثنائي اللغة](governance/policies/bilingual-content-policy-ar.md)
- [Project Charter](governance/project-charter.md) · [ميثاق المشروع](governance/project-charter-ar.md)
- [Repository Architecture](governance/architecture/repository-architecture.md) · [معمارية المستودع](governance/architecture/repository-architecture-ar.md)
- [Curriculum](curriculum/README.md) · [المنهج](curriculum/README-ar.md)
- [SOC Lab Environment](lab-environment/README.md) · [بيئة المختبر](lab-environment/README-ar.md)
- [Detection Engineering](detection-engineering/README.md) · [هندسة الكشف](detection-engineering/README-ar.md)
- [Incident Response](incident-response/README.md) · [الاستجابة للحوادث](incident-response/README-ar.md)
- [Templates](templates/README.md) · [القوالب](templates/README-ar.md)
- [Agent Skills](.agents/skills/README.md)

## Project direction

SOC-LAB is organized around a competency-based curriculum, reproducible practical labs, realistic investigation scenarios, and independently reviewed learning materials. Module titles describe security capabilities and investigative skills rather than vendor products.

## Bilingual Content Audit

- [Initial bilingual content audit — current remediation status](governance/reviews/2026-11-14-bilingual-content-audit.md)
- [Arabic audit report](governance/reviews/2026-11-14-bilingual-content-audit-ar.md)

## Curriculum

The proposed curriculum contains 11 capability-based modules, from SOC fundamentals through an integrated investigation and capstone. Module charters and curriculum maps remain drafts pending Project Owner approval.

## Languages and synchronization

- Arabic and English are first-class languages, not separate curricula.
- English filenames are canonical; Arabic counterparts use the `-ar` suffix before the extension.
- Stable IDs, commands, code, SPL, configuration keys, IP addresses, product names, and standards identifiers remain unchanged.
- Substantial paired documents link to one another and disclose translation status.
- Learning outcomes, procedures, safety controls, evidence, and assessment criteria must remain equivalent.

## AI-assisted content workflow

- **SOC-LAB Content Engineer** drafts and maintains paired language variants.
- **SOC-LAB Quality Reviewer** independently checks technical, instructional, language, and cross-language quality.
- The Project Owner retains final approval and release authority.

## Content lifecycle

Content moves through planned → draft → in-review → approved → released. Translation status and practical validation are tracked separately. A review status is not proof that a lab was executed.

## Repository conventions

- Use English lowercase `kebab-case` paths; Arabic counterparts append `-ar`.
- Keep shared lab infrastructure in `lab-environment/`; module-specific exercises belong inside their module.
- Keep shared detection standards in `detection-engineering/`; module-specific detections stay with their module.
- Keep shared response procedures in `incident-response/`; scenario-specific playbooks remain with the relevant module.
- Keep canonical templates in `templates/` and reusable agent procedures in `.agents/skills/`.
- Keep historical material in `Archive/` until reviewed.
- Never commit credentials, private student data, protected answer keys, or large VM images.

## Current status

The active development branch is `arabic-content`, extending the repository foundation with Arabic counterparts. Bilingual architecture and governance are being standardized. Curriculum and learning assets remain drafts unless explicitly approved by the Project Owner.

## Contributing

Read `AGENTS.md`, `CONTRIBUTING.md`, and the bilingual content policy before contributing.