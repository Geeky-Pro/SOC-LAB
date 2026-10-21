# Lab 02: SOC Lab Environment Setup & Toolchain Deployment

> **Course:** Cybersecurity Operations (SOC Lab)  
> **Instructor:** Hussein Al-Selwi  
> **Total Slides:** 18 Slides  
> **Source Presentation:** `Lab2_SOC_Environment_Setup.html`  

### 📋 Overview
Complete hands-on engineering guide to configuring student laptops as defensive analyst workstations: deploying Wireshark with Npcap, configuring Sysinternals Suite (Process Explorer with VirusTotal & Autoruns), installing Splunk Enterprise Free on port 8000, ingesting local Windows Event Logs, and setting up CyberChef.

---

## 📑 Table of Contents

- [Slide 01: SOC Lab Environment Setup](#slide-01-soc-lab-environment-setup)
- [Slide 02: Lab 2 Objectives](#slide-02-lab-2-objectives)
- [Slide 03: Student Laptop Prerequisites & Architecture](#slide-03-student-laptop-prerequisites-architecture)
- [Slide 04: The Student SOC Workstation Architecture](#slide-04-the-student-soc-workstation-architecture)
- [Slide 05: Installing Wireshark & Npcap Packet Driver](#slide-05-installing-wireshark-npcap-packet-driver)
- [Slide 06: Verifying Wireshark & First Packet Capture](#slide-06-verifying-wireshark-first-packet-capture)
- [Slide 07: Deploying the Sysinternals Suite](#slide-07-deploying-the-sysinternals-suite)
- [Slide 08: Configuring Process Explorer & Process Hacker](#slide-08-configuring-process-explorer-process-hacker)
- [Slide 09: Configuring Sysinternals Autoruns](#slide-09-configuring-sysinternals-autoruns)
- [Slide 10: Choosing the Student SIEM: Why Splunk Enterprise Free?](#slide-10-choosing-the-student-siem-why-splunk-enterprise-free)
- [Slide 11: Step-by-Step Splunk Installation on Laptop](#slide-11-step-by-step-splunk-installation-on-laptop)
- [Slide 12: Accessing Splunk Web Console & Navigation](#slide-12-accessing-splunk-web-console-navigation)
- [Slide 13: Ingesting Local Windows Security Event Logs](#slide-13-ingesting-local-windows-security-event-logs)
- [Slide 14: Executing Your First SPL Queries in Splunk](#slide-14-executing-your-first-spl-queries-in-splunk)
- [Slide 15: Setting up Phishing & Triage Tools (CyberChef)](#slide-15-setting-up-phishing-triage-tools-cyberchef)
- [Slide 16: Alternative Free Cloud Sandbox Options](#slide-16-alternative-free-cloud-sandbox-options)
- [Slide 17: The 6-Point Readiness Verification Checklist](#slide-17-the-6-point-readiness-verification-checklist)
- [Slide 18: Summary & Preparation for Week 3](#slide-18-summary-preparation-for-week-3)

---

## Slide 01: SOC Lab Environment Setup

> **Category:** `PRACTICAL WORKSTATION CONFIGURATION`

### SOC Lab Environment Setup & Toolchain Deployment

A step-by-step practical guide to configuring Wireshark, Sysinternals Suite, CyberChef, and Splunk Enterprise Free on student laptops.

Lab 2 — Hands-On Environment & Tooling Setup Instructor: Hussein Al-Selwi

> [!NOTE] 🎙️ **Instructor Lecture Notes**
> Welcome students to Lab 2. Explain that today is our hands-on engineering lab: converting their personal laptops into fully equipped defensive security analyst workstations. Every tool we deploy today will be used throughout the remaining 10 weeks of the course.

---

## Slide 02: Lab 2 Objectives

> **Category:** `SESSION GOALS`

### Lab 2 Deliverables & Milestones

By the end of today's hands-on session, every student workstation will be fully configured with the four core defensive layers:

- **1. Network Visibility Layer**: Deploy Wireshark + Npcap driver, verify interface bindings, and test packet capture filtering.
- **2. Host & Process Inspection Layer**: Deploy Sysinternals Suite (Process Explorer, Process Hacker, Autoruns), enable VirusTotal integration.
- **3. Central SIEM & Search Layer**: Install Splunk Enterprise Free locally on port 8000, connect Windows Security Event logs, and run initial SPL queries.
- **4. Phishing & Triage Utilities**: Set up CyberChef offline, email header dissection tools, and safe URL defanging bookmarks.

> [!NOTE] 🎙️ **Instructor Lecture Notes**
> Review the session goals. By the end of this 2-hour lab, every student will have Wireshark capturing packets, Sysinternals analyzing processes, and Splunk ingesting local Windows Event logs on localhost:8000.

---

## Slide 03: Student Laptop Prerequisites & Architecture

> **Category:** `HARDWARE & OS REQUIREMENTS`

### Workstation Requirements & Architecture

Our lab setup is engineered to be lightweight, high-performance, and compatible with typical student hardware:

- **Hardware Specifications**: RAM: 8 GB minimum (16 GB recommended). Storage: 10 GB free disk space (SSD preferred). CPU: 64-bit x86 Dual-core or higher.
- **Operating System Support**: Primary: Windows 10 / 11 64-bit. macOS: Intel & Apple Silicon (M1/M2/M3) supported via native builds or UTM. Linux: Ubuntu / Kali / Fedora native.
- **Privilege Requirements**: Local Administrator: Students must have Administrator / root privileges on their laptops to install drivers and read security logs.

> [!NOTE]
> 💡 Why Native Host-Based Tooling? Running 3 heavy VMs (Windows Server + Kali + Splunk) crushes 8GB RAM laptops. Instead, running tools natively on the host provides instant response times, zero virtualization overhead, and direct access to real system telemetry!

> [!NOTE] 🎙️ **Instructor Lecture Notes**
> Address hardware considerations. Students bring varied laptops. Reassure them that our setup is designed to run natively and smoothly on machines with 8GB RAM without burning their CPU with multiple heavy virtual machines.

---

## Slide 04: The Student SOC Workstation Architecture

> **Category:** `SYSTEM ARCHITECTURE`

### The Complete Student SOC Workstation Blueprint

How the components interconnect on your local machine to simulate a miniature corporate SOC:

- **1. Network Layer**: Wireshark + Npcap binds to the Wi-Fi or Ethernet adapter, capturing live packets and inspecting protocol handshakes.
- **2. Endpoint Layer**: Process Hacker & Autoruns monitor OS process trees, memory spaces, and persistence registry keys.
- **3. SIEM Layer**: Splunk Enterprise Free runs as a background service, collecting event logs and serving the analytical web GUI on localhost:8000 .

```bash
http://127.0.0.1:8000 --> Splunk Web Console (GUI)
splunkd.exe:8089 --> Splunk Management API
Npcap Packet Driver --> Kernel-level NDIS Packet Filter
Sysinternals Procexp64 --> Ring-3 Process Inspection & Memory Mapping
```

> [!NOTE] 🎙️ **Instructor Lecture Notes**
> Walk through the diagram. The student's laptop becomes both the monitoring subject and the analyst console: Wireshark monitors the network interface, Sysinternals monitors memory/processes, and Splunk ingests local event logs on port 8000.

---

## Slide 05: Installing Wireshark & Npcap Packet Driver

> **Category:** `STEP 1: NETWORK VISIBILITY`

### Step 1: Installing Wireshark & Npcap Driver

Wireshark is the world's foremost network protocol analyzer. It allows us to see network traffic at microscopic detail:

1. **Download Installer**: Navigate to wireshark.org/download.html and download the Windows Installer (64-bit) .
2. **Component Selection**: Keep all default tools selected: Wireshark, TShark, Plugins/Extensions, and File Type associations.
3. **Install Npcap**: Crucial Step! Check "Install Npcap". In the Npcap wizard, check: "Support raw 802.11 traffic" and "Restrict Npcap driver's access to Administrators only" .
4. **Complete & Reboot**: Finish installation. If prompted by Npcap, reboot or restart network services to bind the driver.

> [!NOTE] 🎙️ **Instructor Lecture Notes**
> Guide students through installing Wireshark. Emphasize that Npcap is the critical component — without Npcap, Wireshark cannot capture any live packets on Windows. Ensure they do NOT check 'Install WinPcap in API-compatible Mode' unless required by older tools.

---

## Slide 06: Verifying Wireshark & First Packet Capture

> **Category:** `VERIFICATION & TESTING`

### Verifying Wireshark Functionality

Verify that your network interface is correctly capturing packets and responding to display filters:

- **1. Select Active Adapter**: Launch Wireshark. Look for the adapter with active traffic sparklines (usually Wi-Fi or Ethernet ). Double-click to begin capturing.
- **2. Generate Test Traffic**: Open your web browser and navigate to example.com or ping a public DNS server from your terminal: ping 8.8.8.8 .

#### Testing Core Display Filters in the Filter Bar:

```bash
# Filter 1: Show only DNS queries and responses
dns

# Filter 2: Show only web HTTP requests
http.request.method == "GET" || http.request.method == "POST"

# Filter 3: Show only TCP SYN packets (Connection Initiation)
tcp.flags.syn == 1 && tcp.flags.ack == 0
```

> [!NOTE] 🎙️ **Instructor Lecture Notes**
> Have students open Wireshark and look at the interface sparklines. Double click on Wi-Fi or Ethernet. Apply a simple display filter like 'dns || http'. Open a browser and visit a website to see the live packets streaming in.

---

## Slide 07: Deploying the Sysinternals Suite

> **Category:** `STEP 2: ENDPOINT VISIBILITY`

### Step 2: Deploying the Sysinternals Suite

The Sysinternals Suite is the gold standard toolkit for Windows internals, process analysis, and forensic troubleshooting:

1. **Download Suite ZIP**: Visit learn.microsoft.com/sysinternals and download SysinternalsSuite.zip (~50 MB).
2. **Extract to Dedicated Folder**: Create a dedicated folder: C:\Tools\Sysinternals and extract all contents there.
3. **Add to System PATH**: Add C:\Tools\Sysinternals to your Windows Environment System PATH variable for instant terminal access.
4. **Accept EULA Script**: Run from admin terminal to suppress prompts: reg add HKCU\Software\Sysinternals /v EulaAccepted /t REG_DWORD /d 1 /f

> [!NOTE] 🎙️ **Instructor Lecture Notes**
> Walk through deploying Sysinternals. It is a standalone set of portable utilities by Mark Russinovich from Microsoft. Tell students to create C:\Tools\Sysinternals, extract the zip there, and optionally add it to their system PATH so they can run tools from any cmd terminal.

---

## Slide 08: Configuring Process Explorer & Process Hacker

> **Category:** `HOST INSPECTION SETUP`

### Configuring Process Explorer with VirusTotal

Transform Process Explorer from a basic task manager into a live malware hunting console:

- **1. Run as Administrator**: Right-click procexp64.exe and select "Run as administrator" . Admin privileges are mandatory to view system-level services and handle tables.
- **2. Enable VirusTotal.com Integration**: Click Options -> VirusTotal.com -> Check VirusTotal.com . Accept terms. Process Explorer will hash every running binary and query VirusTotal!

> [!NOTE]
> 🎯 What to Look for in the VirusTotal Column 0 / 75 (Green): Clean, verified executable known by all commercial antivirus engines. N / 75 (Red, e.g. 48/75): Flagged as malicious trojan/ransomware by 48 vendors — investigate immediately! Unknown / Hash not found: Unseen custom binary or newly compiled payload — high suspicion!

> [!NOTE] 🎙️ **Instructor Lecture Notes**
> Show students how to run Process Explorer or Process Hacker as Administrator. Crucial step: Enable Options -> VirusTotal.com -> Check VirusTotal.com. This submits hashes of every running process to VirusTotal in real time to immediately spot known malware with 0/70 vs 55/70 flags!

---

## Slide 09: Configuring Sysinternals Autoruns

> **Category:** `HOST INSPECTION SETUP`

### Configuring Autoruns for Persistence Hunting

Autoruns shows every program, DLL, driver, and task configured to execute automatically at boot or user logon:

- **1. Run Autoruns64 as Administrator**: Launch Autoruns64.exe with Administrator privileges so it can inspect machine-wide keys in HKLM and hidden drivers.
- **2. The Golden Filter Setting**: In the top menu, click Options -> Scan Options . Check: ✅ Hide Microsoft Entries ✅ Hide Windows Entries ✅ Verify Code Signatures

> [!WARNING]
> ⚡ The Magic of Filtering OS Noise By hiding Microsoft and Windows entries, you reduce the list from 2,000+ entries down to ~20 third-party items! Any persistence mechanism installed by an attacker (malicious service, Run key, or scheduled task) will stand out immediately in bold red/yellow!

> [!NOTE] 🎙️ **Instructor Lecture Notes**
> Show how to set up Autoruns. Tell students to run Autoruns64.exe as Administrator. The most critical setting: Options -> Hide Microsoft Entries and Hide Windows Entries. This filters out 95% of the legitimate OS noise, leaving only user-installed and potential attacker persistence mechanisms!

---

## Slide 10: Choosing the Student SIEM: Why Splunk Enterprise Free?

> **Category:** `STEP 3: SIEM SELECTION`

### Why Splunk Enterprise Free for Our Hands-On SOC Lab?

Selecting the right SIEM platform for student laptops requires balancing enterprise realism with hardware efficiency:

- **1. Industry Market Leader**: Splunk is deployed in over 85% of Fortune 100 SOCs. Learning Splunk SPL gives students immediately marketable job skills.
- **2. Generous Free License**: Includes a perpetual 500 MB/day free ingestion license — more than enough for ingesting local event logs and lab exercise PCAPs!
- **3. Zero VM Overhead**: Installs directly on Windows and macOS as a background service. Consumes < 400 MB of idle RAM vs 8+ GB for virtualized SIEMs!

> [!NOTE]
> 🔄 Alternative Options Available For students interested in Open Source: Wazuh (SIEM/XDR) can be deployed via a lightweight cloud trial sandbox. For cloud-native EDR: LimaCharlie (which we use in Lab 10) requires zero server installation.

> [!NOTE] 🎙️ **Instructor Lecture Notes**
> Explain why we chose Splunk Enterprise Free for their laptops. It is the enterprise market leader. The free license includes 500 MB per day of log ingestion, forever. It installs as a native Windows application in under 5 minutes without needing a virtual machine.

---

## Slide 11: Step-by-Step Splunk Installation on Laptop

> **Category:** `SPLUNK INSTALLATION`

### Step-by-Step Splunk Enterprise Installation

Follow these exact steps to deploy the local Splunk instance on your machine:

1. **Download MSI Installer**: Go to splunk.com/download -> Splunk Enterprise -> Windows (64-bit) .msi (~480 MB).
2. **Run Installer Wizard**: Double-click the MSI. Accept the license agreement. Keep default install path: C:\Program Files\Splunk .
3. **Set Admin Credentials**: Important! Create administrator credentials: Username: admin Password: SOCLab2026! (Write this down!)
4. **Finish & Launch Web**: Click Install. Once finished, check "Launch Splunk Enterprise" and click Finish. It opens your browser to port 8000.

> [!NOTE] 🎙️ **Instructor Lecture Notes**
> Walk through the Splunk installer steps: download MSI, run installer, specify username/password (write it down!), keep default port 8000, and wait ~3 minutes for the service to start.

---

## Slide 12: Accessing Splunk Web Console & Navigation

> **Category:** `SPLUNK INTERACTION`

### Logging into Splunk Web & Orientation

Splunk runs a local web server providing full access to its search and visualization engine:

- **1. Open Web Browser**: Open Google Chrome, Firefox, or Edge and navigate to: http://127.0.0.1:8000 (or http://localhost:8000 ).
- **2. Authenticate**: Enter the credentials you created during installation: Username: admin Password: SOCLab2026!

> [!NOTE]
> 🧭 Key Interface Landmark: "Search & Reporting" On the left-hand navigation panel, click the green icon labeled "Search & Reporting" . This is the primary analyst interface where we execute SPL (Search Processing Language) queries, filter logs, and generate alert dashboards.

> [!NOTE] 🎙️ **Instructor Lecture Notes**
> Show how to access http://127.0.0.1:8000 in Chrome or Edge. Log in with admin and the password. Point out the 'Search & Reporting' app on the left navigation bar — that is where analysts spend their time querying logs.

---

## Slide 13: Ingesting Local Windows Security Event Logs

> **Category:** `DATA ONBOARDING`

### Connecting Your First Data Source: Local Event Logs

Configure Splunk to ingest real-time Windows Event Logs directly from your laptop:

1. **Navigate to Data Inputs**: In top menu: click Settings -> under Data section, click Data Inputs .
2. **Select Windows Logs**: Find "Local event log collection" and click "Add New" .
3. **Choose Channels**: Under Select Event Logs, select: ✅ Security ✅ System ✅ Application
4. **Save & Ingest**: Keep index as default or select wineventlog , click Review -> Submit . Your local events are now streaming live into Splunk!

> [!NOTE] 🎙️ **Instructor Lecture Notes**
> Guide students through onboarding their first real log source into Splunk: Settings -> Data Inputs -> Local Event Log Collection -> Choose 'Security', 'System', and 'Application'. Set the index to 'wineventlog'. In under 60 seconds, their personal machine's live security events stream into Splunk!

---

## Slide 14: Executing Your First SPL Queries in Splunk

> **Category:** `HANDS-ON SPL QUERYING`

### Executing Your First Search Processing Language (SPL) Queries

Go to Search & Reporting . Set time range to "All time" or "Last 24 hours" and run these fundamental queries:

#### Query 1: Find All Successful Logons (Event ID 4624)

```spl
source="WinEventLog:Security" EventCode=4624
| stats count by user, Logon_Type
| sort - count
```

#### Query 2: Hunt for Failed Logon Attempts (Event ID 4625)

```spl
source="WinEventLog:Security" EventCode=4625
| table _time, user, Sub_Status, Source_Network_Address
| sort - _time
```

#### Query 3: Detect Newly Created Processes (Event ID 4688)

```spl
source="WinEventLog:Security" EventCode=4688
| stats count by New_Process_Name
| sort - count
```

> [!NOTE] 🎙️ **Instructor Lecture Notes**
> Have students open Search & Reporting and run their first query. Show them how to query successful logons (EventCode=4624) and failed logons (EventCode=4625). Demonstrate pipes (|) and the stats command. This is their first true hands-on SOC analyst experience!

---

## Slide 15: Setting up Phishing & Triage Tools (CyberChef)

> **Category:** `STEP 4: TRIAGE UTILITIES`

### Step 4: Setting up CyberChef & Phishing Analysis Utilities

A SOC analyst frequently analyzes suspicious strings, encoded payloads, and phishing links. We use dedicated offline utilities:

- **CyberChef (GCHQ)**: The "Cyber Swiss Army Knife". Download the offline standalone bundle from github.com/gchq/CyberChef . Runs 100% locally in your browser.
- **Defang Utilities**: Converts dangerous live URLs into safe non-clickable text for ticketing systems: http://evil.com ➡️ hxxp://evil[.]com .
- **Header Analyzers**: Save bookmarks for: Microsoft Message Header Analyzer (mha.azurewebsites.net) and MXToolbox for SPF/DKIM verification.

> [!NOTE]
> 🔒 The Cardinal Rule of Phishing Triage Never open live malicious URLs in your personal browser! Always defang URLs before pasting into ticketing tools, and detonate or analyze samples inside sandboxes or offline decoders like CyberChef.

> [!NOTE] 🎙️ **Instructor Lecture Notes**
> Introduce CyberChef (The Cyber Swiss Army Knife by GCHQ). Students should download the standalone offline HTML bundle (cyberchef.htm) so they can decode Base64, defang URLs, and inspect payloads safely without sending sensitive data to external web services.

---

## Slide 16: Alternative Free Cloud Sandbox Options

> **Category:** `CLOUD LAB ALTERNATIVES`

### Cloud-Based Alternatives for Constrained Hardware

If a student has a restricted device (e.g. Chromebook or locked enterprise laptop), these cloud options provide full access:

- **LimaCharlie Cloud EDR / SecOps Cloud**: Used in Lab 10. Free tier includes up to 2 active sensors forever. Cloud-hosted web console — requires installing only a tiny 15 MB sensor on the endpoint. Zero server setup required!
- **Wazuh Cloud Trial Sandbox**: Full Open-Source SIEM + XDR platform. Offers free 14-day cloud sandbox environments with pre-loaded alert scenarios without requiring local installation.

> [!NOTE]
> 💡 Recommended Course Path We stick with Native Wireshark + Sysinternals + Splunk Enterprise Free as our primary workstation stack for maximum speed, offline independence, and direct hands-on control!

> [!NOTE] 🎙️ **Instructor Lecture Notes**
> Mention alternative cloud-based options for students whose laptops are underpowered or running locked-down corporate OS. Highlight LimaCharlie (already used in Lab 10) and Wazuh Cloud trial sandbox.

---

## Slide 17: The 6-Point Readiness Verification Checklist

> **Category:** `LAB READINESS AUDIT`

### The 6-Point Workstation Readiness Checklist

Before concluding today's lab, verify that all six operational components are functional on your laptop:

- **✅ 1. Wireshark Capture**: Wireshark launches and captures live packets from your network interface without Npcap errors.
- **✅ 2. Process Explorer Admin**: procexp64.exe runs as Administrator and displays live VirusTotal reputation scores.
- **✅ 3. Autoruns Configured**: Autoruns64.exe launches and successfully filters out Microsoft and Windows OS entries.
- **✅ 4. Splunk Web Online**: http://127.0.0.1:8000 opens in your browser and accepts your admin login credentials.
- **✅ 5. Live Events Ingested**: Executing source="WinEventLog:Security" in Splunk returns real event records from your system.
- **✅ 6. CyberChef Operational**: CyberChef loads in your browser offline and successfully decodes a sample Base64 test string.

> [!NOTE] 🎙️ **Instructor Lecture Notes**
> Before students leave Lab 2, have them verify this 6-point checklist. When all 6 items are checked off, their laptop is officially certified as a ready SOC Analyst Workstation.

---

## Slide 18: Summary & Preparation for Week 3

> **Category:** `CONCLUSION & NEXT STEPS`

### Summary: Ready for Practical Cyber Operations

Congratulations! Your personal machine is now fully equipped as a defensive security operations workstation:

- **Milestone Achieved**: You have deployed the complete SOC analyst triage stack: packet-level network visibility, process & persistence host inspection, and centralized SIEM log collection.
- **Preview: Week 3 — Phishing Analysis Part I**: Next week, we enter active threat analysis: dissecting real phishing emails, validating SPF/DKIM/DMARC headers, and uncovering malicious links!

> [!NOTE]
> Homework / Action Item Keep your Splunk service running. Generate daily traffic on your laptop so your Splunk index builds a rich baseline of normal activity for our upcoming triage exercises.

> [!NOTE] 🎙️ **Instructor Lecture Notes**
> Congratulate students. Their environment is now fully deployed. Preview Week 3: Phishing Analysis Part 1, where we examine real phishing email headers and dissect social engineering tactics.

---

## 🎯 Summary & Key Takeaways

- **Module:** Lab 02: SOC Lab Environment Setup & Toolchain Deployment

- **Core Competencies Developed:** Telemetry ingestion, forensic event analysis, and defensive toolchain deployment.

- **Course Reference:** Cybersecurity Operations Practical Labs by **Hussein Al-Selwi**.
