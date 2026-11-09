# Containment, Eradication, and Recovery

> **Status:** draft  
> **Validation:** NOT VALIDATED

## 1. Purpose

This guide helps analysts evaluate response options and document the decisions needed to reduce harm and restore trusted operations. It does not grant authority to execute disruptive actions.

## 2. Before any action

Confirm:
- incident lead and decision authority;
- affected asset owner and service dependencies;
- objective and expected security benefit;
- likely operational, safety, and business impact;
- evidence that should be preserved before the change;
- scope, duration, success criteria, and rollback;
- communication and approval requirements.

For a classroom lab, obtain instructor approval before disconnecting a VM, changing firewall rules, disabling accounts, deleting files, or reverting snapshots.

## 3. Containment

Containment aims to limit ongoing harm while preserving the ability to investigate and recover. Consider the least disruptive effective option.

| Option | Potential benefit | Risks / checks |
|---|---|---|
| Network isolation or restricted egress | Limits communication and spread | May disrupt services and remove remote visibility |
| Block a verified indicator | Interrupts a known path | Indicators can be shared or change; avoid broad unverified blocks |
| Disable or restrict an account | Stops suspected account misuse | May interrupt services or destroy useful session context |
| Restrict a service or application path | Limits exploitation or exposure | May cause outages; validate dependencies |
| Preserve and monitor without immediate isolation | Retains visibility for bounded cases | Risk continues; requires explicit risk acceptance and close monitoring |

Do not recommend a broad block or shutdown based only on a single weak indicator. Record alternatives and trade-offs.

## 4. Eradication and remediation

After scope is sufficiently understood:
1. Identify the access path, malicious mechanism, persistence, affected credentials, and exploited weakness where evidence supports it.
2. Determine whether the threat is removed or merely inactive.
3. Plan remediation with the system owner and incident lead.
4. Rotate or revoke credentials/tokens when authorized and technically appropriate.
5. Remove malicious artifacts or persistence only through an approved process that preserves required evidence.
6. Patch or correct the exploited weakness and address configuration/control gaps.
7. Verify that remediation did not leave alternate access paths or affected assets untreated.

Do not provide or execute destructive cleanup steps without explicit authorization and a recovery plan.

## 5. Recovery

Recovery should be planned and verified:
- restore from a trusted, known-good source;
- validate system integrity and required security controls;
- confirm identity, network, application, and business functionality;
- reintroduce connectivity or users in a controlled sequence;
- apply enhanced monitoring for recurrence and residual indicators;
- document owner acceptance and remaining risks.

A successful reboot or service start is not sufficient evidence of recovery.

## 6. Monitoring and rollback

Define:
- monitored assets and telemetry sources;
- relevant behaviors and indicators;
- observation window and responsible owner;
- alert/escalation triggers;
- rollback criteria and restoration point;
- conditions for returning to investigation or containment.

## 7. SOC-LAB constraints

The baseline lab does not imply EDR isolation, automated response, or enterprise orchestration. Students should formulate and justify response recommendations. Instructors may implement approved actions using the actual lab controls and must document the precise configuration and reset steps. Never invent that an action was executed or successful.

## 8. References

- NIST SP 800-61r3: https://doi.org/10.6028/NIST.SP.800-61r3
- CISA response playbooks: https://www.cisa.gov/resources-tools/resources/federal-government-cybersecurity-incident-and-vulnerability-response-playbooks
