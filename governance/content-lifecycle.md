# Content Lifecycle

## Status values

| Status | Meaning |
|---|---|
| `planned` | Accepted for future development; content is not yet drafted. |
| `draft` | Work in progress; not ready for learner use. |
| `in-review` | Submitted for independent review. |
| `approved` | Reviewed and accepted by the Project Owner for intended use. |
| `released` | Included in a published course or repository release. |
| `deprecated` | Retained for reference but no longer recommended for current delivery. |

## Typical flow

`planned` → `draft` → `in-review` → `approved` → `released`

A rejected draft returns to `draft` with actionable review findings. Approved content may be revised through a new review cycle.

## Validation is separate from status

Content status does not prove practical execution. Record validation independently:

- `NOT VALIDATED`: no practical validation evidence is available.
- `PASS`: the defined checks passed with evidence.
- `PASS WITH NOTES`: checks passed with documented limitations.
- `NEEDS REVISION`: one or more required checks failed.
- `BLOCKED`: validation could not be completed because of a dependency or access issue.

## Required traceability

For significant content, record owner, reviewer, review date, source references, applicable versions, validation evidence, and known limitations.


## Language and translation status

Track language status separately from content lifecycle:
- `not-started`: no counterpart exists.
- `draft`: counterpart is being authored.
- `in-review`: language and parity review is in progress.
- `synchronized`: a documented parity check found the pair equivalent within scope.
- `needs-update`: source changes may have made the counterpart stale.

A synchronized pair is not necessarily approved, released, or practically validated. Record counterpart paths, content version, review date, and reviewer where appropriate.
