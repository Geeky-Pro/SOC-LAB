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
- Canonical templates live in `templates/`. Do not create competing copies.
- Reusable agent skills belong in `.agents/skills/`; provider-specific agent definitions and Copilot instructions belong in `.github/`.
- Historical assets remain in `Archive/` until reviewed and deliberately promoted.

## Authoring rules

- Use English `kebab-case` for paths and filenames.
- Keep technical concepts vendor-neutral where possible; document tool-specific implementation separately.
- Align learning content with measurable outcomes and assessments.
- Identify prerequisites, versions, assumptions, limitations, expected evidence, troubleshooting, cleanup, and rollback as applicable.
- Cite authoritative sources for technical and version-sensitive claims.
- Distinguish documented, simulated, executed, tested, and independently validated states.
- Never fabricate test results, source citations, tool versions, or lab outcomes.
- Keep attack simulations within the authorized isolated lab and document scope and impact.
- Do not commit secrets, private information, malware samples, or unlicensed content.

## Agent workflow

- Use `.github/agents/soc-lab-content-engineer.agent.md` for drafting and content maintenance.
- Use `.github/agents/soc-lab-quality-reviewer.agent.md` for independent review.
- The Content Engineer must not self-approve.
- The Quality Reviewer reports findings and a review status; it does not grant release approval.
- The Project Owner decides acceptance, scope changes, and release.
- Use prompts in `.github/prompts/` as task starters, adapting them to the actual request.
- Skills in `.agents/skills/` are reusable procedures. Read a skill's `SKILL.md` when its task applies; do not duplicate its full method in prompts or agent definitions.

## Change discipline

Make focused changes. Inspect before editing. Preserve history. Validate links, formatting, and structure where possible. Report changed files, evidence, limitations, and decisions needed. Never merge or release without explicit authorization.
