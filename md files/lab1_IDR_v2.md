# Lab 01 (Revised v2): Security Operations, Logging Architecture & Centralization

> **Course:** Cybersecurity Operations (SOC Lab)  
> **Instructor:** Hussein Al-Selwi  
> **Total Slides:** 34 Slides  
> **HTML Source:** [`lab1_IDR_v2.html`](file:///c:/Users/alsslwy/Desktop/SOC%20LAB/lab1_IDR_v2.html)  

---

## 📑 Table of Contents

- [Slide 01: Security Operations Fundamentals](#slide-01-security-operations-fundamentals)
- [Slide 02: Domain Objectives](#slide-02-domain-objectives)
- [Slide 03: What is a SOC?](#slide-03-what-is-a-soc)
- [Slide 04: The SOC Operational Cycle](#slide-04-the-soc-operational-cycle)
- [Slide 05: The Three Pillars: PPT](#slide-05-the-three-pillars-ppt)
- [Slide 06: SOC Tiers & Roles](#slide-06-soc-tiers--roles)
- [Slide 07: Defending the CIA Triad](#slide-07-defending-the-cia-triad)
- [Slide 08: The Visibility Imperative](#slide-08-the-visibility-imperative)
- [Slide 09: Terminology: Log vs Event vs Alert vs Incident](#slide-09-terminology-log-vs-event-vs-alert-vs-incident)
- [Slide 10: Triage Truth Matrix: TP / FP / TN / FN](#slide-10-triage-truth-matrix-tp--fp--tn--fn)
- [Slide 11: Anatomy of a Log Entry](#slide-11-anatomy-of-a-log-entry)
- [Slide 12: Enterprise Log Landscape](#slide-12-enterprise-log-landscape)
- [Slide 13: Windows Logging Architecture](#slide-13-windows-logging-architecture)
- [Slide 14: Sysmon: Advanced Endpoint Telemetry](#slide-14-sysmon-advanced-endpoint-telemetry)
- [Slide 15: Linux Logging Architecture](#slide-15-linux-logging-architecture)
- [Slide 16: Network & Perimeter Telemetry](#slide-16-network--perimeter-telemetry)
- [Slide 17: Web App & Cloud Telemetry](#slide-17-web-app--cloud-telemetry)
- [Slide 18: Demo 1: Windows Authentication Analysis](#slide-18-demo-1-windows-authentication-analysis)
- [Slide 19: Demo 2: Process Auditing & Sysmon](#slide-19-demo-2-process-auditing--sysmon)
- [Slide 20: Demo 3: Linux Authentication Telemetry](#slide-20-demo-3-linux-authentication-telemetry)
- [Slide 21: Demo 4: Spotting Attacks in Web Logs](#slide-21-demo-4-spotting-attacks-in-web-logs)
- [Slide 22: The Centralization Dilemma](#slide-22-the-centralization-dilemma)
- [Slide 23: Centralization & Time Synchronization](#slide-23-centralization--time-synchronization)
- [Slide 24: Log Shipping: Agents vs Agentless](#slide-24-log-shipping-agents-vs-agentless)
- [Slide 25: The 6-Stage SIEM Pipeline](#slide-25-the-6-stage-siem-pipeline)
- [Slide 26: Integrated SOC Architecture](#slide-26-integrated-soc-architecture)
- [Slide 27: SIEM: Central Brain](#slide-27-siem-central-brain)
- [Slide 28: EDR & Host Defense](#slide-28-edr--host-defense)
- [Slide 29: Network Defenses: FW, IDS/IPS & NSM](#slide-29-network-defenses-fw-idsips--nsm)
- [Slide 30: SOAR, Case Management & TIP](#slide-30-soar-case-management--tip)
- [Slide 31: Walkthrough: Correlated Attack Scenario](#slide-31-walkthrough-correlated-attack-scenario)
- [Slide 32: Course Roadmap & Week 2 Lab Preview](#slide-32-course-roadmap--week-2-lab-preview)
- [Slide 33: Class Challenge: Analyst Triage Quiz](#slide-33-class-challenge-analyst-triage-quiz)
- [Slide 34: Key Takeaways & Homework](#slide-34-key-takeaways--homework)

---

## Slide 01: Security Operations Fundamentals

> **Slide Title:** `Security Operations Fundamentals`

> [!NOTE] 🎙️ **Instructor Lecture Notes & Teaching Guide**
> Welcome students to the course! Emphasize that SOC and Security Operations are the frontline battlefield of enterprise cyber defense. Everything starts with understanding what is happening on our systems. In this foundational lab, we will demystify the SOC, understand the true value of logs and telemetry, see live Windows and Linux logs in action, and explore how centralizing disparate data streams unlocks true enterprise visibility.

---

## Slide 02: Domain Objectives

> **Slide Title:** `Domain Objectives`

> [!NOTE] 🎙️ **Instructor Lecture Notes & Teaching Guide**
> Walk through these core competencies. Make it clear that this lab balances high-level concepts with actual hands-on terminal commands. By the end of today, every student will be able to look at raw log records and pinpoint exactly who did what, when, and how.

---

## Slide 03: What is a SOC?

> **Slide Title:** `What is a SOC?`

> [!NOTE] 🎙️ **Instructor Lecture Notes & Teaching Guide**
> Emphasize that a SOC is not just a room with big TV screens. It is an organizational capability. It operates 24/7/365 because attackers operate globally across all time zones. Explain the continuous dual posture: reacting to alerts while proactively hunting for hidden threats.

---

## Slide 04: The SOC Operational Cycle

> **Slide Title:** `The SOC Operational Cycle`

> [!NOTE] 🎙️ **Instructor Lecture Notes & Teaching Guide**
> Walk through the 4 steps left to right. Emphasize step 5: the Feedback Loop. When an analyst responds to a new attack technique, they don't just close the ticket; they create a new detection rule or tune existing alerts so the SOC detects it faster next time.

---

## Slide 05: The Three Pillars: PPT

> **Slide Title:** `The Three Pillars: PPT`

> [!NOTE] 🎙️ **Instructor Lecture Notes & Teaching Guide**
> Explain the Golden Rule of Security: 'A million-dollar SIEM without trained analysts is just an expensive hard drive full of unread text.' Technology alerts you, but People make the critical decisions and Processes guarantee consistency under pressure.

---

## Slide 06: SOC Tiers & Roles

> **Slide Title:** `SOC Tiers & Roles`

> [!NOTE] 🎙️ **Instructor Lecture Notes & Teaching Guide**
> Explain the escalation path. Tier 1 handles the deluge of incoming alerts (often hundreds a day). When something is confirmed true positive, it is escalated to Tier 2 for full containment. Tier 3 does not handle routine alerts; they proactively search for threats that bypassed automated detections entirely.

---

## Slide 07: Defending the CIA Triad

> **Slide Title:** `Defending the CIA Triad`

> [!NOTE] 🎙️ **Instructor Lecture Notes & Teaching Guide**
> Connect abstract CIA security theory to concrete SOC operational defense. Walk through how ransomware attacks Availability first, but modern double-extortion ransomware also steals data first, violating Confidentiality as well.

---

## Slide 08: The Visibility Imperative

> **Slide Title:** `The Visibility Imperative`

> [!NOTE] 🎙️ **Instructor Lecture Notes & Teaching Guide**
> This is the philosophical heart of the lecture. Explain that an analyst is essentially a detective. When a burglary occurs, detectives look for fingerprint evidence, timestamps, and witness accounts. In cybersecurity, logs are the only digital witness testimony we have. Without logs, an attack is completely invisible.

---

## Slide 09: Terminology: Log vs Event vs Alert vs Incident

> **Slide Title:** `Terminology: Log vs Event vs Alert vs Incident`

> [!NOTE] 🎙️ **Instructor Lecture Notes & Teaching Guide**
> Students often mix these terms up. Emphasize the funnel: Millions of raw logs reduce down to thousands of observable events. Detection rules turn some events into dozens of alerts. When an analyst confirms true malicious impact, it becomes an official Incident.

---

## Slide 10: Triage Truth Matrix: TP / FP / TN / FN

> **Slide Title:** `Triage Truth Matrix: TP / FP / TN / FN`

> [!NOTE] 🎙️ **Instructor Lecture Notes & Teaching Guide**
> Explain the four quadrants. Highlight that False Positives waste precious analyst time and cause 'alert fatigue'. But False Negatives are the true nightmare &mdash; an attacker is actively inside your network and not a single alarm fired.

---

## Slide 11: Anatomy of a Log Entry

> **Slide Title:** `Anatomy of a Log Entry`

> [!NOTE] 🎙️ **Instructor Lecture Notes & Teaching Guide**
> Show the anatomy breakdown. Highlight the difference between legacy unstructured text lines and modern structured JSON/Key-Value pairs. Explain that modern SIEM correlation relies heavily on normalized fields (like src_ip and dest_port).

---

## Slide 12: Enterprise Log Landscape

> **Slide Title:** `Enterprise Log Landscape`

> [!NOTE] 🎙️ **Instructor Lecture Notes & Teaching Guide**
> Provide an aerial view of an enterprise. Show that logs don't just come from Windows laptops. They come from firewalls, web servers, identity providers, switches, and SaaS cloud tenants. An analyst must be comfortable reading telemetry from all layers.

---

## Slide 13: Windows Logging Architecture

> **Slide Title:** `Windows Logging Architecture`

> [!NOTE] 🎙️ **Instructor Lecture Notes & Teaching Guide**
> Deconstruct Windows Event Logging (.evtx). Mention that it's a structured binary format located in C:\Windows\System32\winevt\Logs\. Walk through the essential Event IDs: 4624 (logon), 4625 (failed logon), 4688 (process created), 7045 (new service), and 1102 (audit log cleared).

---

## Slide 14: Sysmon: Advanced Endpoint Telemetry

> **Slide Title:** `Sysmon: Advanced Endpoint Telemetry`

> [!NOTE] 🎙️ **Instructor Lecture Notes & Teaching Guide**
> Explain why default Windows logs leave massive blind spots. Default Windows logs don't calculate file hashes, don't show network connections tied to PIDs, and don't log DNS queries. Microsoft Sysmon fills these exact gaps for free with a kernel-level driver.

---

## Slide 15: Linux Logging Architecture

> **Slide Title:** `Linux Logging Architecture`

> [!NOTE] 🎙️ **Instructor Lecture Notes & Teaching Guide**
> Explain the Linux logging philosophy: everything in Unix is a file! Show where authentication lives (/var/log/auth.log or /var/log/secure), explain syslog facilities and priorities, and introduce systemd-journald and auditd.

---

## Slide 16: Network & Perimeter Telemetry

> **Slide Title:** `Network & Perimeter Telemetry`

> [!NOTE] 🎙️ **Instructor Lecture Notes & Teaching Guide**
> Explain what network traffic sees that endpoints might hide. If malware disables local endpoint logging, network traffic cannot be erased because the packets literally crossed the wire. Introduce Firewalls, IDS/IPS (Snort/Suricata), and DNS logs.

---

## Slide 17: Web App & Cloud Telemetry

> **Slide Title:** `Web App & Cloud Telemetry`

> [!NOTE] 🎙️ **Instructor Lecture Notes & Teaching Guide**
> Explain that Web applications are the primary public-facing door into an organization. Deconstruct the Combined Log Format and show how web application firewalls (WAF) and CloudTrail/Entra ID logs complete modern enterprise visibility.

---

## Slide 18: Demo 1: Windows Authentication Analysis

> **Slide Title:** `Demo 1: Windows Authentication Analysis`

> [!NOTE] 🎙️ **Instructor Lecture Notes & Teaching Guide**
> Perform this live or explain it step-by-step. Have students open PowerShell as Administrator and run the Get-WinEvent command. Explain Logon Types: Type 2 is interactive (hands on keyboard), Type 3 is network (file share access), and Type 10 is Remote Desktop (RDP).

---

## Slide 19: Demo 2: Process Auditing & Sysmon

> **Slide Title:** `Demo 2: Process Auditing & Sysmon`

> [!NOTE] 🎙️ **Instructor Lecture Notes & Teaching Guide**
> Demonstrate how command lines reveal attacker intent. When an attacker runs 'powershell.exe -enc ...' or 'whoami', Event 4688 records it. Point out the crucial field: ParentProcessName. If Word or Excel spawns PowerShell, that is a 99% malicious macro execution!

---

## Slide 20: Demo 3: Linux Authentication Telemetry

> **Slide Title:** `Demo 3: Linux Authentication Telemetry`

> [!NOTE] 🎙️ **Instructor Lecture Notes & Teaching Guide**
> Demonstrate Linux terminal commands. Show how a failed sudo command immediately registers in /var/log/auth.log with the keyword 'authentication failure'. Show how analysts use grep and awk to quickly find brute-force attacker IPs.

---

## Slide 21: Demo 4: Spotting Attacks in Web Logs

> **Slide Title:** `Demo 4: Spotting Attacks in Web Logs`

> [!NOTE] 🎙️ **Instructor Lecture Notes & Teaching Guide**
> Demonstrate how web server logs catch attacks. Show students that an attacker's SQL injection payload or directory traversal is recorded in plain text in the web server access log. Point out the single quotes, UNION SELECT, and ../ in the URI.

---

## Slide 22: The Centralization Dilemma

> **Slide Title:** `The Centralization Dilemma`

> [!NOTE] 🎙️ **Instructor Lecture Notes & Teaching Guide**
> Explain the nightmare of 'islands of data'. Ask the class: 'If a bank has 2,000 servers, can an analyst log into each server one by one to investigate a breach?' Obviously not. Furthermore, if a hacker gets root on a server, what's the first thing they do? They clear the logs. If logs are stored only locally, the evidence is gone forever.

---

## Slide 23: Centralization & Time Synchronization

> **Slide Title:** `Centralization & Time Synchronization`

> [!NOTE] 🎙️ **Instructor Lecture Notes & Teaching Guide**
> Explain the solution: logs must be shipped off the endpoint the instant they are generated to a tamper-proof central store. Stress the critical role of NTP. If clock skew is off by even 3 minutes, correlation rules fail and court-admissible evidence is compromised.

---

## Slide 24: Log Shipping: Agents vs Agentless

> **Slide Title:** `Log Shipping: Agents vs Agentless`

> [!NOTE] 🎙️ **Instructor Lecture Notes & Teaching Guide**
> Explain how logs physically get from the endpoint to the SIEM. Compare Agent-based (Splunk Universal Forwarder, Elastic Agent, Wazuh) with Agentless (Syslog UDP/TCP, WEF, API pull). Explain trade-offs: agents give local caching and compression, but network appliances only speak Syslog.

---

## Slide 25: The 6-Stage SIEM Pipeline

> **Slide Title:** `The 6-Stage SIEM Pipeline`

> [!NOTE] 🎙️ **Instructor Lecture Notes & Teaching Guide**
> Walk through the 6 stages left to right. Explain Parsing & Normalization: turning vendor-specific text into standard fields. Explain Enrichment: looking up an IP in GeoIP or Threat Intel. Explain Correlation: matching multiple events across time windows to trigger an Alert.

---

## Slide 26: Integrated SOC Architecture

> **Slide Title:** `Integrated SOC Architecture`

> [!NOTE] 🎙️ **Instructor Lecture Notes & Teaching Guide**
> This architectural diagram pulls everything together into one unified picture. Show how Endpoints, Networks, Applications, and Cloud streams flow through forwarders into the central SIEM. Show how TIP feeds threat intel into SIEM, and how SIEM triggers SOAR playbooks and case management for the analyst.

---

## Slide 27: SIEM: Central Brain

> **Slide Title:** `SIEM: Central Brain`

> [!NOTE] 🎙️ **Instructor Lecture Notes & Teaching Guide**
> Explain that SIEM is the heart of the SOC analyst's daily workflow. An analyst spends 80% of their shift inside the SIEM search bar. Mention market leaders: Splunk (which we deploy in Lab 2 and use throughout the course), Microsoft Sentinel, IBM QRadar, and Elastic Security.

---

## Slide 28: EDR & Host Defense

> **Slide Title:** `EDR & Host Defense`

> [!NOTE] 🎙️ **Instructor Lecture Notes & Teaching Guide**
> Distinguish between traditional Antivirus and modern EDR. AV looks only for known file hashes (signatures). If malware is fileless or executes in memory, AV misses it completely. EDR records all process behaviors and allows the analyst to remotely isolate the computer from the network with one click.

---

## Slide 29: Network Defenses: FW, IDS/IPS & NSM

> **Slide Title:** `Network Defenses: FW, IDS/IPS & NSM`

> [!NOTE] 🎙️ **Instructor Lecture Notes & Teaching Guide**
> Review network controls. A firewall is a gatekeeper. An IDS is an alarm bell (passive). An IPS is an active guard standing at the gate resetting malicious TCP streams. NSM tools like Zeek and Wireshark capture full conversations for packet forensics.

---

## Slide 30: SOAR, Case Management & TIP

> **Slide Title:** `SOAR, Case Management & TIP`

> [!NOTE] 🎙️ **Instructor Lecture Notes & Teaching Guide**
> Explain the remaining parts of the SOC toolkit. SOAR automates repetitive tasks (like looking up an IP on VirusTotal). Case management tracks evidence for legal and regulatory compliance. Threat Intelligence Platforms (TIP) provide known attacker IOCs to enrich alerts.

---

## Slide 31: Walkthrough: Correlated Attack Scenario

> **Slide Title:** `Walkthrough: Correlated Attack Scenario`

> [!NOTE] 🎙️ **Instructor Lecture Notes & Teaching Guide**
> This slide connects every single concept taught today. Walk through the 4 steps. Emphasize: Look at log 1 alone (just a port scan). Look at log 2 alone (just an error). Look at log 3 alone (just PowerShell). None of them scream 'massive breach' on their own. But when the SIEM correlates all 4 across the 30-minute window, it reveals the complete attack kill chain!

---

## Slide 32: Course Roadmap & Week 2 Lab Preview

> **Slide Title:** `Course Roadmap & Week 2 Lab Preview`

> [!NOTE] 🎙️ **Instructor Lecture Notes & Teaching Guide**
> Walk students through the semester roadmap. Then explain next week's lab: Lab 2 is our hands-on Workstation Setup. Emphasize that we use native Windows host tooling (Splunk Enterprise Free, Wireshark, Sysinternals) because it runs blazingly fast without requiring heavy virtual machines. Give them the prep homework.

---

## Slide 33: Class Challenge: Analyst Triage Quiz

> **Slide Title:** `Class Challenge: Analyst Triage Quiz`

> [!NOTE] 🎙️ **Instructor Lecture Notes & Teaching Guide**
> Engage the classroom! Ask individual students to classify each of the 4 rapid-fire scenarios. Then have them inspect the raw log box and identify the Attacker IP, Target User, and what kind of attack was taking place.

---

## Slide 34: Key Takeaways & Homework

> **Slide Title:** `Key Takeaways & Homework`

> [!NOTE] 🎙️ **Instructor Lecture Notes & Teaching Guide**
> Congratulate the students on completing their first SOC Lab session! Review the key takeaways and assign the homework. The homework involves querying their own machine using PowerShell and optionally completing the recommended free TryHackMe rooms to build confidence before next week's installation lab.

---
