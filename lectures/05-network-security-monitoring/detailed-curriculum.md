# Detailed Curriculum — Module 05: Network Security Monitoring & Analysis

> **Status:** draft — pending independent review and Project Owner approval  
> **Module ID:** 05-network-security-monitoring  
> **Curriculum version:** 0.2  
> **Proposed contact time:** 8 hours

## 1. Module purpose

Network Security Monitoring & Analysis develops the capability to perform the domain-specific work expected of a SOC analyst. Instruction is capability-led; tools are used as supporting instruments, not as learning outcomes.

## 2. Prerequisites

Modules 01–02; IP addressing, TCP/UDP, DNS, HTTP basics.

## 3. Measurable learning outcomes

By the end of this module, learners should be able to:

| ID | Learning outcome | Lesson alignment | Evidence |
|---|---|---|---|
| LO-05-01 | Explain packet, flow, session, and application-layer visibility and their limitations. | L05-01, L05-02, L05-03, L05-04, L05-05, L05-06 | Practical artifact |
| LO-05-02 | Interpret Ethernet/IP/TCP/UDP/DNS/HTTP/TLS metadata relevant to investigations. | L05-01, L05-02, L05-03, L05-04, L05-05, L05-06 | Mapped lesson activity and assessment evidence |
| LO-05-03 | Use packet-capture tools to filter, follow, and summarize conversations. | L05-01, L05-02, L05-03, L05-04, L05-05, L05-06 | Mapped lesson activity and assessment evidence |
| LO-05-04 | Identify unusual connection patterns, scanning-like behavior, and suspicious egress hypotheses. | L05-01, L05-02, L05-03, L05-04, L05-05, L05-06 | Mapped lesson activity and assessment evidence |
| LO-05-05 | Correlate PCAP observations with firewall, endpoint, and SIEM context. | L05-01, L05-02, L05-03, L05-04, L05-05, L05-06 | Mapped lesson activity and assessment evidence |
| LO-05-06 | Document network findings with packet/time references and confidence. | L05-01, L05-02, L05-03, L05-04, L05-05, L05-06 | Mapped lesson activity and assessment evidence |

## 4. Detailed lesson sequence

### L05-01 — Network visibility models and telemetry sources

- **Duration:** 60 minutes
- **Core content:** Packets, flows, logs; SPAN/TAP concepts; metadata versus payload; encryption and blind spots.
- **Learning activity:** Select the best evidence source for investigation questions.
- **Evidence:** learner worksheet, notes, or practical artifact aligned to the lesson outcomes.

### L05-02 — Protocols and conversation reconstruction

- **Duration:** 90 minutes
- **Core content:** Ethernet; IP; TCP handshake/flags; UDP; ports; DNS; HTTP; TLS handshake metadata.
- **Learning activity:** Interpret protocol sequences from supplied captures.
- **Evidence:** learner worksheet, notes, or practical artifact aligned to the lesson outcomes.

### L05-03 — Packet capture workflow and filtering

- **Duration:** 90 minutes
- **Core content:** Capture scope; display/capture filters; stream following; timestamps; reassembly; export objects safely.
- **Learning activity:** Answer structured questions from a PCAP.
- **Evidence:** learner worksheet, notes, or practical artifact aligned to the lesson outcomes.

### L05-04 — DNS, web, and encrypted traffic analysis

- **Duration:** 75 minutes
- **Core content:** Queries/responses; NXDOMAIN; TTL; HTTP methods/status; TLS SNI/cert metadata where present; encrypted payload limits.
- **Learning activity:** Build a destination and request timeline.
- **Evidence:** learner worksheet, notes, or practical artifact aligned to the lesson outcomes.

### L05-05 — Scanning, beaconing, and anomalous traffic hypotheses

- **Duration:** 75 minutes
- **Core content:** Connection frequency; fan-out; periodicity; volume; failed connections; baseline and false positives.
- **Learning activity:** Compare normal and suspicious traffic patterns.
- **Evidence:** learner worksheet, notes, or practical artifact aligned to the lesson outcomes.

### L05-06 — Network investigation and cross-source correlation

- **Duration:** 90 minutes
- **Core content:** PCAP with pfSense logs, endpoint events, and Splunk; time normalization; evidence limits.
- **Learning activity:** Produce a network case summary and timeline.
- **Evidence:** learner worksheet, notes, or practical artifact aligned to the lesson outcomes.

## 5. Practical learning activities

Analyze instructor-provided PCAPs; identify conversations and anomalies; correlate packet and firewall context.

Activities must be delivered only within the authorized lab or with instructor-provided sanitized/synthetic artifacts. If required telemetry is unavailable, disclose the substitution and its limitations.

## 6. Assessment plan

**Primary assessment evidence:** PCAP analysis worksheet, protocol findings, anomalous-traffic hypothesis, and source-referenced timeline.

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

The proposed 8-hour allocation is a planning estimate. It must be checked against the actual lesson materials, learner skill level, lab setup time, and classroom pilot. Breaks and independent study are excluded.

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
