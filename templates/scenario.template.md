# [Scenario Name]

> **Status:** draft  
> **Module:** [module-id]  
> **Scenario ID:** [scenario-id]  
> **Difficulty:** [level]  
> **Estimated duration:** [minutes]  
> **Scenario type:** [investigation/detection/response/integrated]

## 1. Scenario purpose

[Capability being assessed or developed.]

## 2. Learning outcomes

- [LO-01]
- [LO-02]

## 3. Narrative and initial report

[Provide a realistic starting narrative and the alert/report available to the analyst.]

## 4. Authorized scope and safety

- **Environment:** [isolated lab]
- **In-scope assets:** [assets]
- **Excluded assets:** [assets]
- **Simulation method:** [method]
- **Expected impact:** [impact]
- **Cleanup/reset:** [steps]

## 5. Prerequisites and starting state

[Required lab state, telemetry, accounts, snapshots, and prior knowledge.]

## 6. Scenario timeline and injects

| Time/phase | Action or inject | Expected telemetry | Instructor notes |
|---|---|---|---|
| T+00 | [Initial alert] | [Evidence] | [Notes] |
| T+05 | [Activity] | [Evidence] | [Notes] |

## 7. Telemetry and evidence matrix

| Source | Evidence/artifact | Expected fields/indicators | Investigation value |
|---|---|---|---|
| [Endpoint/Sysmon] | [Event/log] | [Fields] | [Value] |
| [Network/PCAP] | [Traffic] | [Indicators] | [Value] |
| [Firewall/IDS] | [Alert/log] | [Fields] | [Value] |
| [Web/email/SIEM] | [Record] | [Fields] | [Value] |

Clearly label synthetic evidence and distinguish it from evidence captured from an executed lab.

## 8. Student investigation tasks

1. [Task]
2. [Task]

## 9. Expected analyst reasoning

[Describe hypotheses, evidence pivots, corroboration, alternative explanations, and confidence. Do not reveal this section in student materials if it is an answer key.]

## 10. Detection opportunities

[Describe candidate searches/rules, prerequisites, field assumptions, false-positive considerations, and validation criteria.]

## 11. Response and containment decisions

[Describe response options, trade-offs, escalation criteria, recovery, and documentation.]

## 12. Instructor guide and answer key

[Hints, expected conclusions, common wrong turns, and debrief prompts. Store separately if required by access policy.]

## 13. ATT&CK mapping

| Technique ID/name | Scenario behavior supporting mapping | Evidence |
|---|---|---|
| [ID/name] | [Observed/simulated behavior] | [Evidence] |

Omit mappings that are not supported by scenario behavior.

## 14. Assessment rubric

| Criterion | Expected performance | Points/level |
|---|---|---:|
| Evidence collection | [Standard] | [Score] |
| Analysis | [Standard] | [Score] |
| Response reasoning | [Standard] | [Score] |

## 15. Cleanup and reset

[Restore lab state and remove generated artifacts.]

## 16. Validation and limitations

- **Evidence generated/captured:** [Details]
- **Scenario executed:** [Yes/no; environment/date/evidence]
- **Detection tested:** [Details or not tested]
- **Independent validation:** [Details or not validated]
- **Known limitations:** [Details]

## 17. References

- [Author/organization, title, version/date, URL, access date]
