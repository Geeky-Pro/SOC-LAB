# Detection Rule Standard

> **Status:** draft standard.

## 1. Purpose and scope
A detection is a documented analytic that identifies a defined, observable behavior from specified telemetry. It is not simply a search that returns events. Every detection must support an analyst decision or a measurable learning objective.

## 2. Required specification
Each detection specification must include:

| Field | Requirement |
|---|---|
| Detection ID | Stable unique identifier, e.g. `SOC-DET-001` |
| Name / summary | Clear behavior-oriented title and concise description |
| Status / version | Lifecycle state and semantic revision |
| Objective | What analyst capability or security question it supports |
| Behavior | Observable behavior; avoid unsupported intent claims |
| Data dependencies | Source, index, sourcetype, required fields, collection prerequisites |
| SPL | Complete query with time window and field assumptions |
| Expected result | What a positive test should produce; do not fabricate sample events |
| False positives | Known benign causes and contextual checks |
| Triage | Ordered analyst steps, pivots, evidence to preserve |
| Severity rationale | Impact and confidence factors; explain rather than assign arbitrarily |
| ATT&CK mapping | Technique ID/name, behavior evidence, ATT&CK release; omit if unsupported |
| Test cases | Positive, negative, edge, and data-quality tests as appropriate |
| Tuning | Exclusions/suppressions with rationale and expiry/review plan |
| Limitations | Visibility gaps, bypasses, dependencies, and known blind spots |
| References | Authoritative sources and internal source documentation |
| Ownership | Author, reviewer, approver, last reviewed date |

## 3. Detection quality principles
- Detect behavior, not merely a filename, tool name, or indicator in isolation, unless that indicator is the explicit objective.
- Prefer multiple relevant signals and contextual enrichment when the telemetry supports them.
- Distinguish observed facts from analyst hypotheses.
- Avoid brittle assumptions about hostnames, usernames, paths, localized strings, or event ordering.
- State the time window and event-time field assumptions.
- Avoid broad wildcards and unnecessary expensive commands; test search performance with representative data.
- Do not hide uncertainty by using overly strong alert names or descriptions.
- Document whether the logic is event-based, threshold-based, sequence-based, or correlation-based.

## 4. Acceptance criteria
A detection can move to `in-review` only when required fields are complete and SPL syntax has been checked against the declared data model. It may move to `implemented` only after it is installed in the intended environment. It may move to `validated` only when positive and relevant negative tests have recorded reproducible evidence, data source versions, time range, and result.

A static review cannot establish runtime validation. A single positive test does not prove broad coverage. Every validation statement must name its scope.

## 5. Safety and privacy
Use benign test events and synthetic identities. Do not include real credentials, personal data, malware, or sensitive production telemetry. Any emulation must follow the isolated-lab safety policy and have explicit scope and cleanup.

## 6. Change control
Changes to SPL, required fields, thresholds, exclusions, data dependencies, severity, or ATT&CK mapping require a version increment and a note explaining impact. Re-run affected test cases after material changes.
