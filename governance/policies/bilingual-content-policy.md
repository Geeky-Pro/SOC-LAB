# Bilingual Content Policy

- Policy ID: SOC-LAB-POL-BILINGUAL-001
- Status: Draft
- Languages: English (en), Arabic (ar)
- Owner: Project Owner

## 1. Purpose

Arabic and English are first-class project languages. SOC-LAB maintains one curriculum and one set of learning requirements represented through paired language variants, not separate curricula.

## 2. Pairing and filenames

- English uses the canonical filename, such as `student-guide.md`.
- Arabic uses the same basename with `-ar` before the extension, such as `student-guide-ar.md`.
- Keep paired files in the same directory; do not create separate language trees.
- Use English lowercase `kebab-case` paths and filenames.
- Every substantial document links to its counterpart. If absent, state that translation is pending.

## 3. Metadata

Where useful, identify language (`en`/`ar`), counterpart path, shared content version, translation status, and last parity-review date/reviewer. Translation status is separate from content lifecycle and practical validation.

## 4. Semantic parity

Paired documents preserve learning outcomes and IDs; scope; prerequisites; assumptions; procedures and order; expected results; safety boundaries; cleanup and rollback; evidence; assessment criteria; references; versions; limitations. Idioms may be adapted, but technical meaning and learning demand must not change silently.

## 5. Technical strings

Keep stable IDs, code, scripts, commands, SPL, queries, configuration keys, IPs, ports, file paths, event IDs, field names, literal sample data, product/protocol names, standards identifiers, ATT&CK technique IDs, and official control identifiers unchanged unless an approved exception exists. Explain canonical English terms in Arabic where useful. Maintain a shared glossary when justified.

## 6. Synchronization

Update both variants in the same change when meaning changes. If one cannot be updated, mark it `needs-update` and identify the missing work. English is the canonical filename and baseline counterpart, not a statement that Arabic is secondary. Do not treat machine translation as evidence of parity.

## 7. Review

Review technical meaning, natural instructional language, completeness, equivalent cognitive demand, steps, evidence, safety, assessments, identifiers, values, references, links, privacy, and protected instructor content. Record reviewer, date, scope, findings, and limitations. Language review does not replace technical review, lab execution, or owner approval.

## 8. Translation status

- `not-started`: no counterpart exists.
- `draft`: counterpart is being authored.
- `in-review`: language/parity review is underway.
- `synchronized`: documented parity check found equivalence within scope.
- `needs-update`: source changes may have made the counterpart stale.

A synchronized pair may still be draft, unapproved, unreleased, or not practically validated.

## 9. Public repository

The repository is public. Do not commit protected answer keys, unreleased instructor-only solutions, credentials, private student data, or restricted assets in either language. Use an access-controlled location.

## 10. Exceptions

Exceptions require documented rationale and Project Owner decision. This policy remains Draft until explicitly approved.