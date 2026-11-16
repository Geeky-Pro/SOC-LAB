# AI System Architecture

## Design

The project uses two focused AI roles rather than a large collection of narrowly scoped agents.

### SOC-LAB Content Engineer

Defined in `.github/agents/soc-lab-content-engineer.agent.md`. Responsible for drafting, organizing, and improving curriculum and learning assets: lectures, slides, labs, scenarios, installation guides, instructor/student materials, assessments, diagrams, and supporting documentation.

### SOC-LAB Quality Reviewer

Defined in `.github/agents/soc-lab-quality-reviewer.agent.md`. Responsible for independent review of technical accuracy, safety, reproducibility, instructional quality, completeness, references, and consistency. It reports evidence and findings; it does not silently rewrite and approve its own review target.

## Skills

Reusable skills provide task-specific methods and checklists. They should be composable and discoverable, with a clear `SKILL.md` entry point and supporting references, templates, or examples where justified.

Skills are not additional agents. An agent reads and applies a relevant skill when the task requires it. Skills should contain reusable procedures/checklists; agent definitions establish role, authority, workflow, and boundaries; prompts provide task-specific starting instructions; path-scoped instructions provide format/domain rules. Avoid copying the same long procedure into all four layers.

Initial skill candidates include curriculum design, lecture development, slide development, lab development, installation documentation, scenario development, instructor/student material development, visual and diagram development, assessment development, security validation, technical documentation, and quality review. Create only the skills that have a clear reusable method and meaningful benefit.

## Instruction layers

1. Root `AGENTS.md`: repository-wide authority, safety, and working rules.
2. `.github/copilot-instructions.md`: Copilot-specific project context and routing.
3. `.github/instructions/*.instructions.md`: path-scoped authoring constraints.
4. `.github/agents/*.agent.md`: focused role definitions and authority boundaries.
5. `.github/prompts/*.prompt.md`: repeatable task starters.
6. `.agents/skills/*/SKILL.md`: reusable task methods and checklists.

If instructions conflict, follow the higher-level governance and human Project Owner decisions. Provider-specific discovery behavior must be configured and verified rather than assumed.

## Authority boundaries

- AI agents are assistants, not project owners.
- The Content Engineer cannot self-approve.
- The Quality Reviewer must distinguish evidence from assumptions.
- The human Project Owner decides acceptance, scope, and release.
- Agents must not claim external research, file edits, test execution, or lab validation that did not occur.

## Workflow

Request → context inspection → draft plan → authoring → author self-check → independent quality review → revision → re-review as needed → Project Owner approval → release preparation.

A review status of PASS or PASS WITH NOTES is a recommendation, not approval. A practical lab execution record is separate evidence and must not be inferred from a documentation review.

## Implementation status

The initial GitHub Copilot agent definitions, repository instructions, path-scoped instructions, and prompt starters are maintained under `.github/`. Their presence in the repository does not prove that every Copilot client or third-party agent runtime discovers or enforces them identically. Verify behavior in the target environment.

Reusable skills are intentionally a later implementation step. Their invocation and ownership boundaries are defined here to prevent duplication with agent and prompt instructions.


## Bilingual authoring and review

Both AI roles operate across English and Arabic. The Content Engineer maintains paired variants with equivalent instructional and technical meaning. The Quality Reviewer checks language quality, terminology, stable identifiers, omissions, contradictions, and cross-language parity. Findings identify the affected language file and its counterpart. Language review does not replace technical review, lab validation, or Project Owner approval. If only one language is completed, the other remains explicitly pending. Normative rules are in `governance/policies/bilingual-content-policy.md`.
