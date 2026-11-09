# SPL Style Guide

> **Status:** draft conventions for Splunk Enterprise searches.

## General rules
1. Use SPL supported by the declared Splunk Enterprise version; record the version used for validation.
2. Specify the intended index and sourcetype where known. Do not use unrestricted `index=*` in reusable detections.
3. Define a bounded time range and state whether it uses event time or ingestion time.
4. Use field names confirmed by the source catalog and sample events. Never guess field names.
5. Filter early on selective, relevant fields; avoid unnecessary `join`, `transaction`, broad regex, and high-cardinality operations.
6. Keep searches readable with one pipeline stage per line and comments for non-obvious logic.
7. Preserve useful original fields. Rename only when it improves clarity and document aliases.
8. Handle missing fields explicitly; do not silently interpret missing telemetry as a negative result.
9. Avoid hard-coded student-specific IPs, usernames, or hostnames. Use documented tokens or configuration where appropriate.
10. Return analyst-useful columns and a meaningful sort order.

## Reusable search layout
Use this as a formatting pattern, not as a runnable detection. Replace every placeholder with verified values before use.

```spl
index=<verified_index> sourcetype=<verified_sourcetype> earliest=<bounded_start> latest=<bounded_end>
| <verified_filter_or_transform>
| <documented_detection_logic>
| table _time host <verified_required_fields>
| sort 0 - _time
```

## Detection-specific requirements
- Document the trigger condition and any threshold/window semantics in prose.
- State whether duplicate events can inflate counts.
- Explain null handling and field normalization.
- If using `stats`, `eventstats`, `streamstats`, or `bin`, document why and how the result affects detection.
- If using lookups, document the lookup name, schema, update process, and failure behavior.
- If using macros, document their definitions and dependencies; do not assume they exist in a clean lab.
- Use `tstats` only when the required data model and acceleration are configured and verified; otherwise provide a tested event-search alternative when feasible.

## Performance and correctness checks
- Run against a bounded representative time range.
- Compare raw events with transformed results.
- Check missing, duplicated, delayed, and out-of-order events.
- Confirm the output is stable under expected event-volume changes.
- Record search runtime and resource impact when material.
- Never label SPL as tested unless it was executed on the stated Splunk build and data.
