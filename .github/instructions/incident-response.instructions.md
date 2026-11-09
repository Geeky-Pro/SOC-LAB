---
applyTo: "incident-response/**/*.md,lectures/**/playbooks/**/*.md,lectures/**/incident-response/**/*.md"
---

# Incident Response Content Instructions

- Read `incident-response/README.md`, relevant shared procedures, and the target module's charter before editing.
- Align the conceptual model with NIST CSF 2.0 and NIST SP 800-61 Rev. 3 (2025); do not present Rev. 2 as current.
- Distinguish events, alerts, investigations, suspected incidents, and confirmed incidents.
- Treat severity models in this repository as educational proposals, not production policy or universal SLAs.
- State roles, decision authority, escalation paths, scope, and stop conditions explicitly.
- Separate observed facts, hypotheses, unknowns, and conclusions.
- Document evidence source, collection context, timestamps/time zones, provenance, handling, and limitations.
- Gate disruptive actions behind explicit authority; include impact, rollback, and lab reset guidance.
- Do not assume EDR, SOAR, automated response, Splunk Enterprise Security, or unverified lab capabilities.
- Keep legal, privacy, regulatory, and external notification decisions with qualified authorized personnel.
- Keep shared procedures in `incident-response/`; scenario-specific playbooks and instructor/student materials stay within their module.
- Use canonical templates in `incident-response/templates/`; do not create conflicting copies.
- Distinguish document review, tabletop exercise, lab execution, technical validation, and independent review.
- Never invent execution results, evidence, approvals, or test outcomes. Preserve draft and NOT VALIDATED status until evidence and authorization exist.
