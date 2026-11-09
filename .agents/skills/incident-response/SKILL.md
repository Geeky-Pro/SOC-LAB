---
name: soc-incident-response
description: Design, document, and review vendor-neutral SOC incident response frameworks, triage procedures, severity models, response playbooks, evidence records, escalation workflows, and safe lab exercises aligned with NIST CSF 2.0 and NIST SP 800-61r3.
---

# SOC Incident Response Skill

## Use this skill when
Creating or revising incident response guidance, triage workflows, incident classification, response playbooks, evidence records, escalation procedures, or incident response learning activities.

## Required context
Before authoring, inspect:
- `AGENTS.md`, `governance/project-charter.md`, and relevant governance policies.
- `incident-response/README.md` and the relevant shared procedure.
- `governance/quality-standards/`.
- The target module README, learning outcomes, scenario, and lab dependencies.
- `lab-environment/` documentation when lab actions or telemetry are involved.
- Canonical templates in `incident-response/templates/` and `templates/`.

Use NIST SP 800-61 Rev. 3 (2025) and CSF 2.0 as the current conceptual baseline. Verify authoritative references before adding version-sensitive claims. Do not treat SP 800-61 Rev. 2 as the current edition.

## Workflow
1. Define the learning or operational objective, audience, scope, and assumptions.
2. Distinguish events, alerts, investigations, suspected incidents, and confirmed incidents.
3. Define roles, decision authority, escalation, and communication boundaries.
4. Design triage and severity criteria using impact, scope, urgency, exposure, and evidence confidence.
5. Document response options with operational impact, approvals, rollback, and residual risk.
6. Specify evidence provenance, timestamps, access restrictions, and recordkeeping.
7. Define recovery checks, monitoring, closure criteria, and improvement actions.
8. Use the canonical templates; keep shared guidance here and scenario-specific playbooks inside the relevant module.
9. Keep vendor-specific steps separate and only document capabilities verified in the current lab.
10. Request independent Quality Reviewer assessment and route approval to the Project Owner.

## Non-negotiable rules
- Analysts recommend actions; they do not automatically possess authority to isolate systems, disable accounts, delete artifacts, notify external parties, or restore services.
- Potentially disruptive lab actions require instructor authorization, explicit scope, impact assessment, and reset/rollback instructions.
- Never claim an incident, containment action, recovery, evidence integrity check, tabletop, or lab exercise was completed unless the record supports it.
- Do not assume EDR, SOAR, Splunk Enterprise Security, response automation, or unverified telemetry exists in the current baseline.
- Do not invent index names, sourcetypes, field names, retention, or logging coverage.
- Keep legal, privacy, regulatory, and external notification decisions with designated qualified authorities.
- This skill is not a digital forensics or memory forensics procedure.
- Never mark material approved or released without explicit Project Owner authorization.

## Deliverable handoff
Report files changed, assumptions, source references, authority boundaries, safety controls, validation performed, evidence, limitations, unresolved decisions, and required independent review.
