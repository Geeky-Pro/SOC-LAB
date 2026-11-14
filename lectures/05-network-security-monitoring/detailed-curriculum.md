# Detailed Curriculum — Module 05: Network Security Monitoring & Analysis

[النسخة العربية](./detailed-curriculum-ar.md)

> **Status:** draft — independently re-reviewed (PASS WITH NOTES); pending Project Owner approval  
> **Module ID:** 05-network-security-monitoring  
> **Curriculum version:** 0.3  
> **Proposed contact time:** 8 hours

## 1. Module purpose

Network Security Monitoring & Analysis develops the capability to perform the domain-specific work expected of a SOC analyst. Instruction is capability-led; tools are used as supporting instruments, not as learning outcomes.

## 2. Prerequisites

Modules 01–02; IP addressing, TCP/UDP, DNS, HTTP basics.

## 3. Measurable learning outcomes

By the end of this module, learners should be able to:

| ID | Learning outcome | Lesson alignment | Evidence |
|---|---|---|---|
| LO-05-01 | Explain packet, flow, session, and application-layer visibility and their limitations. | L05-01, L05-02 | Protocol worksheet with packet/time references and TCP/UDP/DNS/HTTP/TLS interpretation. |
| LO-05-02 | Interpret Ethernet/IP/TCP/UDP/DNS/HTTP/TLS metadata relevant to investigations. | L05-02, L05-04 | DNS/web/TLS timeline with encrypted-payload limitations. |
| LO-05-03 | Use packet-capture tools to filter, follow, and summarize conversations. | L05-03 | PCAP analysis record with scope, filters, packet references, and sanitized export if required. |
| LO-05-04 | Identify unusual connection patterns, scanning-like behavior, and suspicious egress hypotheses. | L05-04, L05-05 | Traffic-pattern comparison, baseline, competing hypotheses, and confidence. |
| LO-05-05 | Correlate PCAP observations with firewall, endpoint, and SIEM context. | L05-05, L05-06 | Network investigation report correlating PCAP with available firewall/endpoint/SIEM records. |
| LO-05-06 | Document network findings with packet/time references and confidence. | L05-03, L05-06 | Network investigation report correlating PCAP with available firewall/endpoint/SIEM records. |

## 4. Detailed lesson sequence

### L05-01 — Network visibility models and telemetry sources

- **Duration:** 60 minutes
- **Core content:** Packets, flows, logs; SPAN/TAP concepts; metadata versus payload; encryption and blind spots.
- **Learning activity:** Select the best evidence source for investigation questions.
- **Evidence:** Completed select the best evidence source for investigation questions artifact with source/time references, the learner's reasoning, and at least one stated limitation or uncertainty.

### L05-02 — Protocols and conversation reconstruction

- **Duration:** 90 minutes
- **Core content:** Ethernet; IP; TCP handshake/flags; UDP; ports; DNS; HTTP; TLS handshake metadata.
- **Learning activity:** Interpret protocol sequences from supplied captures.
- **Evidence:** Completed interpret protocol sequences from supplied captures artifact with source/time references, the learner's reasoning, and at least one stated limitation or uncertainty.

### L05-03 — Packet capture workflow and filtering

- **Duration:** 90 minutes
- **Core content:** Capture scope; display/capture filters; stream following; timestamps; reassembly; export objects safely.
- **Learning activity:** Answer structured questions from a PCAP.
- **Evidence:** Completed answer structured questions from a pcap artifact with source/time references, the learner's reasoning, and at least one stated limitation or uncertainty.

### L05-04 — DNS, web, and encrypted traffic analysis

- **Duration:** 75 minutes
- **Core content:** Queries/responses; NXDOMAIN; TTL; HTTP methods/status; TLS SNI/cert metadata where present; encrypted payload limits.
- **Learning activity:** Build a destination and request timeline.
- **Evidence:** Completed build a destination and request timeline artifact with source/time references, the learner's reasoning, and at least one stated limitation or uncertainty.

### L05-05 — Scanning, beaconing, and anomalous traffic hypotheses

- **Duration:** 75 minutes
- **Core content:** Connection frequency; fan-out; periodicity; volume; failed connections; baseline and false positives.
- **Learning activity:** Compare normal and suspicious traffic patterns.
- **Evidence:** Completed compare normal and suspicious traffic patterns artifact with source/time references, the learner's reasoning, and at least one stated limitation or uncertainty.

