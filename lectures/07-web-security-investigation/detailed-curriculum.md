# Detailed Curriculum — Module 07: Web Security Monitoring & Investigation

> **Status:** draft — pending independent review and Project Owner approval  
> **Module ID:** 07-web-security-investigation  
> **Curriculum version:** 0.2  
> **Proposed contact time:** 7 hours

## 1. Module purpose

Web Security Monitoring & Investigation develops the capability to perform the domain-specific work expected of a SOC analyst. Instruction is capability-led; tools are used as supporting instruments, not as learning outcomes.

## 2. Prerequisites

Modules 02 and 05; HTTP request/response and basic web architecture.

## 3. Measurable learning outcomes

By the end of this module, learners should be able to:

| ID | Learning outcome | Lesson alignment | Evidence |
|---|---|---|---|
| LO-07-01 | Explain web request flow and the roles of web server, application, reverse proxy, and firewall logs. | L07-01, L07-02, L07-03, L07-04, L07-05, L07-06 | Practical artifact |
| LO-07-02 | Interpret access-log fields, HTTP methods, status codes, paths, user agents, and client context. | L07-01, L07-02, L07-03, L07-04, L07-05, L07-06 | Mapped lesson activity and assessment evidence |
| LO-07-03 | Identify suspicious request patterns while distinguishing probes, errors, and confirmed impact. | L07-01, L07-02, L07-03, L07-04, L07-05, L07-06 | Mapped lesson activity and assessment evidence |
| LO-07-04 | Reconstruct a web activity timeline and correlate it with network and endpoint evidence. | L07-01, L07-02, L07-03, L07-04, L07-05, L07-06 | Mapped lesson activity and assessment evidence |
| LO-07-05 | Assess common web attack indicators at a monitoring/investigation level without conducting unsafe exploitation. | L07-01, L07-02, L07-03, L07-04, L07-05, L07-06 | Mapped lesson activity and assessment evidence |
| LO-07-06 | Produce a web security investigation with evidence, uncertainty, and recommended next steps. | L07-01, L07-02, L07-03, L07-04, L07-05, L07-06 | Mapped lesson activity and assessment evidence |

## 4. Detailed lesson sequence

### L07-01 — Web architecture and telemetry sources

- **Duration:** 60 minutes
- **Core content:** Client/server; DNS/TLS; reverse proxy; application logs; access logs; logging gaps.
- **Learning activity:** Map investigative questions to log sources.
- **Evidence:** learner worksheet, notes, or practical artifact aligned to the lesson outcomes.

### L07-02 — HTTP requests, responses, and access-log interpretation

- **Duration:** 90 minutes
- **Core content:** Methods; paths; query strings; status codes; bytes; referrer; user-agent; client IP trust boundaries.
- **Learning activity:** Parse logs and build request summaries.
- **Evidence:** learner worksheet, notes, or practical artifact aligned to the lesson outcomes.

### L07-03 — Suspicious web patterns and attack indicators

- **Duration:** 90 minutes
- **Core content:** Reconnaissance; path traversal indicators; injection-like strings; auth abuse; upload anomalies; rate patterns.
- **Learning activity:** Classify synthetic requests as benign, suspicious, or indeterminate.
- **Evidence:** learner worksheet, notes, or practical artifact aligned to the lesson outcomes.

### L07-04 — Web server investigation in Splunk

- **Duration:** 75 minutes
- **Core content:** Time-bounded searches; field extraction verification; aggregation; client/request pivots.
- **Learning activity:** Investigate a prepared web log dataset.
- **Evidence:** learner worksheet, notes, or practical artifact aligned to the lesson outcomes.

### L07-05 — Cross-source correlation and impact assessment

- **Duration:** 75 minutes
- **Core content:** Correlate firewall/Suricata, PCAP, endpoint, and web records; 4xx/5xx interpretation; impact evidence.
- **Learning activity:** Build a multi-source request timeline.
- **Evidence:** learner worksheet, notes, or practical artifact aligned to the lesson outcomes.

### L07-06 — Web incident report and handoff

- **Duration:** 30 minutes
- **Core content:** Scope, confidence, evidence, recommended containment/escalation.
- **Learning activity:** Submit concise investigation report.
- **Evidence:** learner worksheet, notes, or practical artifact aligned to the lesson outcomes.

## 5. Practical learning activities

Analyze Ubuntu web access/application logs; classify suspicious requests; correlate with network and endpoint records.

Activities must be delivered only within the authorized lab or with instructor-provided sanitized/synthetic artifacts. If required telemetry is unavailable, disclose the substitution and its limitations.

## 6. Assessment plan

**Primary assessment evidence:** Web request timeline, suspicious-pattern assessment, cross-source correlation, and incident handoff.

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
