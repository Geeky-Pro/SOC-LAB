# Shared Detection Rules

This directory is the index for reusable detections that apply across multiple modules or scenarios.

## Current state
No production-ready or runtime-validated shared detections are registered yet. Add a detection only after creating its specification from `../templates/detection-spec-template.md`.

## Naming and identifiers
- Use stable IDs such as `SOC-DET-001`; do not recycle retired IDs.
- Use descriptive kebab-case filenames, for example `soc-det-001-suspicious-process-pattern.md`.
- Keep SPL in the specification or a clearly linked companion file.
- Record lifecycle status and version in the document.

## Placement
Module-specific detections belong in the relevant `lectures/*/detections/` directory. If logic becomes genuinely reusable, promote it here through review rather than duplicating divergent copies.

## Index
| ID | Name | Status | Data source | Validation |
|---|---|---|---|---|
| — | No shared detections registered | — | — | — |
