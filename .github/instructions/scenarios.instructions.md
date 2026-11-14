---
applyTo: "lectures/**/scenarios/**/*,lectures/**/detections/**/*,detection-engineering/**/*,incident-response/**/*"
---

# Scenario, detection, and response instructions

- Define a clear learning purpose, scenario narrative, authorized scope, prerequisites, and expected duration.
- Specify attacker/emulation actions only for the isolated authorized lab; include expected impact and cleanup.
- Map activity to observable telemetry and identify the exact log sources, fields, event IDs, network evidence, or application records expected.
- Provide a timeline/injects, investigation questions, hypotheses, pivots, expected reasoning, and evidence-based conclusions.
- Include detection logic or searches only with field assumptions, data-source prerequisites, test cases, and known limitations.
- Explain false-positive considerations and how an analyst should validate findings.
- Provide response decisions, containment options, recovery, and debrief questions where relevant.
- Map ATT&CK techniques only when the behavior is genuinely supported by the scenario; do not force mappings.
- Keep scenario-specific content in its module; move reusable standards to shared root sections.
- Never claim a detection is validated unless test evidence is included.


## Bilingual authoring requirements

- Arabic and English are first-class project languages. Follow `governance/policies/bilingual-content-policy.md`.
- Keep paired documents in the same directory; English uses the canonical filename and Arabic appends `-ar` before the extension.
- Preserve stable IDs, technical meaning, commands, code, SPL, field names, configuration keys, numeric values, safety boundaries, evidence, and assessment requirements.
- Update both language variants together when meaning changes, or mark the counterpart `needs-update`/pending. Do not claim parity without reviewing both.
