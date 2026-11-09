# Module Reference Catalog

> **Status:** draft — curated starting points for lesson development; verify the relevant page and version again when producing final teaching assets.
> **Review date:** 2026-11-10
> **Rule:** A reference is a research starting point, not evidence that a particular lab configuration or software version has been validated. Cite only the page/edition actually consulted for the claim being taught.

## Program-wide foundations
- NIST Cybersecurity Framework (CSF) 2.0 — https://www.nist.gov/cyberframework
- NIST SP 800-61 Rev. 3 (April 2025) — https://csrc.nist.gov/pubs/sp/800/61/r3/final
- MITRE ATT&CK, Getting Started — https://attack.mitre.org/resources/
- NIST NICE Framework Resource Center — https://www.nist.gov/itl/applied-cybersecurity/nice/nice-framework-resource-center

## Module 01 — SOC Fundamentals & Security Operations
Relevant lessons: L01-01 to L01-06.
- NIST CSF 2.0 — https://www.nist.gov/cyberframework
- NIST NICE Framework — https://www.nist.gov/itl/applied-cybersecurity/nice/nice-framework-resource-center
- NIST SP 800-61 Rev. 3 — https://csrc.nist.gov/pubs/sp/800/61/r3/final
- MITRE ATT&CK Getting Started — https://attack.mitre.org/resources/
Use these to frame security functions, workforce capabilities, incident terminology, and evidence-led operations. Educational severity bands are not universal policy.

## Module 02 — SOC Lab Architecture & Deployment
Relevant lessons: L02-01 to L02-06.
- Broadcom: Installing VMware Workstation Pro — https://knowledge.broadcom.com/external/article/387947
- Broadcom: Download and license VMware Desktop Hypervisor — https://knowledge.broadcom.com/external/article/368667
- Netgate pfSense Documentation — https://docs.netgate.com/pfsense/en/latest/
- Netgate package list (includes Suricata) — https://docs.netgate.com/pfsense/en/latest/packages/list.html
- Splunk Enterprise documentation — https://help.splunk.com/en/splunk-enterprise
- Splunk Search Tutorial — https://help.splunk.com/en/splunk-enterprise/search/search-tutorial/9.2/introduction/about-the-search-tutorial
- Microsoft Sysmon overview — https://learn.microsoft.com/en-us/windows/security/operating-system-security/sysmon/overview
Verify exact versions, license terms, installation procedures, package support, forwarding methods, ports, indexes, sourcetypes, and fields against the deployed environment.

## Module 03 — Endpoint Detection & Investigation
Relevant lessons: L03-01 to L03-06.
- Microsoft Sysmon overview — https://learn.microsoft.com/en-us/windows/security/operating-system-security/sysmon/overview
- Understanding Sysmon events — https://learn.microsoft.com/en-us/windows/security/operating-system-security/sysmon/sysmon-events
- Enable and configure Sysmon — https://learn.microsoft.com/en-us/windows/security/operating-system-security/sysmon/how-to-enable-sysmon
- Windows Event Log — https://learn.microsoft.com/en-us/windows/win32/wes/windows-event-log
- Splunk Search Tutorial — https://help.splunk.com/en/splunk-enterprise/search/search-tutorial/9.2/introduction/about-the-search-tutorial
Sysmon records observations; it does not itself determine maliciousness or block activity.

## Module 04 — Phishing & Email Security Investigation
Relevant lessons: L04-01 to L04-06.
- RFC 5321 SMTP — https://www.rfc-editor.org/rfc/rfc5321
- RFC 5322 Internet Message Format — https://www.rfc-editor.org/rfc/rfc5322
- RFC 7208 SPF — https://www.rfc-editor.org/rfc/rfc7208
- RFC 6376 DKIM — https://www.rfc-editor.org/rfc/rfc6376
- RFC 7489 DMARC — https://www.rfc-editor.org/rfc/rfc7489
- Mailpit documentation — https://mailpit.axllent.org/docs/
Use defanged URLs and inert/sanitized attachment metadata. Never ask learners to open unknown links or execute attachments.

