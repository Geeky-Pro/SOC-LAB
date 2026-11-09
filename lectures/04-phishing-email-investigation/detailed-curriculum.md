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
| LO-04-01 | Explain email delivery components and the purpose and limits of common authentication results. | L04-01, L04-02, L04-03, L04-04, L04-05, L04-06 | Practical artifact |
| LO-04-02 | Parse message headers and reconstruct sender, relay, and timestamp context. | L04-01, L04-02, L04-03, L04-04, L04-05, L04-06 | Mapped lesson activity and assessment evidence |
| LO-04-03 | Assess sender identity, URLs, domains, and message content using multiple independent indicators. | L04-01, L04-02, L04-03, L04-04, L04-05, L04-06 | Mapped lesson activity and assessment evidence |
| LO-04-04 | Handle attachments and URLs safely using offline or controlled analysis methods. | L04-01, L04-02, L04-03, L04-04, L04-05, L04-06 | Mapped lesson activity and assessment evidence |
| LO-04-05 | Determine likely phishing disposition, user exposure, and confidence without overclaiming attribution. | L04-01, L04-02, L04-03, L04-04, L04-05, L04-06 | Mapped lesson activity and assessment evidence |
| LO-04-06 | Write a concise phishing investigation and user/operations recommendation. | L04-01, L04-02, L04-03, L04-04, L04-05, L04-06 | Mapped lesson activity and assessment evidence |

## 4. Detailed lesson sequence

### L04-01 — Email architecture, message anatomy, and threat patterns

- **Duration:** 60 minutes
- **Core content:** SMTP flow; envelope versus header; MIME; spoofing, impersonation, credential lures, malicious links/attachments.
- **Learning activity:** Label message components and classify threat patterns.
- **Evidence:** learner worksheet, notes, or practical artifact aligned to the lesson outcomes.

### L04-02 — Header analysis and sender authentication

- **Duration:** 90 minutes
- **Core content:** Received chain; Message-ID; Return-Path; From/Reply-To; SPF/DKIM/DMARC outcomes and limitations.
- **Learning activity:** Parse a sanitized header and explain trust gaps.
- **Evidence:** learner worksheet, notes, or practical artifact aligned to the lesson outcomes.

### L04-03 — URL, domain, and infrastructure assessment

- **Duration:** 75 minutes
- **Core content:** URL components; redirects; lookalike domains; DNS context; reputation caveats; safe browsing controls.
- **Learning activity:** Analyze defanged URLs and record observable indicators.
- **Evidence:** learner worksheet, notes, or practical artifact aligned to the lesson outcomes.

### L04-04 — Attachment triage and safe artifact handling

- **Duration:** 75 minutes
- **Core content:** File types; hashes; metadata; archive risks; sandbox concepts; no execution on host.
- **Learning activity:** Classify inert sample metadata and propose safe next steps.
- **Evidence:** learner worksheet, notes, or practical artifact aligned to the lesson outcomes.

### L04-05 — Email investigation workflow and disposition

- **Duration:** 75 minutes
- **Core content:** Correlating artifacts; user interaction; scope; confidence; false positives; escalation.
- **Learning activity:** Investigate a synthetic phishing report.
- **Evidence:** learner worksheet, notes, or practical artifact aligned to the lesson outcomes.

### L04-06 — Mailpit-based local exercise and case report

- **Duration:** 45 minutes
- **Core content:** Optional local mail capture; controlled test messages; evidence and reporting.
- **Learning activity:** Trace a benign test message and distinguish simulation from real delivery.
- **Evidence:** learner worksheet, notes, or practical artifact aligned to the lesson outcomes.

## 5. Practical learning activities

Analyze sanitized email headers, defanged URLs, and inert attachment metadata; optional Mailpit local mail exercise.

Activities must be delivered only within the authorized lab or with instructor-provided sanitized/synthetic artifacts. If required telemetry is unavailable, disclose the substitution and its limitations.

## 6. Assessment plan

**Primary assessment evidence:** Header analysis, indicator assessment, safe-handling record, verdict, confidence, and user guidance.

Assessment design rules:
- Map every scored task to one or more LO identifiers.
- Require source references, timestamps where available, reasoning, limitations, and uncertainty.
- Score analytical process and evidence quality, not merely the final verdict.
- Do not require a single severity/verdict when multiple evidence-supported conclusions are reasonable.
- Keep instructor answer keys separate from student-facing instructions.

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

Use authoritative, versioned sources appropriate to the lesson. Record the publication/version and access date during content development. Do not add references that were not consulted or that do not support the relevant claims.

## 12. Change history

| Version | Change | Status |
|---|---|---|
| 0.2 | Initial detailed curriculum design for this module | Draft |
