# L01-05 — Analyst Documentation and Evidence Discipline

[النسخة العربية](./l01-05-analyst-documentation-and-evidence-discipline-ar.md)

> **Status:** draft  
> **Module:** 01-soc-fundamentals  
> **Duration:** 60 minutes  
> **Outcomes:** LO-01-05  
> **Audience:** Entry-level SOC learners

## Learning outcomes

Learners will be able to:
1. Write a case note that another analyst can understand and reproduce.
2. Distinguish observed facts, analyst interpretation, decisions, and unknowns.
3. Reference evidence by source, time, and a usable locator.
4. Handle evidence responsibly and communicate limitations.

## 1. Why documentation is an operational control

A case record is part of the investigation, not paperwork added after the work. It supports:
- Continuity between analysts and shifts.
- Review of why a decision was made.
- Escalation to specialists, management, or service owners.
- Identification of missing evidence and monitoring gaps.
- Learning and improvement after an incident.

If another analyst cannot determine what was observed, when it happened, where the evidence came from, and why a decision was made, the case is difficult to trust or continue.

## 2. The FACTS structure

Use this classroom structure when writing a note:

- **F — Facts:** What was directly observed? Include source and timestamp.
- **A — Analysis:** What does the evidence suggest? State reasoning and confidence.
- **C — Context:** Which asset, account, business service, or approved change is relevant?
- **T — Tasks:** What was done, what remains, and who owns the next step?
- **S — Status:** Current disposition, escalation state, and unresolved questions.

This is a teaching mnemonic, not a formal external standard.

## 3. Separate observation from interpretation

Weak note:
> “The user was hacked. Many logins. Escalated.”

Improved note:
> “The identity event export records 12 failed sign-ins for synthetic account U-104 from source S-22 between 09:02 and 09:06 UTC, followed by one successful sign-in at 09:07 UTC. The source device is not identified in the supplied records. Password guessing is a possible explanation; user error and stale credentials remain alternatives. The case is escalated to the identity administrator to validate source ownership and successful sign-in context.”

The improved note:
- Identifies the source and time.
- Describes the observed sequence.
- Does not claim compromise without evidence.
- States alternatives and missing context.
- Names the requested next action.

## 4. Evidence references

A useful evidence reference includes:
- Evidence identifier or filename.
- Source system or dataset.
- Relevant time and timezone.
- Record ID, event ID, row number, query, or other locator.
- Collection/export method when relevant.
- Whether the artifact is synthetic, simulated, captured, or collected from a live system.

Example:
- Artifact: identity-events.csv
- Source: synthetic training pack, version 0.1
- Record locator: rows 14–26
- Time window: 09:02–09:07 UTC
- Nature: synthetic records; not collected from a real organization

Do not write “see logs” when the reader cannot tell which logs or records matter.

## 5. Time and timeline discipline

- Record the timezone; use UTC for normalized cross-source timelines where practical.
- Preserve the original timestamp when converting it.
- Note clock drift or uncertain timestamps.
- Distinguish event time from alert creation time, ingestion time, and analyst action time.
- Do not infer sequence solely from records whose clocks may differ.

A timeline should show both the event and the source that reported it.

## 6. Evidence handling and privacy

Follow organizational policy and applicable law. At this introductory level:
- Collect only evidence relevant to the authorized investigation.
- Do not copy unrelated personal information into a case.
- Keep original artifacts unchanged when preservation is required.
- Record how and when an artifact was obtained.
- Use approved storage and access controls.
- Do not share evidence through personal email, public file shares, or unapproved services.
- Use hashes when appropriate to identify file integrity, but do not claim that a hash alone proves provenance or legal chain of custody.
- Label synthetic, simulated, and real evidence distinctly.

This module teaches operational evidence discipline, not legal forensics or formal chain-of-custody certification.

## 7. Case note quality checklist

Before saving or handing off a note, check:
- [ ] Is the scope clear?
- [ ] Are facts traceable to sources and timestamps?
- [ ] Are facts separated from hypotheses?
- [ ] Are confidence and uncertainty stated?
- [ ] Are impact and urgency explained?
- [ ] Are completed actions and results recorded?
- [ ] Is the next action specific and assigned?
- [ ] Are privacy and authorization boundaries respected?
- [ ] Can another analyst reproduce the reasoning?

## 8. Workshop: repair a weak case note

**Weak note:** “Suspicious login from another country. User hacked. Close after reset.”

Learners should identify at least five problems and rewrite the note using the synthetic evidence pack. Consider:
- Is the location reliable?
- Is there a successful sign-in?
- Is the account privileged?
- Has the user or device owner confirmed the activity?
- Who authorized a reset?
- What evidence would justify closure?

## 9. Knowledge check

1. What is the difference between event time and ingestion time?
2. Why is “see logs” an inadequate evidence reference?
3. Does a file hash alone prove who collected a file and how? Explain.
4. What is the risk of copying unrelated personal data into a case?

## 10. Summary

- A case record enables continuity, accountability, and reproducibility.
- Record facts, analysis, context, tasks, and status separately.
- Evidence references need source, time, and a usable locator.
- Preserve privacy, authorization, provenance, and uncertainty.

## References

- NIST SP 800-61 Rev. 3 (April 2025) — https://csrc.nist.gov/pubs/sp/800/61/r3/final
- NIST CSF 2.0 — https://www.nist.gov/cyberframework
