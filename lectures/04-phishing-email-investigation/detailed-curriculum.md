# Detailed Curriculum — Module 04: Phishing & Email Security Investigation

> **Status:** draft — pending independent review and Project Owner approval  
> **Module ID:** 04-phishing-email-investigation  
> **Curriculum version:** 0.2  
> **Proposed contact time:** 7 hours

## 1. Module purpose

Phishing & Email Security Investigation develops the capability to perform the domain-specific work expected of a SOC analyst. Instruction is capability-led; tools are used as supporting instruments, not as learning outcomes.

## 2. Prerequisites

Modules 01–02; basic email, DNS, URL, and file concepts.

## 3. Measurable learning outcomes

By the end of this module, learners should be able to:

| ID | Learning outcome | Lesson alignment | Evidence |
|---|---|---|---|
| LO-04-01 | Explain email delivery components and the purpose and limits of common authentication results. | L04-01, L04-02 | Header trace with Received-chain interpretation, authentication results, and trust limitations. |
| LO-04-02 | Parse message headers and reconstruct sender, relay, and timestamp context. | L04-02, L04-05 | Phishing disposition with exposure, corroborating indicators, alternative explanation, and confidence. |
| LO-04-03 | Assess sender identity, URLs, domains, and message content using multiple independent indicators. | L04-02, L04-03, L04-05 | Phishing disposition with exposure, corroborating indicators, alternative explanation, and confidence. |
| LO-04-04 | Handle attachments and URLs safely using offline or controlled analysis methods. | L04-04, L04-06 | Mailpit local trace or supplied sanitized .eml analysis; state that simulation is not external delivery. |
| LO-04-05 | Determine likely phishing disposition, user exposure, and confidence without overclaiming attribution. | L04-03, L04-04, L04-05, L04-06 | Mailpit local trace or supplied sanitized .eml analysis; state that simulation is not external delivery. |
| LO-04-06 | Write a concise phishing investigation and user/operations recommendation. | L04-05, L04-06 | Mailpit local trace or supplied sanitized .eml analysis; state that simulation is not external delivery. |

## 4. Detailed lesson sequence

### L04-01 — Email architecture, message anatomy, and threat patterns

- **Duration:** 60 minutes
- **Core content:** SMTP flow; envelope versus header; MIME; spoofing, impersonation, credential lures, malicious links/attachments.
- **Learning activity:** Label message components and classify threat patterns.
- **Evidence:** Completed label message components and classify threat patterns artifact with source/time references, the learner's reasoning, and at least one stated limitation or uncertainty.

### L04-02 — Header analysis and sender authentication

- **Duration:** 90 minutes
- **Core content:** Received chain; Message-ID; Return-Path; From/Reply-To; SPF/DKIM/DMARC outcomes and limitations.
- **Learning activity:** Parse a sanitized header and explain trust gaps.
- **Evidence:** Completed parse a sanitized header and explain trust gaps artifact with source/time references, the learner's reasoning, and at least one stated limitation or uncertainty.

### L04-03 — URL, domain, and infrastructure assessment

- **Duration:** 75 minutes
- **Core content:** URL components; redirects; lookalike domains; DNS context; reputation caveats; safe browsing controls.
- **Learning activity:** Analyze defanged URLs and record observable indicators.
- **Evidence:** Completed analyze defanged urls and record observable indicators artifact with source/time references, the learner's reasoning, and at least one stated limitation or uncertainty.

### L04-04 — Attachment triage and safe artifact handling

- **Duration:** 75 minutes
- **Core content:** File types; hashes; metadata; archive risks; sandbox concepts; no execution on host.
- **Learning activity:** Classify inert sample metadata and propose safe next steps.
- **Evidence:** Completed classify inert sample metadata and propose safe next steps artifact with source/time references, the learner's reasoning, and at least one stated limitation or uncertainty.

### L04-05 — Email investigation workflow and disposition

- **Duration:** 75 minutes
- **Core content:** Correlating artifacts; user interaction; scope; confidence; false positives; escalation.
- **Learning activity:** Investigate a synthetic phishing report.
- **Evidence:** Completed investigate a synthetic phishing report artifact with source/time references, the learner's reasoning, and at least one stated limitation or uncertainty.

### L04-06 — Mailpit-based local exercise and case report

- **Duration:** 45 minutes
- **Core content:** Optional local mail capture; controlled test messages; evidence and reporting.
- **Learning activity:** Trace a benign test message and distinguish simulation from real delivery.
- **Evidence:** Completed trace a benign test message and distinguish simulation from real delivery artifact with source/time references, the learner's reasoning, and at least one stated limitation or uncertainty.

