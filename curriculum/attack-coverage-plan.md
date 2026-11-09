# MITRE ATT&CK Coverage Plan

> **Status:** draft — mapping methodology, not a completed technique catalog

## Purpose
Use MITRE ATT&CK as a shared vocabulary for adversary behaviors represented in SOC-LAB scenarios and detections. Mappings must support investigation and learning, not decoration.

## Mapping rules
- Map only behavior actually represented by a scenario or evidence.
- Record the technique/sub-technique and the behavior supporting the mapping.
- Distinguish planned, simulated, executed, and captured behavior.
- Record the ATT&CK release/version when maintaining detailed mappings.
- Do not claim detection merely because a technique appears in a scenario.
- Separate scenario coverage, telemetry visibility, detection logic, and successful validation.
- Do not force a mapping when the observed behavior is too generic or ambiguous.

## Coverage dimensions

| Dimension | Question |
|---|---|
| Scenario | Is the behavior represented? |
| Telemetry | Which source can observe it? |
| Detection | Is a rule/search/analytic available? |
| Validation | Was behavior executed and detection tested? |
| Investigation | Can learners interpret and correlate the evidence? |

## Candidate learning themes
Suspicious process execution, script/interpreter activity, persistence indicators, credential-access signals, command-and-control-like network patterns, and web exploitation indicators may be considered where supported by the isolated lab. These are candidates, not approved technique mappings.

## Locations and ownership
- Scenario-specific mappings belong with module scenarios.
- Shared detection specifications and validation records belong in [detection-engineering](../detection-engineering/README.md).
- Source readiness and field assumptions belong in detection-engineering/data-sources/.
- Shared validation methodology belongs in detection-engineering/validation/.

## Release criteria
Each published mapping must include technique identifier/name, supporting scenario behavior, evidence source, ATT&CK version, and an accurate validation state. Report scenario coverage, telemetry visibility, detection availability, and validation separately.