## Module 05 — Network Security Monitoring & Analysis
Relevant lessons: L05-01 to L05-06.
- Wireshark User's Guide — https://www.wireshark.org/docs/wsug_html/
- Wireshark display filters — https://www.wireshark.org/docs/wsug_html_chunked/ChWorkDisplayFilterSection
- RFC 791 IPv4 — https://www.rfc-editor.org/rfc/rfc791
- RFC 9293 TCP — https://www.rfc-editor.org/rfc/rfc9293
- RFC 1035 DNS — https://www.rfc-editor.org/rfc/rfc1035
- RFC 9110 HTTP Semantics — https://www.rfc-editor.org/rfc/rfc9110
Check RFC status/updates during production. Distinguish packet visibility from application payload visibility, especially for encrypted sessions.

## Module 06 — Network Intrusion Detection & Prevention
Relevant lessons: L06-01 to L06-06.
- Suricata User Guide — https://docs.suricata.io/
- Suricata rules documentation — https://docs.suricata.io/en/latest/rules/
- Suricata EVE JSON output — https://docs.suricata.io/en/latest/output/eve/eve-json-output.html
- Netgate pfSense Documentation — https://docs.netgate.com/pfsense/en/latest/
Verify the current pfSense Suricata package documentation and supported IPS/inline mode for the exact pfSense release, interface, and platform. Do not infer prevention capability from alert-only telemetry.

## Module 07 — Web Security Monitoring & Investigation
Relevant lessons: L07-01 to L07-06.
- RFC 9110 HTTP Semantics — https://www.rfc-editor.org/rfc/rfc9110
- OWASP Top 10:2025 — https://owasp.org/Top10/
- OWASP Logging Cheat Sheet — https://cheatsheetseries.owasp.org/cheatsheets/Logging_Cheat_Sheet.html
- Splunk Search Tutorial — https://help.splunk.com/en/splunk-enterprise/search/search-tutorial/9.2/introduction/about-the-search-tutorial
OWASP is awareness/risk vocabulary, not proof that a suspicious request succeeded.

## Module 08 — Incident Response
Relevant lessons: L08-01 to L08-06.
- NIST SP 800-61 Rev. 3 (2025) — https://csrc.nist.gov/pubs/sp/800/61/r3/final
- NIST CSF 2.0 — https://www.nist.gov/cyberframework
- NIST Incident Response Project — https://csrc.nist.gov/projects/incident-response
SP 800-61 Rev. 3 supersedes Rev. 2.

## Module 09 — Attack Simulation & Detection Validation
Relevant lessons: L09-01 to L09-06.
- MITRE ATT&CK — https://attack.mitre.org/
- Atomic Red Team documentation — https://www.atomicredteam.io/docs/atomic-red-team
- MITRE Caldera documentation — https://caldera.readthedocs.io/en/stable/
- NIST SP 800-61 Rev. 3 — https://csrc.nist.gov/pubs/sp/800/61/r3/final
Select only low-risk tests with explicit authorization, prerequisites, scope, expected side effects, cleanup, and rollback.

## Module 10 — Integrated Threat Investigation: Operation Shadow Access
Relevant lessons: L10-01 to L10-07.
- Microsoft Sysmon events — https://learn.microsoft.com/en-us/windows/security/operating-system-security/sysmon/sysmon-events
- Wireshark User's Guide — https://www.wireshark.org/docs/wsug_html/
- Suricata User Guide — https://docs.suricata.io/
- RFC 5322 — https://www.rfc-editor.org/rfc/rfc5322
- Splunk Search Tutorial — https://help.splunk.com/en/splunk-enterprise/search/search-tutorial/9.2/introduction/about-the-search-tutorial
- NIST SP 800-61 Rev. 3 — https://csrc.nist.gov/pubs/sp/800/61/r3/final
- MITRE ATT&CK — https://attack.mitre.org/
Identify every artifact as captured, synthetic, simulated, or collected in the lab. Email evidence may be a sanitized .eml file; Mailpit remains optional.

## Module 11 — SOC Capstone Project
Relevant lessons: L11-01 to L11-05.
Use the module-specific references above according to the assigned evidence domains, plus NIST SP 800-61 Rev. 3, NIST CSF 2.0, and MITRE ATT&CK. Include actual sources in each scenario pack.

## Reference maintenance
- Check current edition/revision and access date during lesson production.
- Prefer standards bodies and primary vendor/project documentation.
- Link each source to the lesson topic or claim it supports.
- Do not use marketing pages as the sole source for technical behavior.
- This catalog does not imply lab-specific versions or configurations are validated.
