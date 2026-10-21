# المعمل 09: أمان النقاط الطرفية - الجزء الثاني: سجل النظام (Registry) وأساليب البقاء والاستدامة (Persistence)

> **المقرر:** عمليات الأمن السيبراني (مختبر الـ SOC - Cybersecurity Operations)  
> **المحاضر:** Hussein Al-Selwi  
> **إجمالي عدد الشرائح:** 17 شريحة  
> **العرض التقديمي المصدري:** `Endpoint_Security_Part2_Lab9_AR.html`  

### 📋 نبذة عامة وأهداف الوحدة التدريبية
التحقيق الجنائي في آليات استدامة المهاجمين داخل البيئة: خلايا سجل النظام الخمس (The Five Hives)، مفاتيح التشغيل التلقائي Run و RunOnce، إنشاء الخدمات الخبيثة عبر سطر الأوامر باستخدام sc.exe، زرع المهام المجدولة عبر schtasks، والفحص الجنائي الاحترافي باستخدام أداة Autoruns.

---

## 📑 جدول المحتويات

- [الشريحة 01: المقدمة](#slide-01-المقدمة)
- [الشريحة 02: آليات الثبات والتخفي (Persistence)](#slide-02-آليات-الثبات-والتخفي-persistence)
- [الشريحة 03: سجل النظام: النشأة والوظيفة](#slide-03-سجل-النظام-النشأة-والوظيفة)
- [الشريحة 04: معاينة السجل عبر Registry Editor](#slide-04-معاينة-السجل-عبر-registry-editor)
- [الشريحة 05: خلايا السجل الخمس (خلايا السجل الخمس (The Five Hives))](#slide-05-خلايا-السجل-الخمس-خلايا-السجل-الخمس-the-five-hives)
- [الشريحة 06: ثبات السجل عبر مفاتيح Run و RunOnce](#slide-06-ثبات-السجل-عبر-مفاتيح-run-و-runonce)
- [الشريحة 07: فحص مفاتيح Run عبر المحرر وسطر الأوامر](#slide-07-فحص-مفاتيح-run-عبر-المحرر-وسطر-الأوامر)
- [الشريحة 08: أداة Autoruns من Sysinternals](#slide-08-أداة-autoruns-من-sysinternals)
- [الشريحة 09: خدمات ويندوز: ما هي ولماذا تُستهدف؟](#slide-09-خدمات-ويندوز-ما-هي-ولماذا-تُستهدف؟)
- [الشريحة 10: معاينة الخدمات عبر أداة Services](#slide-10-معاينة-الخدمات-عبر-أداة-services)
- [الشريحة 11: إدارة الخدمات عبر سطر الأوامر (sc.exe)](#slide-11-إدارة-الخدمات-عبر-سطر-الأوامر-sc-exe)
- [الشريحة 12: فحص واستعلام الخدمات: query و qc](#slide-12-فحص-واستعلام-الخدمات-query-و-qc)
- [الشريحة 13: 3. المهام المجدولة (Scheduled Tasks) — What & Why](#slide-13-3-المهام-المجدولة-scheduled-tasks-what-why)
- [الشريحة 14: معاينة المهام عبر Task Scheduler](#slide-14-معاينة-المهام-عبر-task-scheduler)
- [الشريحة 15: إدارة المهام عبر سطر الأوامر (schtasks.exe)](#slide-15-إدارة-المهام-عبر-سطر-الأوامر-schtasks-exe)
- [الشريحة 16: استعلام وفحص المهام: schtasks /query](#slide-16-استعلام-وفحص-المهام-schtasks-query)
- [الشريحة 17: دليل المقارنة السريع لمواقع الثبات الثلاثة](#slide-17-دليل-المقارنة-السريع-لمواقع-الثبات-الثلاثة)

---

## الشريحة 01: المقدمة

> **التصنيف / الفئة:** `كشف التهديدات والاستجابة للحوادث · IDR`

### Endpoint Security Part II

آليات الثبات التي يستخدمها المهاجمون للبقاء بعد إعادة تشغيل الجهاز والتخفي — سجل النظام، الخدمات، والمهام المجدولة — ونشر EDR لاكتشافها.

المعمل 09 – آليات الثبات (Persistence) ونشر الـ EDR

> [!NOTE] 🎙️ **ملاحظات وتوجيهات المحاضر (Instructor Lecture Notes)**
> رحب بعودة الطلاب للجزء الثاني من معمل أمن الأجهزة والأنظمة (Endpoint Security). يبني هذا المعمل مباشرة على الجزء الأول — فبعد أن تعلمنا كيفية قراءة شجرة العمليات والسلوك الطبيعي للنظام، ننتقل الآن إلى كيفية بقاء المهاجمين داخل الأجهزة بعد الاختراق الأولي: آليات الثبات (Persistence Mechanisms) عبر الـ Registry، والخدمات (Services)، والمهام المجدولة (3. المهام المجدولة (Scheduled Tasks)). ونختم بنشر LimaCharlie كمنصة EDR لاكتشاف هذه الأنشطة مباشرة.

---

## الشريحة 02: آليات الثبات والتخفي (Persistence)

> **التصنيف / الفئة:** `آليات الثبات والتخفي (Persistence)`

### كيف يضمن المهاجم بقاء سيطرته على الجهاز؟

Once an attacker lands on a machine, the next problem they need to solve is surviving a reboot or logoff . Windows gives them several built-in mechanisms to do this — we'll cover three, in this order:

- **1. 1. مفاتيح سجل النظام (Registry Keys)**: مفاتيح Run و RunOnce التي تشغل البرامج تلقائياً عند تسجيل الدخول، سواء في مسار HKCU أو HKLM.
- **2. Services**: 2. خدمات ويندوز (Windows Services) that start automatically at boot, often running as SYSTEM.
- **3. 3. المهام المجدولة (Scheduled Tasks)**: مهام مجهزة للعمل وفق جدول زمني أو أحداث معينة، وتعمل بشكل مستقل عن تسجيل دخول المستخدم.

> [!IMPORTANT]
> لماذا تعد معرفة هذه الآليات جوهرية لمحلل الـ SOC؟ all three are legitimate Windows features that IT and software rely on every day — which is exactly why attackers abuse them. Persistence detection is about knowing what's normal here so the abnormal stands out.

> [!NOTE] 🎙️ **ملاحظات وتوجيهات المحاضر (Instructor Lecture Notes)**
> قدّم آليات الثبات الثلاث التي سنغطيها بهذا الترتيب: مفاتيح الـ Registry أولاً، ثم خدمات ويندوز (Services)، ثم المهام المجدولة (3. المهام المجدولة (Scheduled Tasks)). تشترك جميعها في هدف واحد — الصمود أمام إعادة التشغيل أو تسجيل الخروج حتى لا تفقد البرمجية الخبيثة موطئ قدمها.

---

## الشريحة 03: سجل النظام: النشأة والوظيفة

> **التصنيف / الفئة:** `REGISTRY KEYS`

### سجل النظام (Registry) — النشأة والوظيفة

In the past, Windows stored configuration in plain text initialization files — files with a .ini extension, one per app. Microsoft replaced this with a single hierarchical database : the Registry , which stores all configuration for the system and every installed app in one place.

1. **خطوة 1**: .ini files
2. **خطوة 2**: The Registry

> [!NOTE] 🎙️ **ملاحظات وتوجيهات المحاضر (Instructor Lecture Notes)**
> اشرح بإيجاز نشأة سجل النظام (Registry). قبل ظهوره، كانت برامج ويندوز تخزن إعداداتها في ملفات نصية مبعثرة بصيغة .ini. استبدلت مايكروسوفت ذلك بقاعدة بيانات هرمية موحدة وسريعة هي الـ Registry.

---

## الشريحة 04: معاينة السجل عبر Registry Editor

> **التصنيف / الفئة:** `REGISTRY KEYS`

### معاينة السجل عبر أداة Registry Editor

The Registry is viewed and edited with a built-in Windows tool: Registry Editor ( regedit.exe ). Launch it from the Run dialog or Start menu search.

```bash
Run>
regedit
Opens Registry Editor
```

When Registry Editor opens, the left-hand pane shows five root folders . These are called hives — each one is a separate top-level branch of the Registry, holding a different category of configuration data.

HKLM HKEY_LOCAL_MACHINE HKCU HKEY_CURRENT_USER HKCR HKEY_CLASSES_ROOT HKU HKEY_USERS HKCC HKEY_CURRENT_CONFIG

> [!NOTE] 🎙️ **ملاحظات وتوجيهات المحاضر (Instructor Lecture Notes)**
> وضح للطلاب كيفية فتح ومعاينة الـ Registry: محرر السجل regedit.exe. عند فتحه، تعرض اللوحة اليسرى خمسة مجلدات جذرية رئيسية — تُعرف بالـ Hives. سنعرف كل منها في الشريحة التالية، ولكن رسخ في ذهنهم شكل الأداة والتسلسل الهرمي العام.

---

## الشريحة 05: خلايا السجل الخمس (خلايا السجل الخمس (The Five Hives))

> **التصنيف / الفئة:** `REGISTRY KEYS`

### خلايا السجل الخمس (The Five Hives)

تحتوي كل خلية (Hive) على قطاع مخصص من إعدادات النظام:

| Hive | Full Name | Main Purpose |
| --- | --- | --- |
| HKLM | HKEY_LOCAL_MACHINE | System-wide settings, hardware, services, installed software |
| HKCU | HKEY_CURRENT_USER | Settings specific to the currently logged-in user |
| HKCR | HKEY_CLASSES_ROOT | File associations and registered Windows classes — which program opens a particular file type |
| HKU | HKEY_USERS | Registry settings for all loaded user profiles |
| HKCC | HKEY_CURRENT_CONFIG | Current hardware configuration |

> [!NOTE] 🎙️ **ملاحظات وتوجيهات المحاضر (Instructor Lecture Notes)**
> استعرض خلايا السجل الخمس (خلايا السجل الخمس (The Five Hives)) ووظيفة كل منها: HKLM لإعدادات النظام والبرامج المثبتة والخدمات؛ HKCU لإعدادات المستخدم الحالي المسجل دخوله؛ HKCR لربط امتدادات الملفات والـ COM Classes؛ HKU لجميع ملفات تعريف المستخدمين المحملة؛ و HKCC لبيانات العتاد الحالية.

---

## الشريحة 06: ثبات السجل عبر مفاتيح Run و RunOnce

> **التصنيف / الفئة:** `REGISTRY KEYS`

### آليات الثبات في السجل — مفاتيح Run و RunOnce

The two Registry keys most commonly abused for persistence are Run and RunOnce . Anything listed under either key launches automatically at logon — which is exactly the behavior an attacker wants for a persistent foothold.

- **Run**: يعمل في كل مرة يقوم فيها المستخدم بتسجيل الدخول. تبقى القيمة ثابتة في السجل ولا تُحذف بعد التنفيذ.
- **RunOnce**: يعمل لمرة واحدة فقط عند تسجيل الدخول التالي، ثم يقوم نظام Windows بحذف القيمة تلقائياً.

Both keys exist under HKCU and HKLM , and the distinction matters:

HKCU — runs only for that one logged-in user HKLM — runs for any user machine-wide, needs admin rights to write

> [!NOTE] 🎙️ **ملاحظات وتوجيهات المحاضر (Instructor Lecture Notes)**
> اربط الآن خلايا السجل بآليات الثبات. المفاتيح الأكثر استغلالاً من المهاجمين هي Run و RunOnce، وهي موجودة في كل من HKCU (تعمل للمستخدم الحالي فقط) و HKLM (تعمل لأي مستخدم على الجهاز وتتطلب صلاحيات مدير). مفتاح Run يعمل مع كل تسجيل دخول، بينما RunOnce يعمل لمرة واحدة ثم يُحذف تلقائياً.

---

## الشريحة 07: فحص مفاتيح Run عبر المحرر وسطر الأوامر

> **التصنيف / الفئة:** `REGISTRY KEYS`

### Viewing Run & مفتاح التشغيل لمرة واحدة (RunOnce Key)s

These keys can be checked two ways: browsing to them directly in Registry Editor , or querying them from the command line with reg query .

| العنصر / المفتاح | الوصف / القيمة |
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
> ما الذي تبحث عنه كمحلل أمني؟ any value pointing to an unfamiliar executable, a script interpreter ( powershell.exe , wscript.exe ), an unusual path like %TEMP% , or an entry the user or IT can't explain.

> [!NOTE] 🎙️ **ملاحظات وتوجيهات المحاضر (Instructor Lecture Notes)**
> اعرض للطلاب طريقتي فحص هذه المفاتيح: المسار الرسومي عبر Registry Editor، والاستعلام السريع عبر سطر الأوامر بأمر reg query. استعرض المسارات الكاملة الأربعة لمفاتيح Run و RunOnce في HKCU و HKLM.

---

## الشريحة 08: أداة Autoruns من Sysinternals

> **التصنيف / الفئة:** `REGISTRY KEYS`

### أداة Autoruns — حزمة Microsoft Sysinternals

Autoruns , a free Sysinternals tool, shows every autostart location on a system in one window — registry run keys, services, scheduled tasks, and more — instead of checking each one separately.

It's most powerful when paired with baselining : capturing a snapshot of what's normal, so anything new later stands out on its own.

1. **Baseline**: Snapshot a clean system
2. **Rescan**: Snapshot again later
3. **Diff**: New entries stand out

> [!NOTE] 🎙️ **ملاحظات وتوجيهات المحاضر (Instructor Lecture Notes)**
> Introduce Autoruns by Sysinternals — a tool that shows every autostart location on a system in one view. Then introduce baselining: capturing what's normal for a clean system so a later scan's differences immediately stand out.

---

## الشريحة 09: خدمات ويندوز: ما هي ولماذا تُستهدف؟

> **التصنيف / الفئة:** `SERVICES`

### خدمات ويندوز (Services) — ما هي ولماذا تُستهدف؟

A Service is a background process managed by Windows that can start automatically at boot — before any user even logs in — and often runs under a high-privilege account like SYSTEM .

- **Runs With High Privilege**: غالباً ما تعمل بحساب SYSTEM — وهو أعلى صلاحية في ويندوز وأقوى من حساب المستخدم العادي المخترق.
- **No Login Needed**: تبدأ فور إقلاع الجهاز، وبالتالي تضمن بقاء الاتصال بالمخترق حتى لو لم يسجل أي موظف دخوله.

مع وجود عشرات الخدمات الطبيعية التي تعمل في أي جهاز، يسهل على المهاجم إنشاء خدمة باسم مقارب للشرعي للتخفي.

> [!NOTE] 🎙️ **ملاحظات وتوجيهات المحاضر (Instructor Lecture Notes)**
> Define 2. خدمات ويندوز (Windows Services): background processes managed by the Service Control Manager, most starting automatically at boot before any user logs in, often running as SYSTEM. Explain why attackers target them: high privilege, no need for a logged-in user, and they blend in among the many legitimate services already on a system.

---

## الشريحة 10: معاينة الخدمات عبر أداة Services

> **التصنيف / الفئة:** `SERVICES`

### معاينة الخدمات عبر أداة الخدمات (services.msc)

The built-in GUI for services is the Services app — opened by running services.msc . It lists every service with its status, startup type, and the account it runs as.

```bash
Run>
services.msc
Opens the Services app
```

> [!NOTE] 🎙️ **ملاحظات وتوجيهات المحاضر (Instructor Lecture Notes)**
> اعرض للطلاب أداة Services الرسومية services.msc — الواجهة الرسمية لمعاينة وإدارة الخدمات، مع توضيح حقول اسم الخدمة، الوصف، الحالة (Running/Stopped)، نوع بدء التشغيل (Automatic/Manual)، وحساب تسجيل الدخول.

---

## الشريحة 11: إدارة الخدمات عبر سطر الأوامر (sc.exe)

> **التصنيف / الفئة:** `SERVICES`

### إدارة الخدمات عبر سطر الأوامر باستخدام أداة sc.exe

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

> [!NOTE] 🎙️ **ملاحظات وتوجيهات المحاضر (Instructor Lecture Notes)**
> قدّم أداة سطر الأوامر sc.exe (Service Controller)، وخياراتها الأساسية لإنشاء الخدمات، وتشغيلها، وإيقافها، وتعديل إعداداتها، وحذفها.

---

## الشريحة 12: فحص واستعلام الخدمات: query و qc

> **التصنيف / الفئة:** `SERVICES`

### فحص واستعلام الخدمات وتحليل مساراتها

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
> تذكير هام للمحلل: Autoruns has a dedicated Services tab too — the same information, alongside every other autostart location, in one place.

> [!NOTE] 🎙️ **ملاحظات وتوجيهات المحاضر (Instructor Lecture Notes)**
> اعرض طرق الفحص الآمنة (Read-Only) للخدمات: الأمر sc query لمعرفة الحالة، والأمر sc qc لمعرفة تفاصيل التكوين ومسار الملف التنفيذي، وأمر wmic الرائع الذي يفرز جميع الخدمات بمساراتها في جدول واحد لاكتشاف المسارات الغريبة فوراً.

---

## الشريحة 13: 3. المهام المجدولة (Scheduled Tasks) — What & Why

> **التصنيف / الفئة:** `SCHEDULED TASKS`

A Scheduled Task runs a program or script automatically on a trigger — a set time, at logon, at boot, or on some other event. Windows and installed software use them normally for things like updates, cleanup, and backups.

Attackers use the same trigger to get their own persistence: a task set to run onlogon or on a schedule survives reboot just like a service, and with dozens of legitimate scheduled tasks already on a system, one more is easy to miss.

> [!NOTE] 🎙️ **ملاحظات وتوجيهات المحاضر (Instructor Lecture Notes)**
> عرّف المهام المجدولة (Scheduled Tasks): ميزة في ويندوز تشغل برنامجاً أو سكربتاً بناءً على محفز (وقت محدد، عند تسجيل الدخول، عند الإقلاع، أو عند وقوع حدث). اشرح لماذا يستغلها المهاجمون: تحقق نفس ثبات الخدمات، ويمكن تشغيلها بصلاحيات عليا، وتتخفى وسط مئات المهام الشرعية للنظام.

---

## الشريحة 14: معاينة المهام عبر Task Scheduler

> **التصنيف / الفئة:** `SCHEDULED TASKS`

### معاينة المهام المجدولة عبر أداة (taskschd.msc)

The built-in GUI is Task Scheduler — opened by running taskschd.msc . It shows every task's trigger, the action it runs, and its history.

```bash
Run>
taskschd.msc
Opens Task Scheduler
```

> [!NOTE] 🎙️ **ملاحظات وتوجيهات المحاضر (Instructor Lecture Notes)**
> اعرض للطلاب أداة Task Scheduler الرسومية taskschd.msc — الواجهة الرسمية لإدارة المهام المجدولة، والمنظمة في شجرة مكتبة المهام وتعرض المحفزات، والإجراءات (Actions)، وسجل التنفيذ لكل مهمة.

---

## الشريحة 15: إدارة المهام عبر سطر الأوامر (schtasks.exe)

> **التصنيف / الفئة:** `SCHEDULED TASKS`

### إدارة المهام المجدولة عبر سطر الأوامر باستخدام schtasks.exe

From the command line, tasks are managed with schtasks .

```cmd
C:\>
schtasks /create /tn "MyTask" /tr "C:\path\to\file.exe" /sc onlogon
Creates a task that runs at logon
C:\>
schtasks /delete /tn "MyTask" /f
Deletes the task without confirmation prompt
```

> [!NOTE] 🎙️ **ملاحظات وتوجيهات المحاضر (Instructor Lecture Notes)**
> قدّم أداة schtasks.exe، الأداة الرسمية في سطر الأوامر لإدارة المهام المجدولة، وخيارات الإنشاء والحذف المتاحة للمحللين والمهاجمين على حد سواء.

---

## الشريحة 16: استعلام وفحص المهام: schtasks /query

> **التصنيف / الفئة:** `SCHEDULED TASKS`

### فحص واستعلام المهام المجدولة عبر schtasks /query

استعراض وفحص المهام المجدولة يتم في وضع القراءة فقط — دون إجراء أي تعديل على النظام:

```cmd
C:\>
schtasks /query
عرض قائمة بجميع المهام المجدولة في النظام.
C:\>
schtasks /query /tn "MyTask" /fo LIST /v
Full detail on one task — trigger, action, run-as account, last result
```

> [!WARNING]
> ما الذي تبحث عنه كمحلل أمني؟ a task name mimicking a legitimate one, an action pointing to an unfamiliar path, or a trigger like onlogon on a task with no clear business reason to run then.

> [!NOTE] 🎙️ **ملاحظات وتوجيهات المحاضر (Instructor Lecture Notes)**
> اعرض كيفية استعراض كافة المهام بأمر schtasks /query، وكيفية الحصول على التفاصيل الكاملة لمهمة معينة بأمر schtasks /query /tn مع تنسيق القائمة التفصيلي /fo LIST /v.

---

## الشريحة 17: دليل المقارنة السريع لمواقع الثبات الثلاثة

> **التصنيف / الفئة:** `SUMMARY`

### دليل الفحص المرجعي السريع لآليات الثبات الثلاث

تستطيع أداة Autoruns عرض هذه المواقع الثلاثة مجتمعة في شاشة واحدة. أما بشكل فردي، فإليك الأدوات الرسومية وأوامر الـ CLI المقابلة لكل منها:

Registry regedit reg query "HKCU\...\Run" reg query "HKLM\...\Run" Services services.msc sc query SvcName sc qc SvcName wmic service get Name,DisplayName,State,StartMode,PathName 3. المهام المجدولة (Scheduled Tasks) taskschd.msc schtasks /query schtasks /query /tn "MyTask" /fo LIST /v

> [!NOTE] 🎙️ **ملاحظات وتوجيهات المحاضر (Instructor Lecture Notes)**
> Recap slide: the GUI tool and the command-line options for viewing each of the three persistence locations covered — Registry, Services, and 3. المهام المجدولة (Scheduled Tasks) — side by side for quick reference.

---

## 🎯 الخلاصة ومخرجات التعلم

- **الوحدة التدريبية:** المعمل 09: أمان النقاط الطرفية - الجزء الثاني: سجل النظام (Registry) وأساليب البقاء والاستدامة (Persistence)

- **المهارات المكتسبة:** فهم عملي وتطبيقي عميق لكيفية الكشف، التحقيق، الاستجابة، وإدارة التهديدات الأمنية باحترافية داخل بيئة العمليات.

- **مرجع التدريب:** مختبر عمليات الأمن السيبراني العملي — إعداد وتقديم: **Hussein Al-Selwi**.
