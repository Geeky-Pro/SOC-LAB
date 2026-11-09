# Detailed Curriculum — Module 07: Web Security Monitoring & Investigation

> **Status:** draft — pending independent review and Project Owner approval  
> **Module ID:** 07-web-security-investigation  
> **Curriculum version:** 0.3  
> **Proposed contact time:** 7 hours

## 1. Module purpose

Web Security Monitoring & Investigation develops the capability to perform the domain-specific work expected of a SOC analyst. Instruction is capability-led; tools are used as supporting instruments, not as learning outcomes.

## 2. Prerequisites

Modules 02 and 05; HTTP request/response and basic web architecture.

## 3. Measurable learning outcomes

By the end of this module, learners should be able to:

| ID | Learning outcome | Lesson alignment | Evidence |
|---|---|---|---|
| LO-07-01 | Explain web request flow and the roles of web server, application, reverse proxy, and firewall logs. | L07-01 | Web data-flow diagram mapping access, application, proxy, and firewall log sources. |
| LO-07-02 | Interpret access-log fields, HTTP methods, status codes, paths, user agents, and client context. | L07-02, L07-04 | Reproducible Splunk worksheet using observed fields and sample event references. |
| LO-07-03 | Identify suspicious request patterns while distinguishing probes, errors, and confirmed impact. | L07-03, L07-05 | Cross-source request timeline with confirmed/unconfirmed impact distinction. |
| LO-07-04 | Reconstruct a web activity timeline and correlate it with network and endpoint evidence. | L07-04, L07-05 | Cross-source request timeline with confirmed/unconfirmed impact distinction. |
| LO-07-05 | Assess common web attack indicators at a monitoring/investigation level without conducting unsafe exploitation. | L07-03, L07-05 | Cross-source request timeline with confirmed/unconfirmed impact distinction. |
| LO-07-06 | Produce a web security investigation with evidence, uncertainty, and recommended next steps. | L07-05, L07-06 | Concise web investigation report and analyst handoff with limitations. |

## 4. Detailed lesson sequence

### L07-01 — Web architecture and telemetry sources

- **Duration:** 60 minutes
- **Core content:** Client/server; DNS/TLS; reverse proxy; application logs; access logs; logging gaps.
- **Learning activity:** Map investigative questions to log sources.
- **Evidence:** Completed map investigative questions to log sources artifact with source/time references, the learner's reasoning, and at least one stated limitation or uncertainty.

### L07-02 — HTTP requests, responses, and access-log interpretation

- **Duration:** 90 minutes
- **Core content:** Methods; paths; query strings; status codes; bytes; referrer; user-agent; client IP trust boundaries.
- **Learning activity:** Parse logs and build request summaries.
- **Evidence:** Completed parse logs and build request summaries artifact with source/time references, the learner's reasoning, and at least one stated limitation or uncertainty.

### L07-03 — Suspicious web patterns and attack indicators

- **Duration:** 90 minutes
- **Core content:** Reconnaissance; path traversal indicators; injection-like strings; auth abuse; upload anomalies; rate patterns.
- **Learning activity:** Classify synthetic requests as benign, suspicious, or indeterminate.
- **Evidence:** Completed classify synthetic requests as benign, suspicious, or indeterminate artifact with source/time references, the learner's reasoning, and at least one stated limitation or uncertainty.

### L07-04 — Web server investigation in Splunk

- **Duration:** 75 minutes
- **Core content:** Time-bounded searches; field extraction verification; aggregation; client/request pivots.
- **Learning activity:** Investigate a prepared web log dataset.
- **Evidence:** Completed investigate a prepared web log dataset artifact with source/time references, the learner's reasoning, and at least one stated limitation or uncertainty.

### L07-05 — Cross-source correlation and impact assessment

- **Duration:** 75 minutes
- **Core content:** Correlate firewall/Suricata, PCAP, endpoint, and web records; 4xx/5xx interpretation; impact evidence.
- **Learning activity:** Build a multi-source request timeline.
- **Evidence:** Completed build a multi-source request timeline artifact with source/time references, the learner's reasoning, and at least one stated limitation or uncertainty.

### L07-06 — Web incident report and handoff

- **Duration:** 30 minutes
- **Core content:** Scope, confidence, evidence, recommended containment/escalation.
- **Learning activity:** Submit concise investigation report.
- **Evidence:** Completed submit concise investigation report artifact with source/time references, the learner's reasoning, and at least one stated limitation or uncertainty.

## 5. Practical learning activities

The following are curriculum-level activity blueprints, not final student lab instructions. Convert each activity into its module-specific lab/scenario asset before delivery.

| Activity ID | Learner task | Required input / environment | Expected output | Safety, cleanup, and recovery |
|---|---|---|---|---|
| LAB-07-A | Analyze sanitized web logs and classify suspicious requests. | Instructor-provided Ubuntu web logs or isolated web server logs. | Parsed request table, classification, source references. | No real targets or exploitation; synthetic requests or isolated local services only. |
| LAB-07-B | Correlate web requests with network/IDS records and assess impact. | Matched web logs, PCAP, firewall/Suricata sample records. | Request timeline, impact assessment, report with uncertainty. | Do not infer exploitation from a path/status alone; reset only approved lab data. |

Before publication, the corresponding lab/scenario asset must add exact steps, tested versions, instructor preparation, troubleshooting, reset procedure, expected outputs, and evidence-capture instructions. If a telemetry source is unavailable, use a clearly labeled instructor-provided dataset and record the substitution.

## 6. Assessment plan

**Primary assessment evidence:** LAB-07-A, LAB-07-B — see the practical activity blueprint above and the [common SOC-LAB assessment rubric](../../curriculum/assessment-rubric.md).

| Learning outcome | Lesson(s) introducing/practicing/assessing | Observable assessment evidence |
|---|---|---|
| LO-07-01 | L07-01 | Web data-flow diagram mapping access, application, proxy, and firewall log sources. |
| LO-07-02 | L07-02, L07-04 | Reproducible Splunk worksheet using observed fields and sample event references. |
| LO-07-03 | L07-03, L07-05 | Cross-source request timeline with confirmed/unconfirmed impact distinction. |
| LO-07-04 | L07-04, L07-05 | Cross-source request timeline with confirmed/unconfirmed impact distinction. |
| LO-07-05 | L07-03, L07-05 | Cross-source request timeline with confirmed/unconfirmed impact distinction. |
| LO-07-06 | L07-05, L07-06 | Concise web investigation report and analyst handoff with limitations. |

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
| 0.3 | Revised outcome mapping, evidence expectations, activity blueprint, and lesson evidence following independent review | Draft |
| 0.2 | Initial detailed curriculum design for this module | Draft |
