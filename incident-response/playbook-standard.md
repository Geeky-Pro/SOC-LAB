# Incident Response Playbook Standard

> **Status:** draft  
> **Validation:** NOT VALIDATED

## 1. Purpose

A playbook turns an approved procedure into a scenario- or threat-specific set of actionable tasks. It must be usable under time pressure, explicit about authority, and honest about prerequisites and limitations.

## 2. Required sections

Every playbook should include:
1. Title, unique ID, owner, version, status, reviewer, and review date.
2. Purpose, trigger, scope, exclusions, and intended audience.
3. Prerequisites, dependencies, contacts/roles, and decision authority.
4. Initial validation questions and severity/escalation criteria.
5. Evidence sources and data-readiness assumptions.
6. Ordered tasks with owner, decision point, expected output, and stop condition.
7. Containment options, approvals, impact, and rollback.
8. Eradication/remediation considerations.
9. Recovery checks and monitoring criteria.
10. Communications and documentation requirements.
11. Closure criteria and lessons-learned actions.
12. Safety boundaries, cleanup/reset, and references.
13. Validation record: tabletop, lab execution, technical checks, and independent review.

## 3. Task format

Each task should state:
- **Action:** what the role should do.
- **Purpose:** why it matters.
- **Inputs:** required evidence or authority.
- **Owner:** responsible role.
- **Decision:** criteria and who decides.
- **Output:** record, evidence, or state change.
- **Stop/escalate:** when not to proceed.
- **Validation:** how the outcome will be verified.

Avoid vague instructions such as "investigate thoroughly" or "clean the host."

## 4. Design requirements

- Be vendor-neutral in the response logic; place tool-specific implementation in a clearly marked appendix or linked lab guide.
- Never assume fields, indexes, products, automation, or access that have not been verified.
- Include positive, negative, and ambiguous decision paths.
- Consider false positives, business impact, and alternate explanations.
- Make disruptive actions approval-gated and reversible where feasible.
- Keep student-facing tasks separate from instructor-only answers and inject schedules.
- Do not expose real secrets, sensitive evidence, or unsafe operational details.
- Use scenario-specific evidence and ATT&CK mappings only when supported by behavior.

## 5. Validation levels

Record each independently:
- **Document review:** completeness, clarity, and consistency.
- **Tabletop exercise:** discussion-based walkthrough; no system changes implied.
- **Lab execution:** tasks actually performed in the isolated lab with date and evidence.
- **Technical validation:** specific controls, searches, or configurations tested.
- **Independent review:** findings from a reviewer other than the author.

A tabletop is not a live test. A document review is not proof of technical effectiveness.

## 6. Ownership and release

The Content Engineer drafts. The Quality Reviewer reviews independently. The Project Owner approves intended use and release. Do not label a playbook approved or released without explicit authorization.
