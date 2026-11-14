---
applyTo: "**/*.md"
---

# Markdown documentation instructions

- Use clear headings and concise paragraphs; prefer task-oriented steps for procedures.
- Include purpose, scope, audience, prerequisites, and status when relevant.
- Use relative links for repository files and verify their target paths.
- Use fenced code blocks with language identifiers for commands and configuration.
- Label placeholders explicitly; never use real credentials or tokens in examples.
- Cite external technical references with descriptive link text and record version/date context for volatile material.
- Keep status values consistent with the content lifecycle: planned, draft, in-review, approved, released, deprecated.
- Avoid contradictory duplicated guidance; update the canonical source and link to it.
- State limitations and unverified assumptions explicitly.


## Bilingual authoring requirements

- Arabic and English are first-class project languages. Follow `governance/policies/bilingual-content-policy.md`.
- Keep paired documents in the same directory; English uses the canonical filename and Arabic appends `-ar` before the extension.
- Preserve stable IDs, technical meaning, commands, code, SPL, field names, configuration keys, numeric values, safety boundaries, evidence, and assessment requirements.
- Update both language variants together when meaning changes, or mark the counterpart `needs-update`/pending. Do not claim parity without reviewing both.