## 5. Practical learning activities

The following are curriculum-level activity blueprints, not final student lab instructions. Convert each activity into its module-specific lab/scenario asset before delivery.

| Activity ID | Learner task | Required input / environment | Expected output | Safety, cleanup, and recovery |
|---|---|---|---|---|
| LAB-04-A | Analyze sanitized .eml files, headers, URLs, and inert attachment metadata. | Sanitized messages; offline text tools; no live browsing. | Header trace, authentication interpretation, URL table, artifact triage. | Do not open links or execute attachments; use defanged URLs and inert metadata. |
| LAB-04-B | Trace a benign message through optional Mailpit or a supplied capture. | Mailpit local-only instance or supplied message artifact. | Message trace and phishing disposition report. | Mailpit must remain local and non-relaying; verify no outbound SMTP route. |

Before publication, the corresponding lab/scenario asset must add exact steps, tested versions, instructor preparation, troubleshooting, reset procedure, expected outputs, and evidence-capture instructions. If a telemetry source is unavailable, use a clearly labeled instructor-provided dataset and record the substitution.

## 6. Assessment plan

**Primary assessment evidence:** LAB-04-A, LAB-04-B — see the practical activity blueprint above and the [common SOC-LAB assessment rubric](../../curriculum/assessment-rubric.md).

| Learning outcome | Lesson(s) introducing/practicing/assessing | Observable assessment evidence |
|---|---|---|
| LO-04-01 | L04-01, L04-02 | Header trace with Received-chain interpretation, authentication results, and trust limitations. |
| LO-04-02 | L04-02, L04-05 | Phishing disposition with exposure, corroborating indicators, alternative explanation, and confidence. |
| LO-04-03 | L04-02, L04-03, L04-05 | Phishing disposition with exposure, corroborating indicators, alternative explanation, and confidence. |
| LO-04-04 | L04-04, L04-06 | Mailpit local trace or supplied sanitized .eml analysis; state that simulation is not external delivery. |
| LO-04-05 | L04-03, L04-04, L04-05, L04-06 | Mailpit local trace or supplied sanitized .eml analysis; state that simulation is not external delivery. |
| LO-04-06 | L04-05, L04-06 | Mailpit local trace or supplied sanitized .eml analysis; state that simulation is not external delivery. |

Assessment conditions:
- The student brief must state permitted dataset/environment, time limit, allowed references, and submission format before delivery.
- Score only rubric criteria relevant to the outcomes assessed; weighting and pass threshold remain pending Project Owner decision.
- Require source/time references, reasoning, alternatives, uncertainty, and limitations where relevant.
- Identify individual versus team-produced evidence; team output alone does not establish individual mastery.
- Keep instructor answer keys and expected reasoning separate from student-facing materials.

## 7. Lab and resource dependencies

Refer to [Lab Dependency Map](../../curriculum/lab-dependency-map.md) and the shared [Lab Environment](../../lab-environment/README.md). Exact indexes, sourcetypes, fields, ports, versions, export methods, and collection paths must be verified against the deployed lab before being taught as facts.

## 8. Safety and operational boundaries

- Use only authorized, isolated lab assets and approved datasets.
- No public targets, real-user accounts, uncontrolled malware, or unauthorized data collection.
- Disruptive actions require explicit instructor authorization, impact assessment, rollback, and verification.
- Preserve evidence provenance and label synthetic, simulated, captured, and inferred data distinctly.

## 9. Estimated workload

The proposed 7-hour allocation is a planning estimate. It must be checked against the actual lesson materials, learner skill level, lab setup time, and classroom pilot. Breaks and independent study are excluded.

## 10. Quality and validation gates

- [ ] Outcomes are observable and assessable.
- [ ] Every lesson maps to outcomes and evidence.
- [ ] Activities and assessment instructions are complete and accessible.
- [ ] Technical references and versions are checked.
- [ ] Lab dependencies and telemetry are verified or clearly marked unavailable.
- [ ] Safety, cleanup, and reset instructions are present for every hands-on activity.
- [ ] Instructor and student materials are separated.
- [ ] Independent Quality Reviewer review completed.
- [ ] Project Owner approval recorded.

**Current validation state:** NOT VALIDATED. No classroom pilot or end-to-end practical execution is claimed.

## 11. References

Use the lesson-mapped [Module Reference Catalog](../../curriculum/references/module-reference-catalog.md) as the research starting point. During lesson production, record the exact page/edition and access date for every technical claim. The catalog does not imply that lab-specific versions or configurations have been validated.

## 12. Change history

| Version | Change | Status |
|---|---|---|
| 0.2 | Initial detailed curriculum design for this module | Draft |
