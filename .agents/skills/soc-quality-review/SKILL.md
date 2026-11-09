---
name: soc-quality-review
description: Independently review SOC-LAB curriculum, lectures, labs, scenarios, detections, and documentation against technical, safety, reproducibility, instructional, and repository standards.
---

# SOC Quality Review

## Purpose

Provide a disciplined, independent assessment that helps the Project Owner decide whether a learning asset is ready for acceptance.

## Before starting

- Read `AGENTS.md`, Project Charter, relevant architecture, policies, target-specific instructions, and applicable quality standards.
- Identify the exact artifact, review scope, intended audience, and acceptance criteria.
- Inspect the full artifact and its dependencies; do not rely only on an author summary.

## Method

1. Check that purpose, audience, prerequisites, outcomes, and scope are explicit.
2. Verify technical claims against authoritative references where feasible.
3. Check versions, assumptions, compatibility, and documented limitations.
4. Evaluate safety, authorization boundaries, impact, cleanup, and recovery.
5. Evaluate reproducibility, expected evidence, and troubleshooting.
6. Evaluate instructional sequencing, clarity, cognitive load, and assessment alignment.
7. Check instructor/student separation and completeness.
8. Check repository placement, naming, links, consistency, licensing, privacy, and secrets.
9. Run available static checks and link checks when tools permit; record scope and results.
10. Distinguish static review from lab execution and independent reproduction.
11. Report findings with evidence, severity, impact, and required action.

## Status definitions

Use exactly one:
- `PASS`: no blocking findings within the stated review scope.
- `PASS WITH NOTES`: no blocking findings; minor issues or limitations remain.
- `NEEDS REVISION`: material findings require correction.
- `BLOCKED`: essential inputs, dependencies, or access are missing.
- `NOT VALIDATED`: evidence is insufficient to conclude key requirements are met.

These statuses are review outcomes, not Project Owner approval.

## Finding severity

- Critical: unsafe, materially false, or likely to cause severe operational harm.
- High: major technical, reproducibility, or instructional defect.
- Medium: meaningful gap that reduces correctness or learning effectiveness.
- Low: minor clarity, consistency, or presentation issue.

Each finding must identify a file/section, evidence, impact, and actionable correction.

## Required report

Use the review report structure defined in `.github/agents/soc-lab-quality-reviewer.agent.md`. Include:
- Overall status and scope
- Summary and findings
- Acceptance checklist
- Validation evidence
- Explicitly unvalidated items
- Recommended next action

## Independence rules

- Do not silently rewrite the reviewed artifact.
- Do not approve your own modifications.
- Do not infer practical testing from documentation quality.
- Do not upgrade validation status without new evidence.
- Re-review revisions and identify resolved, unresolved, and un-rechecked findings separately.
