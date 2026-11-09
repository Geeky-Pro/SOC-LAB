# Lab 03: Phishing Analysis Part II — Advanced Header & URL Investigation

> **Course:** Cybersecurity Operations (SOC Lab)  
> **Instructor:** Hussein Al-Selwi  
> **Total Slides:** 15 Slides  
> **Source Presentation:** `Lab3_Phishing_Analysis 2.html`  

### 📋 Overview
Hands-on investigation workflows for inspecting authentic vs spoofed email headers, tracing multi-hop Received lines from bottom to top, identifying Return-Path discrepancies, and performing safe URL defanging.

---

## 📑 Table of Contents

- [Slide 01: Introduction](#slide-01-introduction)
- [Slide 02: Recap & Objectives](#slide-02-recap-objectives)
- [Slide 03: Anatomy of a URL](#slide-03-anatomy-of-a-url)
- [Slide 04: URL Analysis Workflow](#slide-04-url-analysis-workflow)
- [Slide 05: URL Analysis Tools](#slide-05-url-analysis-tools)
- [Slide 06: Static vs Dynamic Analysis](#slide-06-static-vs-dynamic-analysis)
- [Slide 07: Static Analysis Techniques](#slide-07-static-analysis-techniques)
- [Slide 08: Dynamic Analysis & Sandboxing](#slide-08-dynamic-analysis-sandboxing)
- [Slide 09: Automated Analysis Tools](#slide-09-automated-analysis-tools)
- [Slide 10: Defense Measures Overview](#slide-10-defense-measures-overview)
- [Slide 11: Reactive Defense Actions](#slide-11-reactive-defense-actions)
- [Slide 12: Proactive Defense Measures](#slide-12-proactive-defense-measures)
- [Slide 13: Documentation & Reporting](#slide-13-documentation-reporting)
- [Slide 14: Incident Report Structure](#slide-14-incident-report-structure)
- [Slide 15: Full Methodology Recap](#slide-15-full-methodology-recap)

---

## Slide 01: Introduction

> **Category:** `INCIDENT DETECTION & RESPONSE`

### Phishing Analysis Part II

Continuing the methodology — dissecting URLs and attachments, applying automated tools, and closing the loop with defense and reporting.

Lab 03 — Tools, Defense & Reporting

> [!NOTE] 🎙️ **Instructor Lecture Notes**
> Welcome students back for Part 2 of the phishing analysis lab. Lab 2 covered email fundamentals, attack techniques, and the header/content analysis steps of the methodology. This session picks up with URL and attachment analysis, the tools that automate them, defense measures, and reporting.

---

## Slide 02: Recap & Objectives

> **Category:** `LAB OVERVIEW`

### Recap & Today's Objectives

Lab 2 walked through the first half of the phishing analysis methodology. Today completes the process — from clicking nothing, to full response and reporting.

Already Covered — Lab 2 Initial Triage Header & Sender Examination Content Examination Authentication Analysis (SPF/DKIM/DMARC) Today — Lab 3 URL Examination & tooling Attachment Examination — static & dynamic Automated analysis tools Defense Measures — reactive & proactive Documentation & Reporting

> [!NOTE] 🎙️ **Instructor Lecture Notes**
> Quickly recap the four methodology steps already covered in Lab 2 (Initial Triage, Header and Sender Examination, Content Examination, and Authentication Analysis), then introduce the four remaining steps this session will cover: URL Examination, Attachment Examination, Defense Measures, and Documentation and Reporting.

---

## Slide 03: Anatomy of a URL

> **Category:** `FOUNDATIONS`

Before analyzing a suspicious link, an analyst needs to reliably name every part of it — attackers hide their tricks in specific pieces of this structure.

Hostname Path https:// academy. tcm-sec. com /courses/ example.php ?t=129 Protocol Subdomain Domain TLD Subdirectory File Parameter

Now compare that to a real phishing URL — the same structure, but every piece is weaponized:

Hostname — Spoofed Path http:// apple-login. dnsdyn. net /ODFTY/ index.php ?email=asimpson@example.com Protocol Subdomain Real domain TLD Subdirectory File Victim's email

> [!WARNING]
> Read every piece: "apple-login" is just a subdomain label, not proof of Apple — the real domain is dnsdyn.net , a dynamic-DNS provider no legitimate company uses for login pages. "ODFTY" is a random, auto-generated subdirectory. And the highlighted parameter pre-fills the victim's own email into the fake login form, both to look more convincing and to let the attacker track exactly who clicked.

> [!NOTE] 🎙️ **Instructor Lecture Notes**
> Before diving into analysis, make sure students can name every part of a URL: protocol, subdomain, domain, TLD, subdirectory, file, and parameters. Then show a real phishing URL and point out how each part has been abused — a look-alike subdomain, a dynamic-DNS domain, a meaningless random subdirectory, and a parameter carrying the victim's own email address.

---

## Slide 04: URL Analysis Workflow

> **Category:** `METHOD DEEP DIVE`

### URL Analysis — Analyst Workflow

With the anatomy in hand, a suspicious URL is worked through in three stages — extract, inspect, then scan.

1 Extract the URL Pull every link out of the header and body 2 Check for Red Flags Look for spoofing attempts — look-alike domains and subdomain abuse Watch for URL shorteners hiding the real destination Watch for encoding tricks masking the true link 3 Scan With Tools Submit the URL in its original form — scanning tools need the real link, not a defanged one Cross-reference results to reach a verdict

> [!WARNING]
> Never visit a suspicious URL directly. Always use an isolated analysis VM, a dedicated sandbox tool, or a URL-scanning service.

> [!NOTE] 🎙️ **Instructor Lecture Notes**
> Deep-dive into methodology step 4. Walk through the three-stage workflow: first extract every URL from the header and body, then check each one for spoofing attempts, shorteners, or encoding, and finally scan it with dedicated tools before rendering a verdict.

---

## Slide 05: URL Analysis Tools

> **Category:** `TOOLING`

These services let an analyst safely inspect a URL without ever loading it in a real browser.

- **URL2PNG** `[SCREENSHOT]`: Renders a safe screenshot of the destination page without ever loading it in the analyst's own browser — a quick, low-risk first look at what a link leads to.
- **urlscan.io** `[FULL SCAN]`: Loads the page in an isolated sandbox and captures a screenshot, the full DOM, every network request, and the redirect chain.
- **VirusTotal** `[REPUTATION]`: Submits the URL to dozens of antivirus and blocklist engines at once and returns a consolidated malicious / suspicious / clean verdict.
- **PhishTank** `[PHISHING DB]`: A community-driven database of confirmed phishing addresses — search it to check if a URL is already reported, and to see newly submitted phishing sites as they're verified.

> [!IMPORTANT]
> Analyst's tip: A "clean" result from one tool is not proof of safety — brand-new malicious domains are often not yet indexed anywhere. Cross-reference at least two independent sources before clearing a URL.

> [!NOTE] 🎙️ **Instructor Lecture Notes**
> Introduce the four core tools used to scan a suspicious URL: URL2PNG for a safe visual screenshot without loading the page locally, urlscan.io for a full technical scan, VirusTotal for multi-engine reputation, and PhishTank for checking against and searching a community-reported phishing database.

---

## Slide 06: Static vs Dynamic Analysis

> **Category:** `METHOD DEEP DIVE`

### Attachment Analysis — Static vs Dynamic

Once an attachment is securely extracted, hash it and search that hash's reputation first — a known-bad hit alone can be enough for a verdict. From there, an analyst has two complementary approaches to dig deeper.

Static Analysis Examines the file without running it Safe, fast, and repeatable at scale PDF: pdfid / pdf-parser to pull out embedded URLs and objects Office doc: oledump to find and extract macros Dynamic Analysis Executes the file in an isolated sandbox Reveals real runtime behavior and intent Process, file system, registry, network activity Slower, and some malware detects and evades sandboxes

> [!IMPORTANT]
> Scope note: Full malware analysis process is outside this course. The goal here is triage — pull out embedded URLs, objects, and macros to confirm intent, or hand the file to a sandbox and read its report.

> [!NOTE] 🎙️ **Instructor Lecture Notes**
> Deep-dive into methodology step 5, attachment examination. Extract the attachment, hash it, and search that hash's reputation first. From there: static analysis (format-specific tools, no execution) versus dynamic analysis (detonating in a sandbox to observe behavior). Note that full malware reverse engineering is out of scope for this course — the goal is triage.

---

## Slide 07: Static Analysis Techniques

> **Category:** `STATIC ANALYSIS`

Start every file the same way — hash it and search that hash's reputation. If it comes back unknown, the next tools depend on the file type.

> [!IMPORTANT]
> Hash & Search: Compute the file's MD5 / SHA-1 / SHA-256 and search it on VirusTotal and other reputation sources — the fastest check, and often enough to reach a verdict on its own.

PDF Files 1 pdfid Quick triage count of risky keywords — JavaScript, embedded files, launch actions 2 pdf-parser Digs into the flagged objects to pull out embedded URLs and payloads Office Documents 1 oledump Inspects the OLE structure of Word/Excel files to detect embedded VBA macros 2 Extract & Review Pull out the macro code and read it without ever letting it run

> [!WARNING]
> Scope note: The goal is triage, not full reverse engineering — extract the indicator (a URL, an object, a macro), then decide whether it's worth escalating to a sandbox.

> [!NOTE] 🎙️ **Instructor Lecture Notes**
> Cover the practical static triage workflow: hash the file and search reputation databases first for every file type. Then split by format — pdfid and pdf-parser for malicious PDFs (triage keywords, then extract embedded URLs/objects), and oledump plus manual extraction for Office documents (detect and pull VBA macros). Emphasize this is triage, not full reverse engineering, which is out of scope for this course.

---

## Slide 08: Dynamic Analysis & Sandboxing

> **Category:** `DYNAMIC ANALYSIS`

The file is detonated inside an isolated, monitored environment — an analyst watches what it actually does, rather than guessing from its code alone.

- **Process Behavior**: Which child processes spawn, what commands run, and whether the sample tries to inject into or hollow out other processes.
- **File System & Registry Changes**: New or modified files, dropped payloads, and registry keys added for persistence across reboots.
- **Network Traffic**: Command-and-control callbacks, DNS requests, and any second-stage payload downloads captured with full packet detail.
- **Sandbox-Evasion Checks**: Some malware detects it's being watched — checking for a mouse, a real user, or specific VM artifacts — and stays dormant to avoid analysis.

- **Any.Run** `[SANDBOX]`: Interactive, browser-based sandbox with live process, network, and screen visibility during detonation.
- **Joe Sandbox** `[SANDBOX]`: Deep behavioral reports covering process trees, network activity, and MITRE ATT&CK technique mapping.
- **Hybrid Analysis / Cuckoo** `[SANDBOX]`: Free and open-source options for automated detonation with detailed behavioral reports.

> [!NOTE] 🎙️ **Instructor Lecture Notes**
> Explain dynamic analysis: detonating the file in an isolated sandbox and observing what it actually does — process creation, file system and registry changes, and network traffic. Mention that this is essential when static analysis is inconclusive, e.g. against packed or obfuscated malware.

---

## Slide 09: Automated Analysis Tools

> **Category:** `TOOLING`

Manual analysis doesn't scale to hundreds of reported emails a day — these two tools automate the repetitive parts of the process.

- **eioc.py** `[SCRIPT]`: Parses a raw email file and extracts every IOC in one pass — sender and reply-to addresses, URLs, IPs, and attachment hashes — turning what would be several manual steps into a single command.
- **PhishTool** `[WEBSITE]`: A web-based triage platform — upload the email and it pulls header, URL, and attachment analysis into one case, with a verdict and case management built in.

> [!IMPORTANT]
> Analyst's tip: Automation accelerates triage but doesn't replace judgment — a tool's verdict is one input into the analyst's own conclusion, not a substitute for it.

> [!NOTE] 🎙️ **Instructor Lecture Notes**
> Introduce the two main automated tools used in this course: eioc.py, a script that extracts every IOC from an email in one pass, and PhishTool, a web-based platform that runs a full triage workflow on an uploaded email.

---

## Slide 10: Defense Measures Overview

> **Category:** `METHOD DEEP DIVE`

### Defense Measures — Reactive vs Proactive

Once a phishing email is confirmed malicious, the response splits into two tracks: contain what already happened, and reduce the chance it happens again.

Reactive Defense Taken after a confirmed threat is found Focused on containment and eradication Time-sensitive — every minute counts e.g. blocking, quarantining, resetting credentials Proactive Defense Put in place before an attack occurs Focused on reducing likelihood and blast radius Ongoing, not tied to a single incident e.g. DMARC enforcement, training, threat intel

> [!IMPORTANT]
> Analyst's tip: A mature security program treats every reactive response as an input to the proactive program — each incident should improve the defenses that prevent the next one.

> [!NOTE] 🎙️ **Instructor Lecture Notes**
> Deep-dive into methodology step 6, defense measures. Introduce the two categories: reactive defense, taken after a phishing email has already been identified in the environment, and proactive defense, put in place ahead of time to reduce the likelihood and impact of future attacks.

---

## Slide 11: Reactive Defense Actions

> **Category:** `REACTIVE DEFENSE`

### Reactive Phishing Defense

Once a phishing email is confirmed, response moves through five phases — from stopping the spread to closing the loop with training.

1 Containment Determine scope Quarantine Block sender artifacts Block web artifacts Block file artifacts 2 Eradication Remove malicious emails Content search and eDiscovery Remove malicious files Abuse form submissions Credential changes Reimaging 3 Recovery Restore systems 4 Communication Notify affected users Update stakeholders 5 User Education End-user training

> [!NOTE] 🎙️ **Instructor Lecture Notes**
> Cover the five phases of reactive phishing defense: containment (determine scope, quarantine, block sender/web/file artifacts), eradication (remove malicious emails and files, including content search and eDiscovery, plus abuse form submissions, credential changes, and reimaging), recovery (restore systems), communication (notify affected users, update stakeholders), and user education (end-user training).

---

## Slide 12: Proactive Defense Measures

> **Category:** `PROACTIVE DEFENSE`

### Proactive Phishing Defense

Standing controls maintained continuously across five layers to reduce both the likelihood and the impact of the next phishing attempt.

1 Email Filtering Email security appliances Marking external emails 2 URL Scanning & Blocking Real-time URL inspection Block recently registered domains 3 Attachment Filtering File extension blocks Attachment sandboxing 4 Email Authentication Methods SPF DKIM DMARC 5 User Training Security awareness training Phishing simulation exercises Reporting functionality

> [!IMPORTANT]
> Analyst's tip: No single layer is enough on its own — these five work together, so a phish that slips past filtering can still be stopped by authentication checks, sandboxing, or a trained user reporting it.

> [!NOTE] 🎙️ **Instructor Lecture Notes**
> Cover the five pillars of proactive phishing defense: email filtering (security appliances and marking external mail), URL scanning and blocking (real-time inspection and blocking recently registered domains), attachment filtering (extension blocks and sandboxing), email authentication (SPF, DKIM, DMARC), and user training (awareness training, phishing simulations, and reporting functionality).

---

## Slide 13: Documentation & Reporting

> **Category:** `METHOD DEEP DIVE`

An incident isn't closed until it's written down — the report turns a one-off response into knowledge the whole team can use.

- **Institutional Memory**: The next analyst may not have handled this incident. A good report lets them spot the same attack instantly.
- **Compliance & Accountability**: Audits, insurance, and regulators often require proof of what was detected, and how it was handled.
- **Metrics & Trends**: Reports add up over time — showing which departments are targeted most, and whether training is working.
- **Handoff & Escalation**: A clear report lets you pass the incident to another team, or up to management, without re-explaining it.
- **Justify the Response**: Don't just list what was done — explain why. State the reasoning behind each action, so anyone reviewing it later understands the decision, not just the outcome.

> [!IMPORTANT]
> Analyst's tip: Write for a reader who knows nothing about this incident — spell out acronyms, give a clear timeline, and don't rely on memory only you have.

> [!NOTE] 🎙️ **Instructor Lecture Notes**
> Deep-dive into the final methodology step. Explain why documentation matters even after the threat is contained: institutional memory, compliance, metrics, handoff, and — importantly — justifying why each action was taken, not just listing what was done.

---

## Slide 14: Incident Report Structure

> **Category:** `REPORT TEMPLATE`

A consistent structure makes every report easy to skim under pressure and easy to compare against past incidents.

1 Description Plain-language summary of what the email does and why it's suspicious 2 Headers Date, Subject, To, From, Reply-To, Return-Path, Sender IP, Resolved Host, Message-ID 3 URLs Every link extracted from the header and body 4 Attachments Attachment name, MD5, SHA1, and SHA256 for each file 5 Artifact Analysis Sender Analysis, URL Analysis, and Attachment Analysis — findings from each 6 Verdict Final classification — malicious, suspicious, or benign 7 Defense Actions Every reactive step taken in response

> [!WARNING]
> Best practice: Defang every URL and IP written into the report — hxxp[://]evil[.]com , 1.2.3[.]4 — so nothing in the document is clickable or gets auto-parsed as a live indicator by whoever reads it next.

> [!NOTE] 🎙️ **Instructor Lecture Notes**
> Walk through the actual report template students will fill in: Headers, URLs, Attachments, Description, Artifact Analysis (sender/URL/attachment), Verdict, and Defense Actions. Emphasize the best practice of defanging every URL and IP in the written report, even though they weren't defanged during scanning.

---

## Slide 15: Full Methodology Recap

> **Category:** `WRAP-UP`

### The Full Methodology, End to End

Seven steps, one repeatable process — from the first suspicious email in the inbox to a closed, documented case.

- **Initial Triage** `[STEP 1]`: STEP 1
- **Header & Sender Examination** `[STEP 2]`: STEP 2
- **Content Examination** `[STEP 3]`: STEP 3
- **URL Examination** `[STEP 4]`: STEP 4
- **Attachment Examination** `[STEP 5]`: STEP 5
- **Defense Measures** `[STEP 6]`: STEP 6
- **Documentation & Reporting** `[STEP 7]`: STEP 7

> [!IMPORTANT]
> You now have the complete methodology. The hands-on exercise will apply all seven steps to a real suspicious email — from first glance to a fully documented, defensible report.

> [!NOTE] 🎙️ **Instructor Lecture Notes**
> Close the lab by walking through the complete seven-step methodology end to end, spanning both Lab 2 and Lab 3, to reinforce how every piece fits together into one repeatable process.

---

## 🎯 Summary & Key Takeaways

- **Module:** Lab 03: Phishing Analysis Part II — Advanced Header & URL Investigation

- **Core Competencies Developed:** Hands-on triage, log analysis, threat hunting, and defensive incident response.

- **Course Reference:** Cybersecurity Operations Practical Labs by **Hussein Al-Selwi**.
