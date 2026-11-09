# Incident Communications and Escalation

> **Status:** draft  
> **Validation:** NOT VALIDATED

## 1. Purpose

Clear communications help decision-makers understand what is known, what is uncertain, what is at risk, and what decision is needed. Communication must be timely, factual, authorized, and appropriately restricted.

## 2. Communication principles

1. Use approved incident channels and access controls.
2. Share information on a need-to-know basis.
3. Separate facts, hypotheses, and unverified reports.
4. State timestamps with time zone.
5. Avoid unnecessary personal data, secrets, exploit details, or raw evidence in broad status messages.
6. Identify the requested decision, decision owner, and deadline.
7. Maintain a record of important notifications and decisions.
8. Do not make external statements or breach notifications unless authorized.

## 3. Escalation path

Adapt this sequence to the organization's actual roles:
1. SOC analyst → shift lead / incident lead.
2. Incident lead → technical owner and designated decision authority.
3. Decision authority → privacy, legal, communications, executive, or external partners as required by approved policy.
4. Incident lead → recovery/service owner for restoration and monitoring.
5. Incident lead → lessons-learned owners after stabilization.

SOC-LAB exercises should route escalation to the instructor or explicitly assigned role. Learners must not contact real third parties.

## 4. Status update structure

A concise update should include:
- incident ID, current state, category, and provisional severity;
- what happened and when (facts only);
- affected assets/services/data and known scope;
- current impact and whether activity is ongoing;
- actions completed and their verified outcomes;
- actions proposed, required approvals, and decision deadline;
- key unknowns and next investigative step;
- incident lead and next update time.

## 5. Decision log

Record the decision, options considered, rationale, risk accepted, approver, timestamp, implementation owner, and outcome. If the action was not executed, state that clearly.

## 6. External and regulated communications

Notification obligations depend on jurisdiction, contracts, sector, data type, and organizational policy. This repository does not define legal deadlines or determine whether a reportable breach occurred. Escalate these questions to qualified legal/privacy/compliance personnel.

## 7. Reference

- NIST SP 800-61r3: https://doi.org/10.6028/NIST.SP.800-61r3
