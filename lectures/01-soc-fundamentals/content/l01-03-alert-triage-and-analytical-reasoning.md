# L01-03 — Alert Triage and Analytical Reasoning

> **Status:** draft  
> **Module:** 01-soc-fundamentals  
> **Duration:** 60 minutes  
> **Outcomes:** LO-01-02, LO-01-03  
> **Audience:** Entry-level SOC learners

## Learning outcomes

Learners will be able to:
1. Apply a repeatable first-pass triage workflow.
2. Separate observed facts from hypotheses and unknowns.
3. Explain confidence, impact, and urgency without treating them as interchangeable.
4. Recommend a proportionate next step and record why.

## 1. What triage is for

Triage is the structured initial assessment of an alert or report. The analyst determines whether the alert is understandable, relevant, within scope, and important enough for further investigation or escalation.

Triage is not simply closing alerts quickly. It is also not a full forensic investigation. It should establish what is known, what is not known, what needs checking next, and whether the issue should be escalated now.

## 2. A repeatable first-pass workflow

Use this six-step workflow as a training aid. Adapt it to the organization's approved procedures.

### Step 1 — Validate the alert record
- Confirm the alert identifier and detection/source.
- Check that the alert is not duplicated or malformed.
- Confirm the time window and timezone.
- Identify which system, account, asset, or network entity is involved.
- Record missing or unreliable fields.

### Step 2 — Confirm scope and authorization
- Is the affected asset or account part of the monitored environment?
- Is the activity within the approved investigation scope?
- Does the analyst have permission to access the relevant evidence?
- Are there privacy, business, or safety constraints?

### Step 3 — Gather context
Use available, authorized context such as:
- Asset owner and business criticality.
- Account type and privilege level.
- Known maintenance or change windows.
- Expected source devices, network locations, and user behavior.
- Related alerts or events in the same time window.
- Relevant ticket, change, or service records.

Do not assume that unfamiliar means malicious. Do not assume that familiar means safe.

### Step 4 — Separate facts, hypotheses, and unknowns

| Category | Meaning | Example |
|---|---|---|
| Fact | Directly supported by an observed record or verified source. | “The identity log shows 12 failed attempts.” |
| Hypothesis | A possible explanation that still needs testing. | “The account may be targeted by password guessing.” |
| Unknown | Information needed but not yet available or verified. | “The source device owner is not confirmed.” |
| Finding | A conclusion supported by the evidence currently available. | “The attempts came from the approved test host.” |

Write the source and timestamp beside important facts. A hypothesis should never be rewritten as a fact merely because it sounds plausible.

### Step 5 — Assess confidence, impact, and urgency separately

- **Confidence:** How strongly does the available evidence support the current interpretation?
- **Impact:** What could be affected if the activity is malicious or continues?
- **Urgency:** How quickly is action or escalation needed to prevent harm or preserve options?

These are different dimensions. An alert may have high potential impact but low confidence; it may still deserve rapid validation. A high-confidence benign explanation may reduce urgency, but the evidence and rationale must be recorded.

Consider:
- Asset criticality and business function.
- Privilege and reach of the affected identity.
- Evidence of successful access or execution.
- Number of affected systems or users.
- Whether activity is ongoing.
- Data sensitivity and possible business impact.
- Detection quality and corroborating sources.

### Step 6 — Choose a defensible disposition

Possible training dispositions:
- **Benign / expected:** evidence supports authorized or routine activity.
- **False positive:** the detection did not correctly represent its intended condition.
- **Suspicious — investigate:** meaningful uncertainty or indicators remain.
- **Escalate:** severity, impact, authority, or specialist needs require another role.
- **Confirmed incident:** organizational incident criteria are met and the authorized process is initiated.

Use the organization's actual case statuses and definitions in production. These labels are course examples, not a universal taxonomy.

## 3. Worked example

**Alert:** Repeated failed sign-ins for a standard user account.

**Initial facts:**
- 12 failed sign-ins were recorded over four minutes.
- The records identify one source address.
- A successful sign-in followed.
- The device owner and location have not been validated.

**Possible hypotheses:**
- User mistyped a password and then succeeded.
- A stale application repeatedly attempted authentication.
- An unauthorized party guessed the password and succeeded.
- A shared device or NAT address makes attribution ambiguous.

**Next checks:**
1. Confirm the account identity and privilege.
2. Check whether the source device is known and assigned to the user.
3. Review the successful sign-in context.
4. Search for related authentication activity involving the same account or source.
5. Ask the authorized identity or service owner to validate expected activity.
6. Escalate promptly if the account is privileged, activity is ongoing, or evidence indicates unauthorized access.

**Example triage statement:**
> “The identity source recorded 12 failed sign-ins for user account U-104 from source S-22 between 09:02 and 09:06 UTC, followed by one successful sign-in at 09:07 UTC. The source device and user context are not yet verified. Potential password guessing is one hypothesis; user error and stale credentials remain alternatives. Validate source ownership and review the successful sign-in context before final disposition. Escalate sooner if the account is privileged or additional evidence suggests unauthorized access.”

## 4. Avoid common analytical errors

| Error | Why it is weak | Better practice |
|---|---|---|
| Anchoring | The first explanation dominates later reasoning. | Record at least one plausible alternative. |
| Confirmation bias | Only evidence supporting the initial hypothesis is sought. | Seek confirming and disconfirming evidence. |
| Overconfidence | Uncertainty is hidden from the next analyst. | State confidence and missing evidence explicitly. |
| Context blindness | A technical signal is interpreted without business context. | Check asset, identity, owner, and change context. |
| Premature closure | An alert is closed before the key question is answered. | Define closure criteria and record the basis. |
| Severity inflation | Every unusual event is called critical. | Separate impact, urgency, and confidence. |

## 5. Guided practice

Using the synthetic record in the student guide:
1. Identify the alert source and time window.
2. Write three facts.
3. Write two hypotheses and one alternative explanation.
4. List at least three unknowns.
5. Assess confidence, impact, and urgency separately.
6. Recommend the next action and escalation trigger.
7. State what evidence would change your conclusion.

## 6. Knowledge check

1. Why can a high-impact alert still have low confidence?
2. What is the difference between urgency and impact?
3. Give one example of disconfirming evidence for a password-guessing hypothesis.
4. What must be recorded before closing a case as benign?

## 7. Summary

- Validate the record, scope, and context before drawing conclusions.
- Facts, hypotheses, unknowns, and findings are different.
- Confidence, impact, and urgency must be assessed separately.
- A disposition should explain evidence, reasoning, next action, and limitations.

## References

- NIST SP 800-61 Rev. 3 (April 2025) — https://csrc.nist.gov/pubs/sp/800/61/r3/final
- NIST Incident Response Project — https://csrc.nist.gov/projects/incident-response
- NIST CSF 2.0 — https://www.nist.gov/cyberframework
