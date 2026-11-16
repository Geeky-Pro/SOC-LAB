# Repository Architecture

## Architectural goals

The repository separates governance, curriculum, teaching modules, shared lab infrastructure, detection engineering, incident response, templates, automation, validation, and historical content.

## Top-level responsibilities

| Path | Responsibility |
|---|---|
| `.github/` | GitHub-specific agent definitions, instructions, prompts, workflows, and issue templates. |
| `.agents/skills/` | Reusable Agent Skills following the Agent Skills structure. |
| `governance/` | Project authority, policies, roles, quality standards, and architecture decisions. |
| `curriculum/` | Program-level learning outcomes, maps, competencies, schedule, and assessment design. |
| `lectures/` | Self-contained module learning packages, including instructor/student materials, labs, scenarios, and assessments. |
| `lab-environment/` | Shared lab architecture, deployment, configurations, validation, and recovery. |
| `detection-engineering/` | Shared detection standards, rules, queries, mappings, and validation methods. |
| `incident-response/` | Shared response procedures and playbook standards. |
| `instructor/` | Program-wide teaching and classroom delivery guidance. |
| `templates/` | Canonical reusable content templates. |
| `tooling/` | Scripts, validators, generators, and asset processing. |
| `tests/` | Automated repository, documentation, configuration, and release checks. |
| `releases/` | Release notes and manifests. |
| `Archive/` | Historical materials retained for review and provenance. |

## Placement rules

- Shared infrastructure belongs in `lab-environment/`; module-specific exercises belong in that module's `labs/`.
- Shared detection assets belong in `detection-engineering/`; module-specific detections belong in the module.
- General response procedures belong in `incident-response/`; scenario-specific response tasks remain with the scenario.
- Project-wide teaching guidance belongs in `instructor/`; module delivery notes belong in the module's `instructor/`.
- Canonical templates belong in `templates/`. Skills may reference templates but should not maintain conflicting copies.
- Do not create empty directories or speculative files merely to make the tree look complete.

## Module structure

See [Module Architecture](module-architecture.md). A module contains only the subdirectories needed for its actual learning package.


## Bilingual content architecture

Arabic and English are first-class languages maintained as paired documents within the same repository structure. Do not create parallel language trees. English filenames remain canonical; Arabic counterparts append `-ar` before the extension and stay in the same directory. Shared identifiers and machine-readable assets remain language-neutral. Substantial documents link to counterparts. Update both variants together or explicitly mark pending translation. Translation status, content review, and practical validation are separate. See `governance/policies/bilingual-content-policy.md`.
