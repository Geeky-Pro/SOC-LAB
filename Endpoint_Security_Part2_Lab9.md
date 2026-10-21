# Lab 09: Endpoint Security Part II — Windows Registry & Persistence Mechanisms

> **Course:** Cybersecurity Operations (SOC Lab)  
> **Instructor:** Hussein Al-Selwi  
> **Total Slides:** 17 Slides  
> **Source Presentation:** `Endpoint_Security_Part2_Lab9.html`  

### 📋 Overview
Forensic analysis of adversary persistence: the five Windows Registry hives, Run and RunOnce auto-start keys, malicious Windows Service creation via sc.exe, Scheduled Tasks via schtasks, and Sysinternals Autoruns inspection.

---

## 📑 Table of Contents

- [Slide 01: Introduction](#slide-01-introduction)
- [Slide 02: Persistence Mechanisms](#slide-02-persistence-mechanisms)
- [Slide 03: The Registry — History & Why](#slide-03-the-registry-history-why)
- [Slide 04: Viewing the Registry — Registry Editor](#slide-04-viewing-the-registry-registry-editor)
- [Slide 05: The Five Hives](#slide-05-the-five-hives)
- [Slide 06: Registry Persistence — Run & RunOnce](#slide-06-registry-persistence-run-runonce)
- [Slide 07: Viewing Run/RunOnce — Editor & Command Line](#slide-07-viewing-run-runonce-editor-command-line)
- [Slide 08: Autoruns — Sysinternals](#slide-08-autoruns-sysinternals)
- [Slide 09: Services — What & Why Targeted](#slide-09-services-what-why-targeted)
- [Slide 10: Viewing Services — Services App](#slide-10-viewing-services-services-app)
- [Slide 11: Managing Services — sc](#slide-11-managing-services-sc)
- [Slide 12: Displaying Services — query & qc](#slide-12-displaying-services-query-qc)
- [Slide 13: Scheduled Tasks — What & Why](#slide-13-scheduled-tasks-what-why)
- [Slide 14: Viewing Tasks — Task Scheduler](#slide-14-viewing-tasks-task-scheduler)
- [Slide 15: Managing Tasks — schtasks](#slide-15-managing-tasks-schtasks)
- [Slide 16: Displaying Tasks — /query](#slide-16-displaying-tasks-query)
- [Slide 17: Summary — Viewing All Three](#slide-17-summary-viewing-all-three)

---

## Slide 01: Introduction

> **Category:** `INCIDENT DETECTION & RESPONSE`

### Endpoint Security Part II

Persistence mechanisms attackers use to survive reboot and stay hidden — registry, services, and scheduled tasks — and deploying LimaCharlie EDR to catch them.

Lab 09 – Persistence Mechanisms & EDR Deployment

> [!NOTE] 🎙️ **Instructor Lecture Notes**
> Welcome students back for Part II of Endpoint Security. This lab builds directly on Part I — now that we know how to read process trees and normal system behavior, we shift to how attackers stay on a compromised endpoint long after the initial breach: persistence mechanisms via the registry, services, and scheduled tasks. We'll close by deploying LimaCharlie as our EDR to detect this activity live.

---

## Slide 02: Persistence Mechanisms

> **Category:** `PERSISTENCE MECHANISMS`

### How Attackers Stay On an Endpoint

Once an attacker lands on a machine, the next problem they need to solve is surviving a reboot or logoff . Windows gives them several built-in mechanisms to do this — we'll cover three, in this order:

- **1. Registry Keys**: Run / RunOnce keys that launch a program automatically at logon, in HKCU or HKLM.
- **2. Services**: Windows Services that start automatically at boot, often running as SYSTEM.
- **3. Scheduled Tasks**: Tasks configured to run on a schedule or trigger, independent of any logged-in user.

> [!IMPORTANT]
> Why this matters for detection: all three are legitimate Windows features that IT and software rely on every day — which is exactly why attackers abuse them. Persistence detection is about knowing what's normal here so the abnormal stands out.

> [!NOTE] 🎙️ **Instructor Lecture Notes**
> Introduce the three persistence mechanisms we'll cover, in this order: Registry keys first, then Services, then Scheduled Tasks. All three share the same goal — surviving a reboot or logoff so the attacker's foothold doesn't disappear when the machine restarts.

---

## Slide 03: The Registry — History & Why

> **Category:** `REGISTRY KEYS`

In the past, Windows stored configuration in plain text initialization files — files with a .ini extension, one per app. Microsoft replaced this with a single hierarchical database : the Registry , which stores all configuration for the system and every installed app in one place.

1. **Step 1**: .ini files
2. **Step 2**: The Registry

> [!NOTE] 🎙️ **Instructor Lecture Notes**
> Explain where the Registry came from, briefly. Before it existed, Windows apps stored configuration in scattered .ini text files. Microsoft replaced that with one hierarchical database: the Registry.

---

## Slide 04: Viewing the Registry — Registry Editor

> **Category:** `REGISTRY KEYS`

The Registry is viewed and edited with a built-in Windows tool: Registry Editor ( regedit.exe ). Launch it from the Run dialog or Start menu search.

```bash
Run>
regedit
Opens Registry Editor
```

When Registry Editor opens, the left-hand pane shows five root folders . These are called hives — each one is a separate top-level branch of the Registry, holding a different category of configuration data.

HKLM HKEY_LOCAL_MACHINE HKCU HKEY_CURRENT_USER HKCR HKEY_CLASSES_ROOT HKU HKEY_USERS HKCC HKEY_CURRENT_CONFIG

> [!NOTE] 🎙️ **Instructor Lecture Notes**
> Show how to actually see the Registry: Registry Editor, regedit.exe. When it opens, the left pane shows five root folders — these are the hives. We'll define each on the next slide, but first establish that this is the tool and this is the top-level layout students will be looking at.

---

## Slide 05: The Five Hives

> **Category:** `REGISTRY KEYS`

Each hive holds a different slice of the system's configuration:

| Hive | Full Name | Main Purpose |
| --- | --- | --- |
| HKLM | HKEY_LOCAL_MACHINE | System-wide settings, hardware, services, installed software |
| HKCU | HKEY_CURRENT_USER | Settings specific to the currently logged-in user |
| HKCR | HKEY_CLASSES_ROOT | File associations and registered Windows classes — which program opens a particular file type |
| HKU | HKEY_USERS | Registry settings for all loaded user profiles |
| HKCC | HKEY_CURRENT_CONFIG | Current hardware configuration |

> [!NOTE] 🎙️ **Instructor Lecture Notes**
> Walk through each of the five hives and its purpose: HKLM for system-wide settings, hardware, services, and installed software; HKCU for the currently logged-in user's settings; HKCR for file associations and registered classes; HKU for all loaded user profiles; HKCC for the current hardware configuration.

---

## Slide 06: Registry Persistence — Run & RunOnce

> **Category:** `REGISTRY KEYS`

The two Registry keys most commonly abused for persistence are Run and RunOnce . Anything listed under either key launches automatically at logon — which is exactly the behavior an attacker wants for a persistent foothold.

- **Run**: Runs every single time the user logs on. The value stays in place — it's not removed after execution.
- **RunOnce**: Runs a single time at the next logon, then Windows automatically deletes the value.

Both keys exist under HKCU and HKLM , and the distinction matters:

HKCU — runs only for that one logged-in user HKLM — runs for any user machine-wide, needs admin rights to write

> [!NOTE] 🎙️ **Instructor Lecture Notes**
> Now connect the hives to persistence. The keys attackers abuse most are Run and RunOnce, and they exist under both HKCU (runs for that one user at logon) and HKLM (runs for any user, machine-wide, and usually needs admin rights to write to). Run fires every logon; RunOnce fires once and then Windows deletes the value automatically.

---

## Slide 07: Viewing Run/RunOnce — Editor & Command Line

> **Category:** `REGISTRY KEYS`

### Viewing Run & RunOnce Keys

These keys can be checked two ways: browsing to them directly in Registry Editor , or querying them from the command line with reg query .

| Item / Key | Value / Description |
| --- | --- |
| HKCU \ Run | HKCU\SOFTWARE\Microsoft\Windows\CurrentVersion\Run |
| HKCU \ RunOnce | HKCU\SOFTWARE\Microsoft\Windows\CurrentVersion\RunOnce |
| HKLM \ Run | HKLM\SOFTWARE\Microsoft\Windows\CurrentVersion\Run |
| HKLM \ RunOnce | HKLM\SOFTWARE\Microsoft\Windows\CurrentVersion\RunOnce |

```cmd
C:\>
reg query "HKCU\SOFTWARE\Microsoft\Windows\CurrentVersion\Run"
Lists Run entries for the current user
C:\>
reg query "HKLM\SOFTWARE\Microsoft\Windows\CurrentVersion\Run"
Lists Run entries machine-wide (all users)
```

> [!WARNING]
> What to look for: any value pointing to an unfamiliar executable, a script interpreter ( powershell.exe , wscript.exe ), an unusual path like %TEMP% , or an entry the user or IT can't explain.

> [!NOTE] 🎙️ **Instructor Lecture Notes**
> Show both ways to check these keys: navigating to them in Registry Editor by full path, and querying them from the command line with reg query. Walk through the four full paths — Run and RunOnce under both HKCU and HKLM — and the equivalent reg query syntax for each.

---

## Slide 08: Autoruns — Sysinternals

> **Category:** `REGISTRY KEYS`

Autoruns , a free Sysinternals tool, shows every autostart location on a system in one window — registry run keys, services, scheduled tasks, and more — instead of checking each one separately.

It's most powerful when paired with baselining : capturing a snapshot of what's normal, so anything new later stands out on its own.

1. **Baseline**: Snapshot a clean system
2. **Rescan**: Snapshot again later
3. **Diff**: New entries stand out

> [!NOTE] 🎙️ **Instructor Lecture Notes**
> Introduce Autoruns by Sysinternals — a tool that shows every autostart location on a system in one view. Then introduce baselining: capturing what's normal for a clean system so a later scan's differences immediately stand out.

---

## Slide 09: Services — What & Why Targeted

> **Category:** `SERVICES`

A Service is a background process managed by Windows that can start automatically at boot — before any user even logs in — and often runs under a high-privilege account like SYSTEM .

- **Runs With High Privilege**: Often as SYSTEM — more powerful than the compromised user's own account.
- **No Login Needed**: Starts at boot, so it persists even if no one ever signs in.

With dozens of legitimate services already running on any machine, one more — with a convincing name — is easy to hide in plain sight.

> [!NOTE] 🎙️ **Instructor Lecture Notes**
> Define Windows Services: background processes managed by the Service Control Manager, most starting automatically at boot before any user logs in, often running as SYSTEM. Explain why attackers target them: high privilege, no need for a logged-in user, and they blend in among the many legitimate services already on a system.

---

## Slide 10: Viewing Services — Services App

> **Category:** `SERVICES`

The built-in GUI for services is the Services app — opened by running services.msc . It lists every service with its status, startup type, and the account it runs as.

```bash
Run>
services.msc
Opens the Services app
```

> [!NOTE] 🎙️ **Instructor Lecture Notes**
> Show the Services app, services.msc — the GUI for viewing and managing services, listing name, description, status, startup type, and the account each one logs on as.

---

## Slide 11: Managing Services — sc

> **Category:** `SERVICES`

From the command line, services are managed with sc — the Service Controller.

```bash
C:\>
sc create SvcName binPath= "C:\path\to\file.exe" start= auto
Creates a new service, set to start automatically
C:\>
sc start SvcName
Starts the service
C:\>
sc stop SvcName
Stops the service
C:\>
sc config SvcName start= disabled
Changes its startup type
C:\>
sc delete SvcName
Removes the service
```

> [!NOTE] 🎙️ **Instructor Lecture Notes**
> Introduce sc.exe, the Service Controller command-line tool, and its core options for creating, starting, stopping, configuring, and deleting a service.

---

## Slide 12: Displaying Services — query & qc

> **Category:** `SERVICES`

### Displaying Services

Two sc options show what's already there — no changes made:

```cmd
C:\>
sc query SvcName
Current state — running, stopped, etc.
C:\>
sc qc SvcName
Full config — binary path, start type, log-on account
```

To list every service at once with the fields that matter most for a quick review:

```bash
C:\>
wmic service get Name,DisplayName,State,StartMode,PathName
Every service — name, state, startup type, and executable path
```

> [!IMPORTANT]
> Reminder: Autoruns has a dedicated Services tab too — the same information, alongside every other autostart location, in one place.

> [!NOTE] 🎙️ **Instructor Lecture Notes**
> Show the read-only ways to inspect services: sc query for current state, sc qc for configuration detail including binary path, and the wmic one-liner that lists every service with name, display name, state, start mode, and path in one table — useful for spotting one pointing to an odd location.

---

## Slide 13: Scheduled Tasks — What & Why

> **Category:** `SCHEDULED TASKS`

A Scheduled Task runs a program or script automatically on a trigger — a set time, at logon, at boot, or on some other event. Windows and installed software use them normally for things like updates, cleanup, and backups.

Attackers use the same trigger to get their own persistence: a task set to run onlogon or on a schedule survives reboot just like a service, and with dozens of legitimate scheduled tasks already on a system, one more is easy to miss.

> [!NOTE] 🎙️ **Instructor Lecture Notes**
> Define scheduled tasks: a Windows feature that runs a program or script on a trigger — a set time, at logon, at boot, or on an event — normally used for maintenance like updates and backups. Explain why attackers use them: same reboot-surviving persistence as a service, can be set to run at logon or with high privilege, and blends in with the many legitimate scheduled tasks Windows already creates.

---

## Slide 14: Viewing Tasks — Task Scheduler

> **Category:** `SCHEDULED TASKS`

The built-in GUI is Task Scheduler — opened by running taskschd.msc . It shows every task's trigger, the action it runs, and its history.

```bash
Run>
taskschd.msc
Opens Task Scheduler
```

> [!NOTE] 🎙️ **Instructor Lecture Notes**
> Show the Task Scheduler app, taskschd.msc — the GUI for viewing and managing scheduled tasks, organized in a library tree with triggers, actions, and history for each task.

---

## Slide 15: Managing Tasks — schtasks

> **Category:** `SCHEDULED TASKS`

From the command line, tasks are managed with schtasks .

```cmd
C:\>
schtasks /create /tn "MyTask" /tr "C:\path\to\file.exe" /sc onlogon
Creates a task that runs at logon
C:\>
schtasks /delete /tn "MyTask" /f
Deletes the task without confirmation prompt
```

> [!NOTE] 🎙️ **Instructor Lecture Notes**
> Introduce schtasks.exe, the command-line tool for scheduled tasks, and its core create and delete options.

---

## Slide 16: Displaying Tasks — /query

> **Category:** `SCHEDULED TASKS`

Listing and inspecting tasks is read-only — no changes made:

```cmd
C:\>
schtasks /query
Lists every scheduled task on the system
C:\>
schtasks /query /tn "MyTask" /fo LIST /v
Full detail on one task — trigger, action, run-as account, last result
```

> [!WARNING]
> What to look for: a task name mimicking a legitimate one, an action pointing to an unfamiliar path, or a trigger like onlogon on a task with no clear business reason to run then.

> [!NOTE] 🎙️ **Instructor Lecture Notes**
> Show how to list all tasks with schtasks /query, and how to get full detail on one specific task with schtasks /query /tn and /fo LIST /v.

---

## Slide 17: Summary — Viewing All Three

> **Category:** `SUMMARY`

### Viewing All Three — Quick Reference

Autoruns can display all three of these in one place. Individually, here's the GUI and command-line options for each:

Registry regedit reg query "HKCU\...\Run" reg query "HKLM\...\Run" Services services.msc sc query SvcName sc qc SvcName wmic service get Name,DisplayName,State,StartMode,PathName Scheduled Tasks taskschd.msc schtasks /query schtasks /query /tn "MyTask" /fo LIST /v

> [!NOTE] 🎙️ **Instructor Lecture Notes**
> Recap slide: the GUI tool and the command-line options for viewing each of the three persistence locations covered — Registry, Services, and Scheduled Tasks — side by side for quick reference.

---

## 🎯 Summary & Key Takeaways

- **Module:** Lab 09: Endpoint Security Part II — Windows Registry & Persistence Mechanisms

- **Core Competencies Developed:** Hands-on triage, log analysis, threat hunting, and defensive incident response.

- **Course Reference:** Cybersecurity Operations Practical Labs by **Hussein Al-Selwi**.
