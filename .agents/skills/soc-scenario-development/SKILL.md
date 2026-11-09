---
name: soc-scenario-development
description: Create SOC investigation scenarios, attack-emulation storylines, telemetry plans, evidence packs, analyst decision points, detection opportunities, and instructor debriefs for authorized lab environments.
---

# SOC Scenario Development

## Purpose

Create realistic but bounded scenarios that teach analysts to form hypotheses, pivot across telemetry, evaluate evidence, and make defensible response decisions.

## Before starting

- Read the module outcomes, lab architecture, scenario instructions, safety policy, detection/response standards, and existing scenarios.
- Confirm authorized environment, learner level, duration, and available telemetry sources.
- Inspect existing evidence and data schemas; do not invent event IDs, field names, logs, or tool capabilities.

## Method

1. Define scenario purpose, learning outcomes, narrative, scope, difficulty, and success criteria.
2. Establish starting conditions and the initial alert, report, or suspicious observation.
3. Design a plausible timeline with bounded actions and optional injects.
4. Map each action to observable evidence: endpoint, Sysmon, network/PCAP, pfSense/Suricata, web, email, and Splunk as relevant.
5. Specify event attributes, timestamps, source identity, and expected correlation pivots where known.
6. Create investigation questions that guide reasoning without revealing the answer.
7. Define expected hypotheses, evidence interpretation, alternative explanations, and confidence.
8. Identify detection opportunities and response decisions, including containment trade-offs.
9. Prepare instructor hints, answer key, debrief, and cleanup/reset steps.
10. Map ATT&CK techniques only where scenario behavior supports the mapping.
11. Label synthetic evidence clearly and distinguish simulated from observed real lab output.

## Required outputs

As applicable:
- Scenario brief and scope
- Timeline/inject plan
- Telemetry/evidence matrix
- Student investigation worksheet
- Instructor guide and answer key
- Detection and response notes
- Cleanup/reset and validation plan
- Debrief and assessment rubric

## Quality checks

- Every major scenario action has an expected observable trace or an explicit telemetry limitation.
- Evidence supports the intended conclusions; ambiguity is deliberate and explainable.
- Student questions assess reasoning, not command memorization.
- The scenario is safe and bounded to the authorized lab.
- Response choices are operationally plausible.
- ATT&CK mappings are justified rather than decorative.
- Evidence is labeled accurately as synthetic, captured, or generated.

## Handoff

List the evidence sources, expected fields/artifacts, assumptions, safety boundaries, validation performed, and known gaps. Submit for independent review and do not claim lab execution without an execution record.
