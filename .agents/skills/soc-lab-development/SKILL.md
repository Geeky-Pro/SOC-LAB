---
name: soc-lab-development
description: Design or revise safe, reproducible, hands-on SOC lab exercises with prerequisites, topology, ordered steps, expected evidence, troubleshooting, cleanup, and validation criteria.
---

# SOC Lab Development

## Purpose

Produce practical exercises learners can deploy and complete in the documented SOC-LAB environment with observable, assessable outcomes.

## Before starting

- Read `AGENTS.md`, Project Charter, lab architecture, VM inventory, network plan, lab quality standard, safety policy, and target module outcomes.
- Inspect existing lab guides and canonical templates.
- Confirm lab baseline and documented versions. Do not infer unrecorded IP addresses, ports, credentials, or component behavior.
- Confirm authorized scope and whether the activity is safe for a student-run isolated environment.

## Method

1. Define purpose, learning outcomes, learner level, duration, and completion evidence.
2. Specify environment state, VM roles, network zones, prerequisites, permissions, versions, and resource requirements.
3. Describe relevant topology, trust boundaries, data flows, and required firewall access.
4. Prepare snapshots/backups and starting state where needed.
5. Write numbered, copyable steps with expected output or verification at meaningful checkpoints.
6. Explain the underlying security concept and analyst interpretation, not just commands.
7. Define student tasks, questions, and expected evidence.
8. Put instructor hints, expected answers, and reset guidance in instructor material.
9. Add troubleshooting, cleanup, recovery, and rollback.
10. Define validation cases and record what was actually executed versus only documented.

## Safety requirements

- Keep simulations inside the authorized isolated lab.
- Document scope, prerequisites, expected impact, and cleanup for disruptive actions.
- Do not provide instructions for unauthorized external targets.
- Never include secrets, real credentials, malware binaries, or sensitive student data.
- Avoid destructive changes unless they are necessary, isolated, recoverable, and explicitly documented.

## Required outputs

As applicable:
- Student lab guide
- Instructor guide/answer key
- Topology/configuration references
- Expected logs and evidence checklist
- Troubleshooting and reset/rollback guidance
- Validation checklist and evidence record

## Quality checks

- Steps are complete, ordered, and reproducible from the stated starting state.
- Each major step has a verification point.
- Expected evidence is specific enough to assess.
- Network and data-flow assumptions match the approved architecture.
- Cleanup restores a known-good state.
- Validation claims match the evidence available.

## Handoff

State the environment/version assumptions, changed paths, checks actually performed, untested procedures, risks, and owner decisions. Submit for independent review; do not self-approve.
