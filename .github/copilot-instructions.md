# SOC-LAB Copilot Instructions

These instructions apply to GitHub Copilot throughout this repository. They complement, and do not replace, the root `AGENTS.md`.

## First read
Before making substantive changes, inspect:
1. `AGENTS.md`
2. `governance/project-charter.md`
3. Relevant repository/module architecture and policies
4. Applicable quality standards
5. The target module's README and existing files, if present

## Project context
SOC-LAB is an instructor-led, hands-on SOC learning program. The curriculum is organized around 11 capability-based units, from SOC fundamentals through an integrated investigation and capstone. Module titles describe competencies, not vendor products.

Current lab baseline:
- VMware Workstation
- Splunk Enterprise only
- pfSense with integrated Suricata
- Windows endpoint with Sysmon
- Kali Linux on `10.0.90.0/24`
- Ubuntu web server in a segmented DMZ
- Mailpit may support local email exercises

Do not silently substitute Splunk ES, Wazuh, standalone Suricata, or any other optional component for the current baseline.

## Source of truth and file placement
- Follow `governance/architecture/repository-architecture.md` and `governance/architecture/module-architecture.md`.
- Shared lab infrastructure belongs in `lab-environment/`; module-specific exercises belong in `lectures/<module>/`.
- Shared detection standards and reusable detections belong in `detection-engineering/`; module-specific detections stay with the module.
- Shared response procedures belong in `incident-response/`; scenario-specific playbooks stay with the relevant module.
- Canonical general templates live in `templates/`; detection specifications and test-record templates live in `detection-engineering/templates/`; incident response templates live in `incident-response/templates/`.
- Reusable agent skills belong in `.agents/skills/`; provider-specific agent definitions and Copilot instructions belong in `.github/`.
- Historical assets remain in `Archive/` until reviewed and deliberately promoted.

## Authoring rules
- Treat Arabic and English as first-class project languages.
- Use English `kebab-case` paths; Arabic counterparts append `-ar` before the extension.
- Read `governance/policies/bilingual-content-policy.md` before substantive bilingual authoring.
- Update paired variants together where practical; otherwise disclose the pending counterpart.
- Preserve stable IDs, commands, code, SPL, field names, configuration keys, IPs, product names, and standards identifiers.
- Review technical equivalence and instructional clarity, not literal translation symmetry.
- Keep technical concepts vendor-neutral where possible; document tool-specific implementation separately.
- Align learning content with measurable outcomes and assessments.
- Identify prerequisites, versions, assumptions, limitations, expected evidence, troubleshooting, cleanup, and rollback as applicable.
- Cite authoritative sources for technical and version-sensitive claims.
- Distinguish documented, simulated, executed, tested, and independently validated states.
- Never fabricate test results, source citations, tool versions, or lab outcomes.
- Keep attack simulations within the authorized isolated lab and document scope and impact.
- Do not commit secrets, private information, malware samples, or unlicensed content.

## Detection engineering rules
- Current SIEM baseline is Splunk Enterprise only; do not require Splunk Enterprise Security features.
- Verify index, sourcetype, field names, event-time semantics, and source readiness against sanitized observed events. Never invent schema.
- Document observable behavior, SPL assumptions, false positives, triage, limitations, and test cases.
- Separate detection specification, Project Owner approval, implementation, and runtime validation.
- Map to MITRE ATT&CK only when supported by behavior evidence and record the framework release/version.
- A query that has not been executed is not a validated detection. Record the exact environment and tests actually run.
- Follow `detection-engineering/standards/` and `.github/instructions/detections.instructions.md`.

## Incident response rules
- Use NIST CSF 2.0 and NIST SP 800-61 Rev. 3 (2025) as the current conceptual baseline; do not present Rev. 2 as current.
- Treat repository severity levels as educational proposals, not production policy or universal SLAs.
- Distinguish events, alerts, investigations, suspected incidents, and confirmed incidents.
- State response roles, decision authority, escalation, and communication boundaries explicitly.
- Separate observed facts, hypotheses, unknowns, and conclusions; preserve evidence provenance and timestamps.
- Gate disruptive actions behind explicit authority and document impact, rollback, and lab reset.
- Do not assume EDR, SOAR, automated response, Splunk Enterprise Security, or unverified lab capabilities.
- Keep legal, privacy, regulatory, and external notification decisions with qualified authorized personnel.
- Follow `incident-response/` and `.github/instructions/incident-response.instructions.md`.

## Bilingual quality checks
- Compare paired variants for omitted steps, changed scope, mismatched evidence, inconsistent safety controls, and assessment drift.
- Retain canonical English technical terms with Arabic explanations where useful.
- Do not assume machine translation establishes synchronization.

## Agent workflow
- Use `.github/agents/soc-lab-content-engineer.agent.md` for drafting and content maintenance.
- Use `.github/agents/soc-lab-quality-reviewer.agent.md` for independent review.
- The Content Engineer must not self-approve.
- The Quality Reviewer reports findings and a review status; it does not grant release approval.
- The Project Owner decides acceptance, scope changes, and release.
- Use prompts in `.github/prompts/` as task starters, adapting them to the actual request.
- Skills in `.agents/skills/` are reusable procedures. Read the matching `SKILL.md` when its task applies.

## Change discipline
Make focused changes. Inspect before editing. Preserve history. Validate links, Markdown, and structure where possible. Report changed files, evidence, limitations, and decisions needed. Never merge or release without explicit authorization.
