---
name: soc-detection-engineering
description: Design, document, review, and validate behavior-based SOC detections and reusable Splunk SPL searches using verified telemetry, explicit lifecycle states, evidence-based MITRE ATT&CK mappings, and safe lab testing.
---

# SOC Detection Engineering Skill

## Use this skill when
Creating or changing detection specifications, Splunk SPL detections, reusable investigation searches, source-readiness records, ATT&CK mappings, or detection validation evidence.

## Required context
Before authoring, inspect:
- `AGENTS.md` and relevant governance policies.
- `detection-engineering/README.md` and applicable standards.
- `lab-environment/deployment/telemetry-pipeline.md`.
- `detection-engineering/data-sources/source-catalog.md`.
- Relevant module scenario and learning outcomes.
- Canonical templates in `detection-engineering/templates/`.

## Workflow
1. Define the observable behavior and analyst question.
2. Confirm telemetry source readiness and inspect sanitized representative events.
3. Verify index, sourcetype, event-time field, and required fields; never invent schema.
4. Create the specification using the canonical template.
5. Author bounded, readable SPL compatible with the declared Splunk Enterprise version.
6. Document expected output, false positives, triage, limitations, and performance considerations.
7. Map to MITRE ATT&CK only when the behavior and current technique definition support it; record release/version.
8. Create positive, negative, and relevant boundary/data-quality test cases.
9. Run static review and, only when an environment is available, runtime tests. Record exact evidence and scope.
10. Request independent Quality Reviewer review and route approval to the Project Owner.

## Non-negotiable rules
- Current SIEM baseline is Splunk Enterprise only; do not require Splunk Enterprise Security features.
- A written SPL query is not a validated detection.
- Never fabricate sample events, fields, test output, or validation evidence.
- Keep shared detections in `detection-engineering/rules/`; module-specific logic stays with the module.
- Use safe, authorized, isolated test activity and synthetic data.
- Separate ATT&CK scenario coverage, telemetry visibility, detection availability, and validation.
- Never mark content approved or released without explicit Project Owner authorization.

## Deliverable handoff
Report changed files, detection IDs, assumptions, data dependencies, review status, tests actually run, evidence references, limitations, and unresolved decisions.
