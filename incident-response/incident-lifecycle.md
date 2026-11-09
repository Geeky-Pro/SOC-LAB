# Incident Lifecycle and State Management

> **Status:** draft  
> **Validation:** NOT VALIDATED

## 1. Model

SOC-LAB uses a practical operational workflow that can be mapped to NIST CSF 2.0's Detect, Respond, Recover, and continuous Improvement functions. Preparation (Govern, Identify, Protect) is ongoing and must not be treated as work that begins only after an alert.

The stages below are an operational teaching sequence, not a claim that all incidents follow a strict linear path. Activities may overlap, repeat, or be performed in parallel.

## 2. Operational stages

| Stage | Core questions | Typical outputs |
|---|---|---|
| Prepare and coordinate | Are roles, authority, contacts, systems, and procedures ready? | Contact path, approved procedures, exercise scope |
| Detect and report | What signal was observed, when, and by whom? | Alert/event reference, initial report |
| Validate and triage | Is the activity credible, relevant, and potentially harmful? | Triage notes, provisional category/severity |
| Analyze and scope | What happened, which assets/identities/data are involved, and what remains unknown? | Timeline, evidence matrix, scope statement |
| Decide and contain | What immediate risk reduction is justified and who can authorize it? | Decision record, approved containment actions |
| Eradicate and remediate | What access, mechanism, or weakness must be addressed? | Remediation plan and completion evidence |
| Recover | How can services be restored safely and monitored? | Recovery verification and monitoring plan |
| Close and improve | Are objectives met, records complete, and lessons assigned? | Closure rationale, lessons, action owners |

## 3. Incident states

Use these suggested record states. A state describes workflow progress; it is not a severity rating.

- `new`: report received; not yet triaged.
- `triage`: validation, prioritization, and initial scope underway.
- `investigating`: evidence analysis and scope development underway.
- `contained`: approved containment actions completed or risk otherwise controlled; explain residual risk.
- `eradication`: removal of malicious access/mechanisms and remediation underway.
- `recovering`: service restoration and enhanced monitoring underway.
- `monitoring`: restored environment is under defined observation.
- `closed`: closure criteria met and rationale recorded.
- `reopened`: new evidence or recurrence requires renewed response.
- `duplicate` / `false-positive` / `benign`: closed with explanation and link to the related record where applicable.

An incident may move backwards or return to investigation if new evidence invalidates prior assumptions.

## 4. Entry, exit, and transition controls

For each transition, record:
- timestamp and time zone;
- previous and new state;
- decision or evidence supporting the transition;
- person making or approving the decision;
- unresolved risks and next action.

Do not mark an incident contained merely because an alert stopped. Confirm whether the threat path is blocked and whether alternate access or affected assets remain.

Do not close an incident solely because a ticket was updated or a system was rebooted.

## 5. Closure criteria

Closure should be considered only when:
- the incident objective and scope are documented;
- containment and remediation actions have an outcome or an explicitly accepted residual risk;
- affected services have passed defined recovery checks;
- monitoring and ownership for remaining risks are defined;
- evidence references, timeline, communications, and approvals are recorded;
- follow-up actions have owners and due dates;
- the closure decision is authorized.

## 6. Improvement loop

Capture detection gaps, missing telemetry, procedural friction, unclear authority, recovery weaknesses, and training needs. Convert material findings into owned actions and feed them into curriculum, lab, detection, and governance updates.