### L05-06 — Network investigation and cross-source correlation

- **Duration:** 90 minutes
- **Core content:** PCAP with pfSense logs, endpoint events, and Splunk; time normalization; evidence limits.
- **Learning activity:** Produce a network case summary and timeline.
- **Evidence:** Completed produce a network case summary and timeline artifact with source/time references, the learner's reasoning, and at least one stated limitation or uncertainty.

## 5. Practical learning activities

The following are curriculum-level activity blueprints, not final student lab instructions. Convert each activity into its module-specific lab/scenario asset before delivery.

| Activity ID | Learner task | Required input / environment | Expected output | Safety, cleanup, and recovery |
|---|---|---|---|---|
| LAB-05-A | Analyze a supplied PCAP to answer protocol and traffic questions. | Sanitized PCAP; Wireshark. | Packet/time references, protocol worksheet, filters, conversation summary. | Use approved captures only; do not capture unrelated physical LAN traffic. |
| LAB-05-B | Correlate traffic patterns with firewall/endpoint logs. | Sanitized PCAP and matching logs, or isolated lab traffic under instructor direction. | Cross-source timeline, competing hypotheses, confidence, visibility limits. | No scanning outside isolated lab; define target allowlist and stop condition. |

Before publication, the corresponding lab/scenario asset must add exact steps, tested versions, instructor preparation, troubleshooting, reset procedure, expected outputs, and evidence-capture instructions. If a telemetry source is unavailable, use a clearly labeled instructor-provided dataset and record the substitution.

## 6. Assessment plan

**Primary assessment evidence:** LAB-05-A, LAB-05-B — see the practical activity blueprint above and the [common SOC-LAB assessment rubric](../../curriculum/assessment-rubric.md).

| Learning outcome | Lesson mapping (I/P/A) | Observable assessment evidence |
|---|---|---|
| LO-05-01 | L05-01 (I/P), L05-02 (A) | Protocol worksheet with packet/time references and TCP/UDP/DNS/HTTP/TLS interpretation. |
| LO-05-02 | L05-02 (I/P), L05-04 (A) | DNS/web/TLS timeline with encrypted-payload limitations. |
| LO-05-03 | L05-03 (I/P/A) | PCAP analysis record with scope, filters, packet references, and sanitized export if required. |
| LO-05-04 | L05-04 (I/P), L05-05 (A) | Traffic-pattern comparison, baseline, competing hypotheses, and confidence. |
| LO-05-05 | L05-05 (I/P), L05-06 (A) | Network investigation report correlating PCAP with available firewall/endpoint/SIEM records. |
| LO-05-06 | L05-03 (I/P), L05-06 (A) | Network investigation report correlating PCAP with available firewall/endpoint/SIEM records. |

**Mapping legend:** I = introduces the outcome; P = provides guided/independent practice; A = contains the observable assessment evidence. A single-lesson outcome is marked I/P/A in that lesson. These labels are the proposed instructional design and must be confirmed when the lecture and lab assets are authored.

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

The proposed 8-hour allocation is a planning estimate. It must be checked against the actual lesson materials, learner skill level, lab setup time, and classroom pilot. Breaks and independent study are excluded.

## 10. Quality and validation gates

- [ ] Outcomes are observable and assessable.
- [ ] Every lesson maps to outcomes and evidence.
- [ ] Activities and assessment instructions are complete and accessible.
- [ ] Technical references and versions are checked.
- [ ] Lab dependencies and telemetry are verified or clearly marked unavailable.
- [ ] Safety, cleanup, and reset instructions are present for every hands-on activity.
- [ ] Instructor and student materials are separated.
- [x] Independent Quality Reviewer review completed (PASS WITH NOTES; 2026-11-10).
- [ ] Project Owner approval recorded.

**Current validation state:** NOT VALIDATED. No classroom pilot or end-to-end practical execution is claimed.

## 11. References

Use the lesson-mapped [Module Reference Catalog](../../curriculum/references/module-reference-catalog.md) as the research starting point. During lesson production, record the exact page/edition and access date for every technical claim. The catalog does not imply that lab-specific versions or configurations have been validated.

## 12. Change history

| Version | Change | Status |
|---|---|---|
| 0.3 | Revised outcome mapping, evidence expectations, activity blueprint, and lesson evidence following independent review | Draft |
| 0.2 | Initial detailed curriculum design for this module | Draft |
