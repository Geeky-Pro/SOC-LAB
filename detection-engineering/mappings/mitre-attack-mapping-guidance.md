# MITRE ATT&CK Mapping Guidance

> **Status:** draft guidance; mapping must be evidence-based.

## Mapping rules
1. Map the behavior the detection actually observes, not the suspected actor or presumed intent.
2. Record technique and sub-technique identifiers only after checking the current official ATT&CK knowledge base.
3. Include the ATT&CK release/version used.
4. Explain the exact behavior and telemetry supporting the mapping.
5. Distinguish scenario intent, behavior simulated, behavior executed, telemetry captured, analytic implemented, and analytic validated.
6. Do not map generic process execution or network traffic to a specific technique without sufficient behavioral evidence.
7. If a defensible mapping is unavailable, state “Not mapped” and explain why.

## Required mapping fields
- ATT&CK domain (Enterprise, Mobile, or ICS as applicable).
- Release/version and date checked.
- Technique ID and official name.
- Sub-technique ID/name where supported.
- Detection behavior and evidence source.
- Scenario/module reference.
- Mapping confidence and rationale.
- Validation state and linked test record.

## Coverage reporting
Report these dimensions separately:
- Scenario representation.
- Telemetry visibility.
- Detection logic availability.
- Runtime validation.
- Analyst investigation capability.

A technique appearing in a scenario does not prove that the lab can observe it or detect it. A detection mapping is not a claim of complete coverage.
