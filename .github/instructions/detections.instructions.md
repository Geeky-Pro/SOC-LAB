# Detection Engineering Instructions

These instructions apply to detection specifications, SPL searches, source catalogs, ATT&CK mappings, and detection validation records.

## Before authoring
- Read `detection-engineering/README.md` and the relevant standards.
- Inspect the telemetry pipeline and source catalog.
- Confirm the relevant module scenario and intended analyst outcome.
- Use the canonical detection or test-case template.

## Required quality
- Define an observable behavior and bounded scope.
- Verify index, sourcetype, fields, timestamp semantics, and data readiness from sanitized events.
- Use readable, bounded SPL compatible with the declared Splunk Enterprise version.
- Document trigger logic, expected output, false positives, triage, limitations, and test cases.
- Use evidence-grounded ATT&CK mappings and record the framework release.
- Separate planned, drafted, reviewed, approved, implemented, and validated states.

## Validation integrity
Never fabricate events, field names, test output, screenshots, source readiness, or execution status. If the environment is unavailable, mark runtime validation as NOT RUN or BLOCKED and explain the missing prerequisite. A passing document review is not a runtime validation.

## Safety
Use synthetic data and benign test events within the isolated authorized lab. Never run tests against production or external targets without explicit authorization. Record scope, impact, cleanup, and recovery.
