---
applyTo: "lab-environment/**/*,lectures/**/labs/**/*,lectures/**/installation-guides/**/*"
---

# Lab and installation documentation instructions

- State the target environment, topology, VM roles, network segments, prerequisites, resource requirements, versions, and assumptions.
- Use the approved baseline: VMware Workstation, Splunk Enterprise only, pfSense with integrated Suricata, Windows with Sysmon, Kali, and Ubuntu web server in a segmented DMZ. Mailpit is optional for local mail exercises.
- Use the documented `10.0.0.0` addressing plan; Kali is on `10.0.90.0/24`. Do not invent unspecified addresses.
- Provide ordered, copyable steps with expected output or verification after meaningful steps.
- Include firewall rules, data flows, required ports, and trust boundaries when relevant.
- Separate student-safe actions from instructor/admin actions.
- For potentially disruptive steps, include authorization, scope, impact, snapshot/backup, cleanup, and rollback.
- Include troubleshooting and recovery guidance.
- Mark whether steps are documented, statically checked, executed, or independently validated. Never claim execution without evidence.
- Do not place secrets, license files, private keys, or credentials in the repository.


## Bilingual authoring requirements

- Arabic and English are first-class project languages. Follow `governance/policies/bilingual-content-policy.md`.
- Keep paired documents in the same directory; English uses the canonical filename and Arabic appends `-ar` before the extension.
- Preserve stable IDs, technical meaning, commands, code, SPL, field names, configuration keys, numeric values, safety boundaries, evidence, and assessment requirements.
- Update both language variants together when meaning changes, or mark the counterpart `needs-update`/pending. Do not claim parity without reviewing both.
