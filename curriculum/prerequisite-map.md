# Prerequisite Map

> **Status:** draft — proposed progression

```mermaid
flowchart TD
  M01[01 SOC Fundamentals] --> M02[02 Lab Architecture]
  M02 --> M03[03 Endpoint]
  M02 --> M04[04 Email]
  M02 --> M05[05 Network Monitoring]
  M05 --> M06[06 Network IDS/IPS]
  M02 --> M07[07 Web Investigation]
  M03 --> M08[08 Incident Response]
  M04 --> M08
  M05 --> M08
  M06 --> M08
  M07 --> M08
  M08 --> M09[09 Simulation & Validation]
  M03 --> M10[10 Operation Shadow Access]
  M04 --> M10
  M05 --> M10
  M06 --> M10
  M07 --> M10
  M08 --> M10
  M09 --> M10
  M10 --> M11[11 SOC Capstone]
```

## Assumptions
- Module 01 establishes shared SOC vocabulary and analyst workflow.
- Module 02 provides the practical environment.
- Modules 03–07 teach focused evidence domains.
- Module 08 consolidates investigation into incident handling.
- Module 09 requires understanding of the behaviors and telemetry being validated.
- Modules 10 and 11 integrate and assess the preceding capabilities.

Review this graph against actual lesson content, lab readiness, and the final schedule before approval.
