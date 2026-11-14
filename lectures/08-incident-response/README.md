# Incident Response

[Arabic module guide](README-ar.md)

> **Status:** draft — pending independent review and Project Owner approval  
> **Module ID:** 08-incident-response  
> **Curriculum version:** 0.1  
> **Learning package version:** 0.2

## Purpose

Develop the judgment and operational discipline required to assess, scope, coordinate, contain, remediate, recover from, and document cybersecurity incidents.

## Audience and prerequisites

Learners following SOC-LAB. Proposed prerequisites come from SOC fundamentals, lab operations, endpoint investigation, network monitoring, intrusion detection, and web security investigation. Confirm readiness against the curriculum prerequisite map.

## Measurable learning outcomes

See [Learning Outcomes](learning-outcomes.md). Six canonical outcomes (LO-08-01 through LO-08-06) cover incident classification, hypothesis validation, severity/priority, evidence timelines, response options, communications, incident records, and measurable improvement.

## Lesson sequence

See [Lesson Plan](lesson-plan.md) for the proposed 8-hour (480-minute) sequence, including the 120-minute tabletop and debrief. Timing is provisional.

1. L08-01 — Incident response foundations, terminology, and authority.
2. L08-02 — Incident intake, triage, and severity.
3. L08-03 — Investigation scope, evidence, and timeline.
4. L08-04 — Containment, eradication, recovery, and verification.
5. L08-05 — Escalation, communications, closure, and improvement.
6. L08-06 — Suspicious Web Server Compromise tabletop.

## Practical scenario

The first tabletop is [Suspicious Web Server Activity — Student Brief](scenarios/student-brief.md). The public [Tabletop Master](scenarios/tabletop-suspicious-web-server-compromise.md) contains the inject sequence and facilitator prompts. Because this repository is public, students may be able to read it; use an access-controlled private version if inject concealment is required.

The exercise is discussion-based by default. Use synthetic evidence unless the instructor supplies verified, sanitized lab telemetry. Do not assert successful compromise, exfiltration, or persistence without supporting evidence.

## Learning materials

[Arabic learning package](README-ar.md)

- [Student Guide](student/student-guide.md)
- [Instructor Guide](instructor/instructor-guide.md)
- [Assessment](assessments/incident-response-assessment.md)
- [Learning Outcomes](learning-outcomes.md)
- [Lesson Plan](lesson-plan.md)

## Shared response guidance

Use the reusable procedures in [incident-response](../../incident-response/README.md): framework, classification/severity, lifecycle, triage, containment/eradication/recovery, evidence, communications/escalation, and playbook standards.

## Lab and telemetry dependencies

Potential sources include Windows/Sysmon, Splunk Enterprise, pfSense/Suricata, Ubuntu web-server logs, and optional packet-capture metadata. Verify availability, field names, indexes, sourcetypes, export paths, and time semantics before publishing tool-specific steps. Do not assume EDR, SOAR, Splunk Enterprise Security, or automated response.

## Safety boundaries

Students analyze evidence and recommend actions. The instructor controls disruptive actions such as VM isolation, firewall changes, account disablement, service restart, deletion, or restoration. Any live demonstration requires explicit scope, approval, impact assessment, rollback, and reset.

## Assessment

The proposed tabletop assessment is 100 points, with a suggested 70% pass mark subject to Project Owner approval. Safety and evidence integrity are mandatory.

## Validation and review

- Technical validation: not validated.
- Instructional review: pending.
- Tabletop delivery: not conducted.
- Lab execution: not performed.
- Independent Quality Reviewer review: pending.
- Project Owner approval: pending.

## References

- NIST SP 800-61 Rev. 3 (April 2025): https://doi.org/10.6028/NIST.SP.800-61r3
- NIST CSF 2.0: https://doi.org/10.6028/NIST.CSWP.29
- NIST Incident Response project: https://csrc.nist.gov/projects/incident-response
