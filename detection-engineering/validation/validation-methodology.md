# Detection Validation Methodology

> **Status:** draft methodology; no detections have been validated by this document.

## 1. Validation objective
Establish whether a detection identifies its documented behavior under a defined set of lab conditions, while avoiding expected benign activity and identifying data-quality blind spots.

## 2. Test dimensions
For each detection, select applicable tests:

| Test type | Question |
|---|---|
| Positive | Does the documented behavior produce the expected detection result? |
| Negative | Does representative benign behavior avoid an alert? |
| Boundary | What happens at threshold, time-window, and sequence boundaries? |
| Data quality | What happens when fields are null, delayed, duplicated, or malformed? |
| Coverage | Which variants or paths are visible, and which are not? |
| Performance | Does the search complete within acceptable resource/time bounds? |
| Recovery | Does the detection resume correctly after source interruption or configuration repair? |

## 3. Safe test procedure
1. Confirm isolated lab scope, target, authorization, snapshot, and cleanup plan.
2. Confirm source health and time synchronization.
3. Record build versions, detection revision, SPL, indexes, sourcetypes, and search window.
4. Generate a benign, documented test event or use a safe test fixture.
5. Preserve source event evidence and the exact search output.
6. Run relevant negative/boundary tests.
7. Record observed result against expected result.
8. Tune only with a documented rationale; rerun impacted tests.
9. Remove temporary artifacts and restore the baseline when required.

Never use live malware or unapproved external targets for routine validation. Follow the repository safety policy and the exercise-specific authorization boundaries.

## 4. Evidence package
A validation record should include:
- Detection ID and version.
- Lab build identifier and component versions.
- Test case IDs, test time, operator, and scope.
- Source event references or sanitized event excerpts.
- Exact SPL and search time range.
- Expected and observed results.
- Screenshots or exports with sensitive information removed.
- False-positive observations and blind spots.
- Search runtime/resource notes when relevant.
- Final result and limitations.

## 5. Result vocabulary
- `PASS`: all required tests for the stated scope passed.
- `PASS WITH NOTES`: required tests passed with documented limitations.
- `FAIL`: one or more required tests did not meet expectations.
- `BLOCKED`: prerequisites or telemetry were unavailable.
- `NOT RUN`: no execution evidence exists.

## 6. Coverage claims
Use bounded language such as “validated for Sysmon configuration X on lab build Y using test cases A–C.” Do not claim complete ATT&CK coverage, production readiness, or universal detection based on a small lab test.
