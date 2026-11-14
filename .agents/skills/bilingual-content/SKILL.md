---
name: soc-bilingual-content
description: Create, translate, synchronize, and review paired Arabic and English SOC-LAB documents while preserving technical and instructional equivalence.
---

# SOC-LAB Bilingual Content

## When to use

Use this skill when creating a new bilingual document, translating an existing project document, revising one language variant, synchronizing paired files, or reviewing Arabic/English parity.

## Required context

Read:
- `AGENTS.md`
- `governance/policies/bilingual-content-policy.md`
- `governance/content-lifecycle.md`
- The relevant source and counterpart documents
- The applicable module architecture, template, and path-scoped instructions

## Pairing rules

- Keep both language files in the same directory.
- Use the canonical English filename and append `-ar` before the extension for Arabic.
- Link each substantial document to its counterpart.
- Preserve shared content version and stable IDs.
- Record translation status independently from content lifecycle and practical validation.

## Authoring workflow

1. Identify whether the task is creation, translation, revision, synchronization, or review.
2. Inspect both variants and their dependencies before editing.
3. Establish the source scope and intended audience. Do not silently omit sections.
4. Preserve learning outcomes, scope, prerequisites, assumptions, sequence, decision points, expected evidence, safety controls, cleanup, rollback, assessment criteria, references, and limitations.
5. Preserve technical strings: IDs, commands, code, SPL, queries, field names, configuration keys, IP addresses, ports, paths, event IDs, product names, protocol names, standards identifiers, and sample values.
6. Use natural instructional Arabic. Retain canonical English terms and explain them in Arabic where useful; do not force literal translation.
7. Update both variants when the underlying meaning changes. If one remains stale, mark it `needs-update` and state the missing work.
8. Add or update counterpart links and language metadata when appropriate.
9. Run the parity checklist before handing off for review.

## Parity checklist

- [ ] All headings and substantive sections have counterparts.
- [ ] Learning outcomes and stable IDs match.
- [ ] Scope, prerequisites, assumptions, and learner level match.
- [ ] Procedures, order, decision points, and expected results match.
- [ ] Safety boundaries, warnings, cleanup, and rollback match.
- [ ] Evidence requirements and assessment criteria match.
- [ ] Technical strings, values, references, and version constraints match.
- [ ] No steps, caveats, limitations, or instructor/student boundaries were lost.
- [ ] Arabic is clear, technically accurate, and suitable for the learner audience.
- [ ] Both files link to each other and translation status is accurate.

## Review and handoff

Report:
- English and Arabic paths
- Content version and translation status
- Sections compared
- Parity checklist results
- Unresolved differences and limitations
- Technical checks not performed

Do not mark content approved or released. Do not claim lab execution or technical validation based on translation review. The Quality Reviewer performs independent review; the Project Owner retains final approval.

## Security boundary

The public repository must not contain protected answer keys, unreleased instructor-only solutions, credentials, private student data, or restricted materials in either language.
