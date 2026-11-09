# [Detection Name]

> **Status:** draft  
> **Detection ID:** SOC-DET-[NNN]  
> **Version:** 0.1  
> **Lifecycle state:** draft  
> **Owner:** [Role/person]  
> **Last reviewed:** [YYYY-MM-DD]

## Summary
[Describe the observable behavior and why it matters.]

## Objective
[Define the analyst question or learning outcome.]

## Behavior and scope
- Observable behavior:
- In-scope systems:
- Out-of-scope behavior:
- Trigger model: [event / threshold / sequence / correlation]

## Data dependencies
| Source | Index | Sourcetype | Required fields | Readiness |
|---|---|---|---|---|
| [Verified source] | [Verified index] | [Verified sourcetype] | [Observed fields] | [State] |

## SPL
```spl
[Insert version-compatible SPL using verified fields and a bounded time range.]
```

## Trigger logic
[Explain filters, thresholds, grouping, time windows, null handling, and duplicate handling.]

## Expected result
[Describe expected fields and behavior. Include only sanitized, observed examples.]

## False positives and tuning
| Benign cause | How to distinguish | Tuning action | Review/expiry |
|---|---|---|---|
| [Known cause] | [Contextual check] | [Minimal change] | [Date/condition] |

## Analyst triage
1. [Validate event and source health.]
2. [Pivot to related host/user/process/network evidence.]
3. [Assess scope and impact.]
4. [Preserve evidence and follow the applicable response procedure.]

## Severity rationale
[Explain impact, confidence, and escalation factors. Avoid unsupported severity labels.]

## MITRE ATT&CK mapping
- Domain:
- Release/version:
- Technique/sub-technique:
- Behavior evidence:
- Mapping rationale:
- Mapping confidence:

## Test cases
| Test ID | Type | Preconditions | Action/fixture | Expected result | Status |
|---|---|---|---|---|---|
| [DET-NNN-T01] | Positive | [Set] | [Safe test] | [Set] | NOT RUN |
| [DET-NNN-T02] | Negative | [Set] | [Benign test] | [Set] | NOT RUN |

## Limitations and blind spots
[Document visibility gaps, alternate paths, dependencies, and assumptions.]

## References
- [Official documentation / source]

## Change history
| Version | Date | Change | Author |
|---|---|---|---|
| 0.1 | [YYYY-MM-DD] | Initial draft | [Set] |

## Validation record
- Lab build:
- Splunk Enterprise version:
- Detection revision:
- Test record:
- Result: NOT RUN
- Evidence location:
- Validator/date:
