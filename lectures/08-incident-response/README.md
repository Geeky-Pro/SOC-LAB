# Incident Response

> **Status:** draft — pending module design and Project Owner approval  
> **Module ID:** 08-incident-response  
> **Curriculum version:** 0.1

## Purpose
Develop the judgment and operational discipline required to assess, scope, coordinate, contain, remediate, recover from, and document cybersecurity incidents.

## Target audience
Learners following the SOC-LAB program. Final entry level and prerequisites remain to be confirmed.

## Proposed learning outcomes
By the end of this module, learners should be able to:
- Distinguish events, alerts, investigations, suspected incidents, and confirmed incidents.
- Validate an incident hypothesis using corroborated evidence and identify important unknowns.
- Classify an incident and justify a provisional severity based on impact, scope, urgency, exposure, and confidence.
- Build an incident timeline and maintain traceable evidence references.
- Recommend proportionate containment and recovery options, including operational trade-offs and approval requirements.
- Communicate status, escalate appropriately, and document decisions and lessons learned.

These outcomes are preliminary and require measurable criteria and mapping to lessons and assessments.

## Prerequisites
[To be finalized against `curriculum/prerequisite-map.md`. Likely dependencies include SOC fundamentals, endpoint investigation, network monitoring, and web security investigation.]

## Proposed topic sequence
1. Incident response purpose, terminology, and governance.
2. NIST CSF 2.0 and SP 800-61 Rev. 3 conceptual model.
3. Incident intake, validation, triage, and severity.
4. Investigation scope, evidence provenance, and incident timeline.
5. Decision authority, escalation, and communications.
6. Containment strategy and operational trade-offs.
7. Eradication, remediation, recovery, and monitoring.
8. Closure, lessons learned, and tabletop exercise.

Sequence and depth remain subject to curriculum review.

## Shared response guidance
Use the reusable procedures in [incident-response/](../../incident-response/README.md):
- Framework and incident lifecycle
- Classification and severity
- Triage procedures
- Containment, eradication, and recovery
- Evidence and recordkeeping
- Communications and escalation
- Playbook standard and templates

## Practical activities
[To be designed. Exercises must remain inside the authorized isolated lab. Students should recommend disruptive actions; the instructor controls whether any action is actually executed.]

## Assessment
Map assessments to the proposed outcomes and the program assessment framework. Include evidence-based triage, severity rationale, decision log, incident record, and recovery/closure reasoning.

## Dependencies
- Relevant prior module outcomes and investigation skills.
- Verified Windows/Sysmon, Splunk Enterprise, pfSense/Suricata, network, and web telemetry.
- Lab reset and recovery documentation.
- Shared incident response procedures.

Do not assume that telemetry or response controls are available until verified in the deployed lab.

## References
- NIST SP 800-61 Rev. 3 (April 2025): https://doi.org/10.6028/NIST.SP.800-61r3
- NIST Incident Response project: https://csrc.nist.gov/projects/incident-response
- CISA Federal Government Cybersecurity Incident and Vulnerability Response Playbooks: https://www.cisa.gov/resources-tools/resources/federal-government-cybersecurity-incident-and-vulnerability-response-playbooks

## Validation and review
- Technical validation: not validated
- Instructional review: not reviewed
- Lab execution: not executed
- Open decisions: final prerequisites, lesson breakdown, practical scenarios, assessment rubric, and exercise authority.

## Change history
| Version | Date | Change | Status |
|---|---|---|---|
| 0.1 | 2026-11-10 | Initial module charter | Draft |
