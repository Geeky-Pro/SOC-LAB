# ADR-0001: SOC-LAB Repository Architecture v2

- **Status:** Proposed working foundation; pending explicit Project Owner approval.
- **Date:** 2026-11-10
- **Owner:** Project Owner

## Context

The previous repository accumulated course files with inconsistent naming, overlapping content, and mixed audiences. The existing materials were moved to `Archive/` to preserve them while a maintainable architecture is established.

## Decision

Adopt a competency-oriented repository with distinct areas for governance, curriculum, modules, shared lab infrastructure, detection engineering, incident response, instructor guidance, templates, tooling, validation, releases, and archive.

Use two AI roles: a Content Engineer for drafting and a separate Quality Reviewer for independent review. Keep reusable skills separate from provider-specific agent definitions. The Project Owner retains final approval.

## Consequences

- Existing archived material must be reviewed before reuse.
- Module structures remain intentionally flexible; do not create unused empty directories.
- Shared assets have one canonical location.
- Curriculum and AI workflow will be implemented in later phases.
- Validation and release evidence become explicit requirements.

## Alternatives considered

- Keep the old flat structure: rejected due to discoverability and maintenance issues.
- Create many narrowly scoped agents: rejected in favor of two focused agents with composable skills.
- Make every module use an identical exhaustive folder tree: rejected because it creates empty scaffolding and unnecessary maintenance.
