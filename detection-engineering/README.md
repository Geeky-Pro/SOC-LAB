# Detection Engineering

> **Status:** draft foundation — no detection is considered operational or validated merely because its specification or SPL exists.

## Purpose
Provide a consistent, evidence-based method to design, document, test, tune, maintain, and retire detections across SOC-LAB modules. The framework is SIEM-aware but focused on observable behavior and investigative value.

## Current platform boundary
The current lab baseline uses **Splunk Enterprise only**. Detection examples and searches may use SPL. Splunk Enterprise Security is not a dependency. Do not assume premium correlation-search, risk-based alerting, or ES-specific content is available.

## Structure
- `standards/detection-rule-standard.md` — required detection specification fields and acceptance criteria
- `standards/spl-style-guide.md` — SPL authoring conventions
- `standards/detection-lifecycle.md` — proposal through retirement
- `data-sources/source-catalog.md` — telemetry readiness and source ownership
- `validation/validation-methodology.md` — repeatable test and evidence process
- `mappings/mitre-attack-mapping-guidance.md` — behavior-grounded ATT&CK mapping
- `rules/README.md` — shared detection rule index
- `shared-searches/README.md` — reusable investigation searches
- `templates/detection-spec-template.md` — canonical detection specification
- `templates/detection-test-case-template.md` — canonical test record

## Ownership and placement
- Reusable detections and shared searches belong here.
- Exercise-specific detection logic, scenario evidence, and learner tasks belong in the relevant `lectures/*/` module.
- Source-specific collection configuration belongs in `lab-environment/`.
- Do not duplicate canonical templates in modules.
- Content Engineer drafts; Quality Reviewer reviews independently; Project Owner approves.

## Detection states
Use one state per detection: `planned`, `draft`, `in-review`, `approved`, `implemented`, `validated`, `tuning`, `deprecated`.
Approval, implementation, and validation are separate states. A rule can be approved but not implemented; implemented but not validated; or validated only for a defined test scope.

## Minimum quality bar
Every detection must state its observable behavior, data dependencies, SPL, expected output, false-positive considerations, analyst triage guidance, ATT&CK mapping (only when supported), test cases, limitations, owner, and validation evidence. Missing data is a blocker, not a reason to invent field names or results.

## Related project references
- [Lab telemetry pipeline](../lab-environment/deployment/telemetry-pipeline.md)
- [Lab dependency map](../curriculum/lab-dependency-map.md)
- [ATT&CK coverage plan](../curriculum/attack-coverage-plan.md)
- [Technical quality standard](../governance/quality-standards/technical-quality.md)
