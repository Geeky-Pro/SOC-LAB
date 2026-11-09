# Shared Investigation Searches

Store reusable analyst searches that support investigation, triage, and data-quality checks but are not necessarily alerting detections.

## Difference from detections
- **Investigation search:** helps an analyst explore evidence or answer a question.
- **Detection:** defines behavior, trigger logic, expected output, false-positive considerations, and validation requirements.

Do not describe a generic pivot or hunt query as a validated detection.

## Requirements
Every shared search should document its purpose, supported source/index/sourcetype, required fields, bounded time range, SPL version assumptions, expected output, performance considerations, and limitations. Use verified field names only.

## Index
No shared investigation searches are registered yet. Add new content only after reviewing the SPL style guide.
