# Module Map

> **Status:** draft — proposed dependencies

| ID | Module | Capability focus | Main evidence | Depends on |
|---|---|---|---|---|
| 01 | SOC Fundamentals & Security Operations | SOC roles, workflow, alert triage | Triage notes, priority and escalation rationale | — |
| 02 | SOC Lab Architecture & Deployment | Deploy and understand lab topology and telemetry | Topology, deployment and data-flow checks | 01 |
| 03 | Endpoint Detection & Investigation | Windows/Sysmon host investigation | Event evidence, process/activity timeline | 01, 02 |
| 04 | Phishing & Email Security Investigation | Email artifacts and phishing triage | Header/artifact analysis, verdict | 01, 02 |
| 05 | Network Security Monitoring & Analysis | Network traffic and protocol analysis | PCAP observations, traffic findings | 01, 02 |
| 06 | Network Intrusion Detection & Prevention | Suricata alert interpretation | Alert context and validation notes | 02, 05 |
| 07 | Web Security Monitoring & Investigation | Web and application log investigation | Request timeline and suspicious activity analysis | 02, 05 |
| 08 | Incident Response | Scope, contain, recover, document | Incident record and response plan | 03–07 |
| 09 | Attack Simulation & Detection Validation | Controlled emulation and detection testing | Test plan, telemetry, detection results | 03, 05–08 |
| 10 | Operation Shadow Access | Integrated multi-source investigation | Correlated timeline, hypotheses, response decisions | 03–09 |
| 11 | SOC Capstone Project | End-to-end SOC performance | Investigation package, report, briefing | 01–10 |

Dependencies are proposed learning dependencies, not a statement that content or infrastructure is complete. Module 10 integrates earlier skills; Module 11 assesses them rather than introducing unrelated tools.
