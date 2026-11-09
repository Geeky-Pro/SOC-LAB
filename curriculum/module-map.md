# Module Map

> **Status:** draft — revised proposed dependencies and duration estimates

| ID | Module | Capability focus | Proposed hours | Detailed design | Depends on |
|---|---|---|---:|---|---|
| 01 | SOC Fundamentals & Security Operations | SOC roles, workflow, alert triage | 6 | [Detailed curriculum](../lectures/01-soc-fundamentals/detailed-curriculum.md) | — |
| 02 | SOC Lab Architecture & Deployment | Deploy and understand lab topology and telemetry | 8 | [Detailed curriculum](../lectures/02-soc-lab-architecture/detailed-curriculum.md) | 01 |
| 03 | Endpoint Detection & Investigation | Windows/Sysmon host investigation | 8 | [Detailed curriculum](../lectures/03-endpoint-detection-investigation/detailed-curriculum.md) | 01, 02 |
| 04 | Phishing & Email Security Investigation | Email artifacts and phishing triage | 7 | [Detailed curriculum](../lectures/04-phishing-email-investigation/detailed-curriculum.md) | 01, 02 |
| 05 | Network Security Monitoring & Analysis | Network traffic and protocol analysis | 8 | [Detailed curriculum](../lectures/05-network-security-monitoring/detailed-curriculum.md) | 01, 02 |
| 06 | Network Intrusion Detection & Prevention | Alert analysis, prevention-policy evaluation, and safe control validation | 7 | [Detailed curriculum](../lectures/06-network-intrusion-detection/detailed-curriculum.md) | 02, 05 |
| 07 | Web Security Monitoring & Investigation | Web and application log investigation | 7 | [Detailed curriculum](../lectures/07-web-security-investigation/detailed-curriculum.md) | 02, 05 |
| 08 | Incident Response | Scope, contain, recover, document | 8 | [Detailed curriculum](../lectures/08-incident-response/detailed-curriculum.md) | 03–07 |
| 09 | Attack Simulation & Detection Validation | Controlled emulation and detection testing | 8 | [Detailed curriculum](../lectures/09-attack-simulation-detection-validation/detailed-curriculum.md) | 03, 05–08 |
| 10 | Operation Shadow Access | Integrated endpoint, email, network, IDS, web, and SIEM investigation | 10 | [Detailed curriculum](../lectures/10-operation-shadow-access/detailed-curriculum.md) | 03–09 |
| 11 | SOC Capstone Project | End-to-end SOC performance | 12 | [Detailed curriculum](../lectures/11-soc-capstone/detailed-curriculum.md) | 01–10 |
| | **Total proposed contact time** | | **89** | | |

Dependencies are proposed learning dependencies, not a statement that content or infrastructure is complete. Durations are estimates excluding breaks and independent work. Module 10 integrates earlier skills, including email analysis through a sanitized message artifact; Module 11 assesses them rather than introducing unrelated tools.
