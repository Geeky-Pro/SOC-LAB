# L01-04 — SOC Workflow, Escalation, and Communication

[النسخة العربية](./l01-04-soc-workflow-escalation-and-communication-ar.md)

> **Status:** draft  
> **Module:** 01-soc-fundamentals  
> **Duration:** 60 minutes  
> **Outcomes:** LO-01-01, LO-01-04  
> **Audience:** Entry-level SOC learners

## Learning outcomes

Learners will be able to:
1. Describe how alerts and cases move through a SOC queue.
2. Prioritize a set of cases using evidence, impact, urgency, and confidence.
3. Identify when and to whom a case should be escalated.
4. Produce a concise handoff that enables the next analyst to continue without repeating basic work.

## 1. From alert to owned work

A SOC queue is a controlled view of work requiring attention. A queue item should have, as applicable:
- Unique alert or case identifier.
- Detection/source and time received.
- Affected asset, account, service, or user.
- Current owner and status.
- Priority or severity according to local policy.
- Next action and due time, if defined.
- Escalation or communication history.

A queue is not a substitute for a case record. The queue helps manage work; the case preserves investigation details and decisions.

## 2. A simplified case workflow

1. **Receive:** an alert or report enters the queue.
2. **Assign:** ownership is established.
3. **Acknowledge:** an analyst confirms the item is being handled.
4. **Triage:** validity, scope, context, and urgency are assessed.
5. **Investigate:** evidence is collected and hypotheses are tested.
6. **Escalate or resolve:** the case is routed or closed with a supported disposition.
7. **Handoff:** open work, evidence, risks, and next steps are transferred.
8. **Review:** recurring issues and lessons inform improvement.

Real SOCs may use different statuses, queues, automation, and ownership rules. Do not treat this list as a universal ticketing workflow.

## 3. Severity, priority, impact, urgency, and confidence

These terms are related but should not be used as synonyms.

- **Severity:** a classification of how serious the event or condition is under a defined scheme.
- **Priority:** the order in which work should be handled, considering urgency, impact, confidence, and operational context.
- **Impact:** the actual or potential harm to systems, users, data, or business operations.
- **Urgency:** how quickly action is needed.
- **Confidence:** how strongly the evidence supports the current interpretation.

A high-severity technical alert may be low priority if it is confirmed as a harmless test. A medium-confidence alert involving a critical identity may require rapid validation. The organization must define its own scales and thresholds.

### Example training matrix

This is an illustrative classroom aid, not an operational policy:

| Situation | Confidence | Potential impact | Urgency | Suggested handling |
|---|---|---|---|---|
| Repeated failures on a standard account; source unknown | Medium | Medium | Medium | Validate source and successful sign-in context |
| Confirmed unauthorized access to privileged account | High | High | High | Immediate escalation through approved incident path |
| Known approved maintenance matching an alert | High benign context | Low | Low | Document validation and close according to policy |
| Suspicious activity on a critical service; evidence incomplete | Low–medium | High | High for validation | Rapid owner/specialist escalation while preserving uncertainty |

Do not calculate priority from a made-up universal formula. Use the approved organizational matrix where one exists.

## 4. Escalation

Escalate when the issue exceeds the analyst's authority, expertise, or available evidence, or when policy requires prompt notification.

Common triggers include:
- Privileged or executive account involvement.
- Critical system or business service affected.
- Evidence of successful unauthorized access.
- Activity continuing or spreading.
- Potential data exposure or safety impact.
- Multiple users, hosts, or locations involved.
- Conflicting evidence or a need for specialist investigation.
- A required response deadline or notification threshold.
- A proposed action that may disrupt business operations.

An escalation should say why it is being escalated, what is known, what is unknown, what has already been done, what is needed, and how quickly a decision is required.

## 5. Handoff communication

A useful handoff is concise but complete. Use this structure:

1. **Case and status:** identifier, owner, current state.
2. **Summary:** one or two sentences describing the issue.
3. **Scope:** affected account, asset, service, and time window.
4. **Facts:** evidence-backed observations with source and timestamps.
5. **Assessment:** current hypothesis and confidence.
6. **Impact/urgency:** why the case matters and how soon action is needed.
7. **Actions completed:** checks performed and their results.
8. **Open questions:** unknowns and alternative explanations.
9. **Next action:** a specific task, responsible role, and requested timeframe.
10. **Authority/constraints:** approvals or business owners required.

Avoid vague phrases such as “looks bad,” “probably hacked,” or “please check.” Avoid long unfiltered log dumps without explaining what matters.

## 6. Worked handoff example

**Case:** SOC-TRAIN-014  
**Status:** Escalated for identity validation  
**Summary:** Multiple failed sign-ins to a standard account were followed by a successful sign-in. Source ownership is not yet confirmed.

**Scope and facts**
- Account: U-104 (synthetic training identity).
- Time: 09:02–09:07 UTC, 10 November 2026 (synthetic exercise time).
- Identity records: 12 failures from source S-22; one success follows.
- Device ownership and user confirmation are not available in the exercise pack.

**Assessment**
- Password guessing is possible but not confirmed.
- User error and stale credentials remain alternatives.
- Confidence: medium that the activity warrants further review; low that compromise is established.

**Impact and urgency**
- Standard account; no privileged role is indicated in current records.
- Validate promptly because a successful sign-in followed the failures.

**Completed**
- Confirmed the event sequence and normalized the exercise timestamps to UTC.
- Checked the supplied account record; no privilege flag is present.

**Requested next action**
- Identity administrator to confirm source S-22 ownership and successful sign-in context.
- Escalate to the incident lead if the source is unrecognized or additional unauthorized activity is found.

## 7. Queue-prioritization exercise

Prioritize the four cases in the student guide. Explain:
- Which case should be handled first and why.
- Which case needs escalation now.
- Which case can wait for routine validation.
- What additional context could change your ordering.

There may be more than one defensible ordering. Credit the reasoning and evidence, not an unexplained single ranking.

## 8. Knowledge check

1. Why is priority not always equal to severity?
2. Name three escalation triggers.
3. What five elements make a handoff actionable?
4. Why should a handoff include unknowns and alternatives?

## 9. Summary

- Queue management provides ownership and work control; the case record preserves the investigation.
- Severity, priority, impact, urgency, and confidence are distinct.
- Escalation is driven by evidence, impact, urgency, expertise, and authority.
- A good handoff enables continuity and makes uncertainty visible.

## References

- NIST SP 800-61 Rev. 3 (April 2025) — https://csrc.nist.gov/pubs/sp/800/61/r3/final
- NIST CSF 2.0 — https://www.nist.gov/cyberframework
