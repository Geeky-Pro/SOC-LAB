# 🛡️ خطة تدريس القسم العملي – عمليات الأمن السيبراني (SOC Lab)

---

## 📋 معلومات المقرر

| البند | التفاصيل |
|-------|----------|
| **المادة** | عمليات الأمن السيبراني – Cybersecurity Operations |
| **القسم** | العملي (Lab) |
| **الدور** | معيد (Teaching Assistant) |
| **عدد المحاضرات** | 12 محاضرة (10 تعليمية + 2 اختبارات/مشاريع) |
| **المدة** | 12 أسبوع |
| **ساعات الأسبوع** | ساعتان |

---

## 📅 نظرة عامة على الأسابيع الـ 12

| الأسبوع | العنوان | النوع |
|---------|---------|-------|
| 1 | أساسيات SOC و Logs – شرح نظري عملي مع أمثلة | 📖 شرح |
| 2 | تثبيت بيئة المعمل (Lab Setup) | 🔧 إعداد |
| 3 | تحليل السجلات باستخدام SIEM (Splunk) | 🔬 لاب |
| 4 | تحليل حركة الشبكة (Wireshark + PCAP) | 🔬 لاب |
| 5 | أنظمة كشف التطفل (IDS – Suricata) | 🔬 لاب |
| 6 | **اختبار / مشروع منتصف الفصل** | 📝 تقييم |
| 7 | الاستجابة للحوادث الأمنية (Incident Response) | 🔬 لاب |
| 8 | التحقيق الرقمي وتحليل الذاكرة (Forensics) | 🔬 لاب |
| 9 | تحليل البرمجيات الخبيثة (Malware Analysis) | 🔬 لاب |
| 10 | Threat Intelligence + MITRE ATT&CK | 🔬 لاب |
| 11 | Threat Hunting + كتابة التقارير الأمنية | 🔬 لاب |
| 12 | **المشروع / الاختبار النهائي** | 📝 تقييم |

---

## 📖 الأسبوع 1: أساسيات SOC والـ Logs (شرح مع أمثلة)

> **الهدف**: بناء أساس قوي – الطالب يفهم ما هو SOC، لماذا موجود، ما هي الـ Logs، وكيف نقرأها

### 🕐 توزيع الوقت (ساعتان = 120 دقيقة)

| الوقت | المحتوى |
|-------|---------|
| 00:00 – 00:10 | تعارف + نظرة عامة على المادة والتقييم |
| 00:10 – 00:35 | ما هو SOC؟ الأدوار، المستويات، سير العمل |
| 00:35 – 00:55 | ما هي الـ Logs؟ أنواعها ولماذا مهمة |
| 00:55 – 01:05 | استراحة (10 دقائق) |
| 01:05 – 01:35 | قراءة وتحليل Logs – أمثلة حية على الشاشة |
| 01:35 – 01:50 | تمرين تفاعلي جماعي (Logs على الورق أو الشاشة) |
| 01:50 – 02:00 | تلخيص + تكليف الأسبوع القادم (تحضير الأجهزة) |

---

### 📌 الجزء 1: ما هو مركز عمليات الأمن (SOC)؟

#### التعريف
```
SOC = Security Operations Center
مركز متخصص يراقب ويحلل ويستجيب للتهديدات الأمنية 24/7
```

#### لماذا نحتاج SOC؟
اشرح بقصة واقعية:
```
💡 مثال تشبيهي:
"SOC مثل غرفة العمليات في المستشفى – تراقب كل المرضى (الأنظمة)
على شاشات (SIEM)، وإذا أي مريض وضعه خطر (Alert)،
الفريق الطبي (Analysts) يتدخل فوراً"

💡 مثال حقيقي:
"في 2020، شركة SolarWinds تعرضت لاختراق ضخم.
فرق SOC في الشركات المتأثرة هي اللي اكتشفت الاختراق
من خلال مراقبة Logs غير طبيعية"
```

#### أدوار فريق SOC (SOC Team Roles)

```
┌─────────────────────────────────────────────────────┐
│                    SOC Manager                       │
│              (مدير مركز العمليات)                     │
├──────────┬──────────────┬───────────────────────────┤
│          │              │                           │
│  Tier 1  │    Tier 2    │         Tier 3            │
│  Alert   │   Incident   │    Threat Hunter /        │
│ Analyst  │   Responder  │    Senior Analyst         │
│          │              │                           │
│ • مراقبة │ • تحقيق      │ • Threat Hunting          │
│   Alerts │   معمّق      │ • Malware Analysis        │
│ • تصنيف  │ • تحليل      │ • تطوير Detection         │
│   أولي   │   السبب      │   Rules                   │
│ • تصعيد  │   الجذري     │ • تحسين العمليات           │
│          │ • احتواء     │                           │
└──────────┴──────────────┴───────────────────────────┘
```

#### سير العمل في SOC (SOC Workflow)

```
Alert يوصل من SIEM
        ↓
Tier 1: هل هو True Positive أو False Positive?
        ↓
   ┌────┴────┐
   ↓         ↓
False     True
Positive  Positive
   ↓         ↓
إغلاق    تصعيد لـ Tier 2
التذكرة      ↓
          تحقيق معمّق
              ↓
          احتواء + إزالة
              ↓
          تقرير + دروس مستفادة
```

#### أسئلة تفاعلية اسألها للطلاب:
```
❓ "لو أنت محلل SOC ووصلك 200 Alert في ساعة، كيف تتعامل؟"
❓ "إيش الفرق بين Alert و Incident؟"
❓ "ليش مهم يكون SOC يشتغل 24/7؟"
```

---

### 📌 الجزء 2: ما هي الـ Logs؟

#### التعريف البسيط
```
Logs = سجلات تسجل كل شيء يحصل في النظام
مثل "كاميرات المراقبة" للأنظمة والشبكات

كل حدث يتم تسجيله: من دخل، متى دخل، إيش سوى، من وين جاء
```

#### لماذا الـ Logs مهمة لمحلل SOC؟
```
1. 🔍 الكشف: اكتشاف الأنشطة المشبوهة
2. 🔎 التحقيق: فهم ماذا حدث بالضبط ومتى
3. 📋 الامتثال: متطلبات قانونية وتنظيمية
4. 🛡️ الوقاية: التعلم من الأحداث السابقة
5. ⚖️ الإثبات: دليل رقمي في التحقيقات
```

#### أنواع الـ Logs الرئيسية

```
📁 أنواع Logs التي يتعامل معها محلل SOC:

┌─────────────────┬──────────────────────────────────┐
│ النوع            │ المصدر / الوصف                   │
├─────────────────┼──────────────────────────────────┤
│ System Logs     │ نظام التشغيل (Windows/Linux)     │
│ Auth Logs       │ تسجيل الدخول والخروج             │
│ Application Logs│ التطبيقات والبرامج               │
│ Web Server Logs │ Apache, Nginx, IIS               │
│ Firewall Logs   │ حركة المرور المسموحة/المحظورة    │
│ IDS/IPS Logs    │ محاولات الاختراق المكتشفة         │
│ DNS Logs        │ استعلامات أسماء النطاقات          │
│ Email Logs      │ الرسائل الواردة والصادرة          │
│ Proxy Logs      │ حركة تصفح الإنترنت              │
│ DHCP Logs       │ توزيع عناوين IP                  │
│ VPN Logs        │ اتصالات VPN                      │
└─────────────────┴──────────────────────────────────┘
```

---

### 📌 الجزء 3: قراءة وفهم الـ Logs (أمثلة حية)

#### 📋 مثال 1: Windows Event Log – تسجيل دخول ناجح

```
Log Name:      Security
Source:        Microsoft-Windows-Security-Auditing
Date:          2026-10-20 09:15:32
Event ID:      4624
Level:         Information
User:          DOMAIN\ahmed.ali
Computer:      WKS-FIN-PC01

Description:
An account was successfully logged on.

Subject:
  Security ID:    SYSTEM
  Account Name:   WKS-FIN-PC01$

Logon Information:
  Logon Type:     2          ← تسجيل دخول تفاعلي (جالس على الجهاز)
  Account Name:   ahmed.ali
  Account Domain: DOMAIN
  Logon ID:       0x3A7B2F

Network Information:
  Workstation:    WKS-FIN-PC01
  Source Address: 192.168.1.50
  Source Port:    52431
```

```
💡 اشرح للطلاب:
• Event ID 4624 = تسجيل دخول ناجح
• Logon Type 2 = الشخص جالس فعلياً على الجهاز (Interactive)
• Logon Type 3 = دخول عن بُعد عبر الشبكة (Network)
• Logon Type 10 = دخول عبر Remote Desktop (RDP)

❓ سؤال: "لو شفت Logon Type 10 الساعة 3 الفجر، إيش رأيك؟"
```

#### 📋 مثال 2: Windows Event Log – تسجيل دخول فاشل

```
Log Name:      Security
Source:        Microsoft-Windows-Security-Auditing
Date:          2026-10-20 03:22:15
Event ID:      4625
Level:         Information
User:          N/A
Computer:      SRV-DC01

Description:
An account failed to log on.

Subject:
  Account Name:   -
  
Logon Information:
  Account Name:   administrator
  Account Domain: DOMAIN
  Failure Reason: Unknown user name or bad password
  Status:         0xC000006D    ← كلمة مرور خاطئة
  Sub Status:     0xC000006A

Network Information:
  Source Address:  10.0.0.55
  Source Port:     49832
```

```
💡 اشرح للطلاب:
• Event ID 4625 = محاولة دخول فاشلة
• المحاولة على حساب "administrator" ← هدف شائع للمهاجمين
• الوقت 3:22 فجراً ← وقت مشبوه
• Status 0xC000006D = اسم المستخدم أو كلمة المرور خاطئة

❓ سؤال: "لو شفت 500 Event ID 4625 في 5 دقائق من نفس الـ IP، 
   إيش نوع الهجوم؟"
👉 الجواب: Brute Force Attack
```

#### 📋 مثال 3: Linux Auth Log – محاولة SSH فاشلة

```
Oct 20 03:15:22 web-server sshd[12345]: Failed password for root from 185.220.101.42 port 52431 ssh2
Oct 20 03:15:24 web-server sshd[12346]: Failed password for root from 185.220.101.42 port 52433 ssh2
Oct 20 03:15:25 web-server sshd[12347]: Failed password for root from 185.220.101.42 port 52435 ssh2
Oct 20 03:15:27 web-server sshd[12348]: Failed password for admin from 185.220.101.42 port 52437 ssh2
Oct 20 03:15:28 web-server sshd[12349]: Failed password for admin from 185.220.101.42 port 52439 ssh2
Oct 20 03:15:30 web-server sshd[12350]: Failed password for test from 185.220.101.42 port 52441 ssh2
Oct 20 03:15:32 web-server sshd[12351]: Accepted password for admin from 185.220.101.42 port 52443 ssh2
```

```
💡 اشرح للطلاب:
• المهاجم من IP: 185.220.101.42
• يجرب أسماء مستخدمين مختلفة: root, admin, test
• المحاولات بفارق ثوانٍ ← آلي (Bot/Script)
• ❌ آخر سطر: "Accepted password" ← المهاجم نجح بالدخول!

🚨 هذا هو اللي يخوّف – Brute Force نجح!

❓ سؤال: "إيش أول إجراء تسويه لو شفت هذا الـ Log؟"
👉 الجواب: 
  1. تغيير كلمة مرور admin فوراً
  2. حظر IP المهاجم
  3. مراجعة ماذا فعل المهاجم بعد الدخول
  4. فتح تذكرة Incident
```

#### 📋 مثال 4: Apache Web Server Log – محاولة SQL Injection

```
192.168.1.100 - - [20/Oct/2026:14:23:15 +0300] "GET /products?id=1 HTTP/1.1" 200 5432
192.168.1.100 - - [20/Oct/2026:14:23:18 +0300] "GET /products?id=1' HTTP/1.1" 500 1024
192.168.1.100 - - [20/Oct/2026:14:23:20 +0300] "GET /products?id=1' OR '1'='1 HTTP/1.1" 200 45231
192.168.1.100 - - [20/Oct/2026:14:23:22 +0300] "GET /products?id=1' UNION SELECT username,password FROM users-- HTTP/1.1" 200 8923
```

```
💡 اشرح للطلاب كل سطر:

السطر 1: طلب عادي → id=1 → Response 200 (OK) → حجم طبيعي
السطر 2: أضاف ' (فاصلة عليا) → Response 500 (Error) ← يختبر SQL Injection
السطر 3: OR '1'='1 → Response 200 → حجم كبير 45KB ← الحقنة نجحت!
السطر 4: UNION SELECT → يسحب بيانات المستخدمين وكلمات المرور ← سرقة بيانات!

🔍 مكونات السطر:
192.168.1.100          ← عنوان IP الطالب/المهاجم
[20/Oct/2026:14:23:15] ← التاريخ والوقت
"GET /products?id=1"   ← الطلب (Request)
200                    ← كود الاستجابة (Status Code)
5432                   ← حجم الاستجابة بالبايت

📊 HTTP Status Codes المهمة:
200 = OK (نجح)
301 = Redirect (تحويل)
403 = Forbidden (ممنوع)
404 = Not Found (ما لقى الصفحة)
500 = Server Error (خطأ بالسيرفر)
```

#### 📋 مثال 5: Firewall Log

```
Date=2026-10-20 Time=02:15:33 Action=DENY Protocol=TCP
SrcIP=203.0.113.50 SrcPort=44821 DstIP=10.0.0.5 DstPort=3389
Rule=Block-RDP-External

Date=2026-10-20 Time=02:15:34 Action=DENY Protocol=TCP
SrcIP=203.0.113.50 SrcPort=44822 DstIP=10.0.0.5 DstPort=22
Rule=Block-SSH-External

Date=2026-10-20 Time=02:15:35 Action=DENY Protocol=TCP
SrcIP=203.0.113.50 SrcPort=44823 DstIP=10.0.0.5 DstPort=445
Rule=Block-SMB-External

Date=2026-10-20 Time=02:15:36 Action=DENY Protocol=TCP
SrcIP=203.0.113.50 SrcPort=44824 DstIP=10.0.0.5 DstPort=1433
Rule=Block-MSSQL-External
```

```
💡 اشرح للطلاب:
• مهاجم خارجي (203.0.113.50) يسوي Port Scan
• يجرب منافذ حساسة: 3389 (RDP), 22 (SSH), 445 (SMB), 1433 (SQL Server)
• الفايروول حظر كل المحاولات (Action=DENY) ← الحماية تعمل

❓ سؤال: "لو كان Action=ALLOW بدل DENY، إيش المشكلة؟"
👉 الجواب: معناها المنافذ مفتوحة للخارج = خطر كبير!

📊 المنافذ المهمة التي يجب أن يعرفها محلل SOC:
Port 22    = SSH
Port 23    = Telnet (غير آمن)
Port 25    = SMTP (بريد)
Port 53    = DNS
Port 80    = HTTP
Port 443   = HTTPS
Port 445   = SMB (مشاركة ملفات Windows)
Port 1433  = MS SQL Server
Port 3306  = MySQL
Port 3389  = RDP (Remote Desktop)
Port 8080  = HTTP Proxy / Alt HTTP
```

#### 📋 مثال 6: DNS Log – نشاط مشبوه

```
20-Oct-2026 14:30:01 client 10.0.0.25 query: google.com IN A
20-Oct-2026 14:30:05 client 10.0.0.25 query: outlook.com IN A
20-Oct-2026 14:30:45 client 10.0.0.25 query: aGVsbG8gd29ybGQ.evil-domain.com IN A
20-Oct-2026 14:30:46 client 10.0.0.25 query: dGhpcyBpcyBhIHRlc3Q.evil-domain.com IN A
20-Oct-2026 14:30:47 client 10.0.0.25 query: c2VjcmV0IGRhdGE.evil-domain.com IN A
```

```
💡 اشرح للطلاب:
• أول طلبين عاديين: google.com, outlook.com
• الطلبات الثلاثة الأخيرة مشبوهة:
  → Subdomain طويلة وغريبة (نص مشفر Base64)
  → كلها تروح لـ evil-domain.com
  → هذا يسمى DNS Tunneling (تهريب بيانات عبر DNS)!

🔓 لو فكينا Base64:
  aGVsbG8gd29ybGQ = "hello world"
  dGhpcyBpcyBhIHRlc3Q = "this is a test"
  c2VjcmV0IGRhdGE = "secret data"

❓ سؤال: "ليش المهاجم يستخدم DNS لتهريب البيانات؟"
👉 الجواب: لأن DNS عادةً مسموح ومو مراقب بشكل دقيق
```

---

### 📌 الجزء 4: تمرين تفاعلي جماعي (15 دقيقة)

اعرض هذا الـ Log على الشاشة واطلب من الطلاب تحليله:

```
=== تمرين: حلل هذه الأحداث وأجب عن الأسئلة ===

[2026-10-20 01:00:05] Event ID: 4625 | User: admin | Source IP: 10.10.10.99 | Failure Reason: Bad Password
[2026-10-20 01:00:06] Event ID: 4625 | User: admin | Source IP: 10.10.10.99 | Failure Reason: Bad Password
[2026-10-20 01:00:07] Event ID: 4625 | User: admin | Source IP: 10.10.10.99 | Failure Reason: Bad Password
[2026-10-20 01:00:08] Event ID: 4625 | User: admin | Source IP: 10.10.10.99 | Failure Reason: Bad Password
[2026-10-20 01:00:09] Event ID: 4624 | User: admin | Source IP: 10.10.10.99 | Logon Type: 10
[2026-10-20 01:02:15] Event ID: 4720 | A user account was created: Account Name: backdoor01
[2026-10-20 01:02:30] Event ID: 4732 | Member added to Administrators group: backdoor01
[2026-10-20 01:05:00] Event ID: 4688 | Process Created: powershell.exe -enc SQBuAHYAbwBrAGUALQBXAGUAYgBS...
[2026-10-20 01:10:00] Event ID: 4634 | User: admin | Logoff

❓ الأسئلة:
1. ما نوع الهجوم في البداية؟
2. هل نجح المهاجم؟ كيف عرفت؟
3. ما هو Logon Type 10؟ ماذا يعني؟
4. ماذا فعل المهاجم بعد الدخول؟ (ما الأحداث المشبوهة؟)
5. ما مستوى خطورة هذا الحادث؟ (Low / Medium / High / Critical)
6. ما أول 3 إجراءات تتخذها كمحلل SOC؟
```

```
✅ الإجابات (لك فقط – لا تعرضها مباشرة):

1. Brute Force Attack (4 محاولات فاشلة متتالية بفارق ثانية)
2. نعم نجح → Event ID 4624 (تسجيل دخول ناجح)
3. Logon Type 10 = Remote Desktop (RDP) ← دخل عن بُعد
4. الأحداث المشبوهة بعد الدخول:
   - 4720: أنشأ حساب جديد اسمه "backdoor01" ← Persistence
   - 4732: أضاف الحساب لمجموعة Administrators ← Privilege Escalation
   - 4688: شغّل PowerShell مشفر ← ممكن Malware Download
5. Critical ← اختراق كامل + backdoor + privilege escalation
6. الإجراءات:
   - عزل الجهاز المصاب عن الشبكة فوراً
   - تعطيل حساب backdoor01
   - إعادة تعيين كلمة مرور admin
   - بدء تحقيق شامل (Incident Response)
```

### 📌 تكليف نهاية المحاضرة 1

```
📋 للأسبوع القادم (المحاضرة 2 – تثبيت اللاب):

1. تأكد أن جهازك يستوفي المتطلبات:
   ✅ RAM: 8GB كحد أدنى (16GB مُفضّل)
   ✅ مساحة فارغة: 50GB+
   ✅ المعالج يدعم Virtualization (VT-x أو AMD-V)

2. حمّل البرامج التالية (لا تثبتها – فقط حمّلها):
   ✅ VirtualBox: https://www.virtualbox.org/
   ✅ سأوفر لكم ملفات الـ VM في المحاضرة القادمة

3. فعّل Virtualization من BIOS/UEFI:
   ✅ ابحث في YouTube: "Enable Virtualization [اسم جهازك]"
```

---

## 🔧 الأسبوع 2: تثبيت بيئة المعمل (Lab Setup)

### 🕐 توزيع الوقت

| الوقت | المحتوى |
|-------|---------|
| 00:00 – 00:10 | مراجعة سريعة للأسبوع الماضي + التأكد من الاستعداد |
| 00:10 – 00:40 | تثبيت VirtualBox + استيراد VM |
| 00:40 – 01:10 | إعداد Splunk Free + إدخال بيانات أولية |
| 01:10 – 01:20 | استراحة |
| 01:20 – 01:50 | تثبيت أدوات إضافية (Wireshark, Suricata) |
| 01:50 – 02:00 | التأكد أن بيئة الجميع تعمل + تكليف |

### 🖥️ بيئة المعمل المطلوبة

```
📦 ما سيتم تثبيته:

Option A: بيئة مبسطة (الأسهل)
├── VirtualBox
├── Kali Linux VM (أو Ubuntu)
├── Splunk Free (داخل الـ VM)
├── Wireshark
└── Suricata

Option B: بيئة متكاملة (الأفضل لو الأجهزة قوية)
├── VirtualBox
├── Security Onion VM (يشمل ELK + Suricata + Zeek)
├── Windows 10 VM (كضحية)
└── Kali Linux VM (كمهاجم - اختياري)

💡 التوصية: ابدأ بـ Option A لأنها أخف على الأجهزة
```

### 📋 خطوات التثبيت

```
خطوة 1: تثبيت VirtualBox
→ Next → Next → Install → Finish

خطوة 2: استيراد الـ VM
→ File → Import Appliance → اختر ملف .ova → Import

خطوة 3: إعدادات الـ VM
→ RAM: 4GB minimum
→ CPU: 2 cores
→ Network: NAT أو Bridged

خطوة 4: تثبيت Splunk Free (داخل الـ VM)
→ حمّل من splunk.com (يحتاج تسجيل مجاني)
→ dpkg -i splunk.deb (لو Linux)
→ /opt/splunk/bin/splunk start --accept-license
→ الوصول عبر: http://localhost:8000

خطوة 5: اختبار أن كل شيء يعمل
→ افتح Splunk → ابحث عن: index=* | head 10
→ افتح Wireshark → capture على أي interface
```

---

## 🔬 الأسبوع 3: تحليل السجلات باستخدام SIEM (Splunk)

### 🕐 توزيع الوقت

| الوقت | المحتوى |
|-------|---------|
| 00:00 – 00:10 | مراجعة: ما هو SIEM وكيف يعمل |
| 00:10 – 00:30 | شرح واجهة Splunk + أساسيات SPL |
| 00:30 – 01:00 | لاب: إدخال بيانات + أول Queries |
| 01:00 – 01:10 | استراحة |
| 01:10 – 01:50 | لاب: سيناريو - اكتشاف Brute Force من Logs |
| 01:50 – 02:00 | مناقشة + تكليف |

### 📋 محتوى اللاب

```
🔍 أساسيات SPL (Search Processing Language):

# البحث الأساسي
index=main sourcetype=WinEventLog:Security EventCode=4625

# عدّ المحاولات الفاشلة لكل IP
index=main EventCode=4625 
| stats count by src_ip 
| sort -count

# عرض المحاولات بتسلسل زمني
index=main EventCode=4625 
| timechart count by src_ip

# البحث عن تسجيل دخول ناجح بعد محاولات فاشلة
index=main (EventCode=4624 OR EventCode=4625) 
| stats count(eval(EventCode=4625)) as failures, 
        count(eval(EventCode=4624)) as successes 
  by src_ip 
| where failures > 5 AND successes > 0
```

### 🎯 سيناريو اللاب
```
📋 السيناريو: شركة ABC Bank

وصلك تنبيه من SIEM: "عدد كبير من محاولات تسجيل الدخول الفاشلة"

المهام:
1. ابحث عن جميع الأحداث 4625 في آخر 24 ساعة
2. حدد أكثر 5 عناوين IP محاولةً
3. هل نجح أي منهم بالدخول؟ (ابحث 4624)
4. ما هي الحسابات المستهدفة؟
5. ما توصيتك؟

التسليم: لقطات شاشة من Splunk + إجابات مختصرة
```

---

## 🔬 الأسبوع 4: تحليل حركة الشبكة (Wireshark + PCAP)

### 🕐 توزيع الوقت

| الوقت | المحتوى |
|-------|---------|
| 00:00 – 00:10 | مراجعة: TCP/IP Basics + أهمية Network Analysis |
| 00:10 – 00:30 | شرح Wireshark: الواجهة، الفلاتر، Follow Stream |
| 00:30 – 01:00 | لاب 1: تحليل HTTP Traffic عادي |
| 01:00 – 01:10 | استراحة |
| 01:10 – 01:50 | لاب 2: تحليل PCAP مشبوه (C2 Communication) |
| 01:50 – 02:00 | مناقشة + تكليف |

### 📋 محتوى اللاب

```
🔍 Wireshark Display Filters المهمة:

# فلترة بـ IP
ip.addr == 192.168.1.100

# فلترة HTTP فقط
http

# فلترة DNS
dns

# فلترة TCP SYN (بداية اتصال)
tcp.flags.syn == 1 && tcp.flags.ack == 0

# فلترة بالمنفذ
tcp.port == 4444       ← منفذ شائع لـ Reverse Shell

# فلترة POST Requests (ممكن Data Exfil)
http.request.method == "POST"

# البحث عن نص معين
frame contains "password"
```

### 🎯 سيناريو اللاب
```
📋 ملف PCAP مشبوه (حمّل من malware-traffic-analysis.net)

المهام:
1. ما هي عناوين IP المتصلة في الـ capture؟
2. هل يوجد DNS queries لنطاقات مشبوهة؟
3. هل يوجد اتصال على منافذ غير عادية؟
4. استخدم Follow TCP Stream لقراءة محتوى اتصال مشبوه
5. هل يوجد ملفات تم تحميلها؟ (File → Export Objects → HTTP)
6. حدد IOCs (عناوين IP، نطاقات، ملفات)

التسليم: تقرير مختصر + IOCs + لقطات شاشة
```

---

## 🔬 الأسبوع 5: أنظمة كشف التطفل (IDS – Suricata)

### 🕐 توزيع الوقت

| الوقت | المحتوى |
|-------|---------|
| 00:00 – 00:15 | شرح: IDS vs IPS، كيف تعمل، Signature-based vs Anomaly-based |
| 00:15 – 00:40 | شرح Suricata Rules وبنيتها |
| 00:40 – 01:00 | لاب 1: تشغيل Suricata وقراءة Alerts |
| 01:00 – 01:10 | استراحة |
| 01:10 – 01:50 | لاب 2: كتابة Custom Rules |
| 01:50 – 02:00 | مناقشة + مراجعة للاختبار |

### 📋 محتوى اللاب

```
📖 بنية Suricata Rule:

action  protocol  src_ip  src_port  ->  dst_ip  dst_port  (options)

مثال:
alert tcp any any -> any 80 (msg:"Possible SQL Injection"; 
  content:"UNION"; nocase; content:"SELECT"; nocase; 
  sid:1000001; rev:1;)

التمارين:
1. اكتب Rule لاكتشاف Nmap SYN Scan
2. اكتب Rule لاكتشاف محاولة تحميل ملف .exe عبر HTTP
3. شغّل Suricata على ملف PCAP وراجع الـ Alerts
4. حلل Alert وحدد: True Positive أو False Positive
```

---

## 📝 الأسبوع 6: اختبار / مشروع منتصف الفصل (Midterm)

### الخيار A: اختبار عملي (الأسهل في التقييم)

```
📝 اختبار عملي – ساعتان

السيناريو: أنت محلل SOC في شركة XYZ. وصلك التالي:
- ملف Log يحتوي Windows Events
- ملف PCAP لحركة شبكة مشبوهة
- عدة Suricata Alerts

المطلوب (5 أسئلة):
Q1: [25%] حلل الـ Log وحدد نوع الهجوم + الأدلة
Q2: [25%] افتح الـ PCAP في Wireshark وأجب: ما IOCs؟
Q3: [20%] اكتب Suricata Rule لاكتشاف هذا الهجوم
Q4: [15%] ما التصنيف حسب MITRE ATT&CK؟
Q5: [15%] اكتب ملخص تنفيذي (Executive Summary) للحادثة

التسليم: ملف Word/PDF + لقطات شاشة
```

### الخيار B: مشروع مصغر (أفضل لقياس الفهم)

```
📋 مشروع منتصف الفصل (فردي أو ثنائي)

المطلوب: تحقيق كامل في حادثة أمنية
- يُعطى الطالب Dataset (BOTS أو مشابه)
- يجب تقديم: Timeline + IOCs + تقرير مختصر (2-3 صفحات)
- يُسلّم في نهاية المحاضرة أو خلال أسبوع (حسب الصعوبة)
```

---

## 🔬 الأسبوع 7: الاستجابة للحوادث الأمنية (Incident Response)

### 🕐 توزيع الوقت

| الوقت | المحتوى |
|-------|---------|
| 00:00 – 00:15 | شرح: NIST IR Lifecycle + Triage + Escalation |
| 00:15 – 00:35 | شرح: كيف تصنف Alert (True/False Positive) |
| 00:35 – 01:00 | لاب: سيناريو Phishing Email Analysis |
| 01:00 – 01:10 | استراحة |
| 01:10 – 01:50 | لاب: Tabletop Exercise – Ransomware Scenario |
| 01:50 – 02:00 | مناقشة + تكليف |

### 📋 محتوى اللاب

```
📧 لاب 1: تحليل Phishing Email

يُعطى الطالب بريد إلكتروني مشبوه:
- حلل Email Headers (من أين جاء فعلياً؟)
- افحص الرابط في VirusTotal / URLScan.io
- افحص المرفق (hash) في VirusTotal
- صنّف: Phishing أم لا؟
- وثّق IOCs
- ما الإجراء المناسب؟

أدوات: MXToolbox, VirusTotal, URLScan.io, CyberChef

💀 لاب 2: Tabletop Exercise – Ransomware

السيناريو (يُقرأ شفهياً ويُناقش جماعياً):
"الساعة 6 صباحاً، موظفون يبلغون أن ملفاتهم مشفرة.
رسالة فدية تطلب 5 Bitcoin. 50 جهاز متأثر.
السيرفر الرئيسي متأثر أيضاً."

أسئلة للنقاش الجماعي:
1. ما أول خطوة تسويها؟
2. هل تدفع الفدية؟ ليش / ليش لا؟
3. مين تبلّغ؟ (الإدارة، الجهات الحكومية؟)
4. كيف تحتوي الانتشار؟
5. كيف تتعافى؟
6. كيف تمنع تكراره؟
```

---

## 🔬 الأسبوع 8: التحقيق الرقمي وتحليل الذاكرة (Digital Forensics)

### 🕐 توزيع الوقت

| الوقت | المحتوى |
|-------|---------|
| 00:00 – 00:15 | شرح: ما هو Digital Forensics، Chain of Custody |
| 00:15 – 00:30 | شرح: أداة Volatility وأوامرها |
| 00:30 – 01:00 | لاب: تحليل Memory Dump |
| 01:00 – 01:10 | استراحة |
| 01:10 – 01:50 | لاب: اكتشاف Malware من الذاكرة |
| 01:50 – 02:00 | مناقشة + تكليف |

### 📋 محتوى اللاب

```bash
# أوامر Volatility الأساسية:

# تحديد نوع النظام
vol.py -f memory.dmp windows.info

# عرض العمليات
vol.py -f memory.dmp windows.pslist
vol.py -f memory.dmp windows.pstree

# عرض الاتصالات الشبكية
vol.py -f memory.dmp windows.netscan

# عرض أوامر CMD المنفذة
vol.py -f memory.dmp windows.cmdline

# البحث عن عمليات مخفية
vol.py -f memory.dmp windows.psscan

# استخراج ملفات
vol.py -f memory.dmp windows.dumpfiles --pid 1234
```

```
🎯 سيناريو اللاب:
"جهاز موظف مشتبه بإصابته. تم أخذ Memory Dump."

المهام:
1. حدد العمليات المشبوهة (اسم غريب، مسار غريب)
2. هل يوجد اتصالات شبكية غير عادية؟
3. هل يوجد عمليات مخفية؟
4. استخرج العملية المشبوهة واحسب Hash
5. افحص Hash على VirusTotal
6. وثّق النتائج

مصادر Memory Dumps للتدريب:
- MemLabs (GitHub)
- Volatility Foundation Samples
- CyberDefenders challenges
```

---

## 🔬 الأسبوع 9: تحليل البرمجيات الخبيثة (Basic Malware Analysis)

### 🕐 توزيع الوقت

| الوقت | المحتوى |
|-------|---------|
| 00:00 – 00:15 | شرح: Static vs Dynamic Analysis |
| 00:15 – 00:30 | شرح: الأدوات (PE Studio, strings, CyberChef, Any.Run) |
| 00:30 – 01:00 | لاب: Static Analysis لعينة |
| 01:00 – 01:10 | استراحة |
| 01:10 – 01:50 | لاب: Dynamic Analysis باستخدام Any.Run |
| 01:50 – 02:00 | مناقشة + تكليف |

### 📋 محتوى اللاب

```
⚠️ قواعد السلامة (اشرحها أول شيء):
1. لا تحلل Malware على جهازك الأساسي أبداً
2. استخدم VM معزولة أو Sandbox أونلاين
3. لا تشغّل Malware حقيقي – نستخدم عينات تعليمية آمنة

🔍 خطوات التحليل الثابت (Static):
1. حساب Hash: sha256sum sample.exe
2. فحص على VirusTotal
3. استخراج النصوص: strings sample.exe
4. تحليل PE Headers: PE Studio
5. فك تشفير Base64: CyberChef

🔍 التحليل الديناميكي (Dynamic) – باستخدام Any.Run:
1. ارفع العينة على Any.Run (أونلاين)
2. راقب: العمليات المُنشأة
3. راقب: الاتصالات الشبكية
4. راقب: التغييرات في الملفات
5. راقب: تعديلات Registry
6. استخرج IOCs
```

---

## 🔬 الأسبوع 10: Threat Intelligence + MITRE ATT&CK

### 🕐 توزيع الوقت

| الوقت | المحتوى |
|-------|---------|
| 00:00 – 00:15 | شرح: IOCs, TTPs, Pyramid of Pain |
| 00:15 – 00:30 | شرح: MITRE ATT&CK Framework + Navigator |
| 00:30 – 01:00 | لاب: تحقيق باستخدام Threat Intel |
| 01:00 – 01:10 | استراحة |
| 01:10 – 01:50 | لاب: ربط حادثة بـ MITRE ATT&CK |
| 01:50 – 02:00 | مناقشة + تكليف |

### 📋 محتوى اللاب

```
🎯 لاب 1: تحقيق باستخدام Threat Intel

يُعطى الطالب قائمة IOCs:
- 3 عناوين IP
- 2 Domain
- 2 File Hashes

المهام:
1. افحص كل IOC على: VirusTotal, AbuseIPDB, URLScan
2. هل يوجد ارتباط بمجموعة تهديد معروفة (APT)؟
3. ما هي الدولة المصدر؟
4. هل IOCs مرتبطة ببعض (نفس الحملة)؟

🎯 لاب 2: MITRE ATT&CK Mapping

بناءً على حادثة سابقة (من الأسابيع الماضية):
1. افتح ATT&CK Navigator
2. حدد Tactics و Techniques المستخدمة
3. حدد مجموعة التهديد الأقرب
4. ما Detection Rules التي تقترحها؟
```

---

## 🔬 الأسبوع 11: Threat Hunting + كتابة التقارير الأمنية

### 🕐 توزيع الوقت

| الوقت | المحتوى |
|-------|---------|
| 00:00 – 00:15 | شرح: Proactive vs Reactive، Hypothesis-driven Hunting |
| 00:15 – 00:35 | شرح: هيكل التقرير الأمني الاحترافي |
| 00:35 – 01:00 | لاب: Threat Hunting في Splunk |
| 01:00 – 01:10 | استراحة |
| 01:10 – 01:50 | لاب: كتابة تقرير حادثة كامل |
| 01:50 – 02:00 | توجيهات المشروع النهائي |

### 📋 محتوى اللاب

```
🎯 لاب 1: Threat Hunting

الفرضية: "يوجد PowerShell مشبوه يعمل في الشبكة"

Splunk Queries:
index=main source="WinEventLog:*" EventCode=4688 
  CommandLine="*powershell*" 
| where like(CommandLine, "%-enc%") OR like(CommandLine, "%-encoded%")
| table _time, Computer, User, CommandLine

المهام:
1. ابحث عن أوامر PowerShell مشفرة (Base64)
2. فك التشفير باستخدام CyberChef
3. حدد: هل هي مشبوهة أم عادية؟
4. وثّق النتائج

📝 لاب 2: كتابة تقرير حادثة

استخدم أي حادثة من اللابات السابقة واكتب تقرير يشمل:
1. ملخص تنفيذي (Executive Summary) – فقرة واحدة
2. جدول زمني (Timeline) – بالتواريخ
3. تحليل تقني (Technical Analysis) – IOCs + TTPs
4. التأثير (Impact) – ما تأثر
5. الإجراءات المتخذة (Actions Taken)
6. التوصيات (Recommendations)

التسليم: ملف PDF، 3-5 صفحات
```

---

## 📝 الأسبوع 12: المشروع / الاختبار النهائي (Final)

### الخيار A: مشروع نهائي شامل

```
📋 المشروع النهائي – Full SOC Investigation

يُعطى الطالب Dataset يحتوي:
- SIEM Logs (Windows Events)
- PCAP file (Network Traffic)
- Memory Dump (اختياري حسب الصعوبة)
- Suricata Alerts

هجوم متعدد المراحل:
1. Initial Access (Phishing → Malicious Document)
2. Execution (PowerShell Download)
3. Persistence (Scheduled Task)
4. Lateral Movement (PsExec)
5. Exfiltration (DNS Tunneling أو HTTP POST)

المطلوب:
✅ تحليل كامل للهجوم
✅ Timeline من البداية للنهاية
✅ قائمة IOCs
✅ تصنيف MITRE ATT&CK
✅ تقرير حادثة احترافي (5-7 صفحات)
✅ عرض تقديمي (5 دقائق) – اختياري

⏱️ المدة: ساعتان في المحاضرة + يمكن التسليم خلال يومين

📊 معايير التقييم (Rubric):
| المعيار                    | النسبة |
|---------------------------|--------|
| صحة التحليل الفني         | 30%    |
| اكتمال Timeline           | 15%    |
| IOCs صحيحة وشاملة         | 15%    |
| MITRE ATT&CK Mapping      | 10%    |
| جودة التقرير              | 20%    |
| التوصيات والإجراءات        | 10%    |
```

### الخيار B: اختبار عملي نهائي

```
📝 اختبار عملي شامل – ساعتان

5-6 أسئلة تغطي كل المحاور:
Q1: [20%] تحليل Logs (Windows + Linux)
Q2: [20%] تحليل PCAP في Wireshark
Q3: [15%] كتابة Suricata Rule
Q4: [15%] تحليل Memory Dump بـ Volatility
Q5: [15%] Threat Intel + MITRE ATT&CK
Q6: [15%] كتابة ملخص تنفيذي للحادثة
```

---

## 📊 نظام التقييم النهائي

| عنصر التقييم | النسبة | الأسبوع |
|-------------|--------|---------|
| الحضور والمشاركة | 10% | طوال الفصل |
| تسليم اللابات الأسبوعية | 30% | أسابيع 3-5, 7-11 |
| اختبار/مشروع منتصف الفصل | 25% | الأسبوع 6 |
| المشروع/الاختبار النهائي | 35% | الأسبوع 12 |
| **المجموع** | **100%** | |

---

## 🛠️ الأدوات المطلوبة (كلها مجانية)

| الأداة | الاستخدام | أسابيع الاستخدام |
|--------|----------|-----------------|
| VirtualBox | بيئة افتراضية | 2-12 |
| Splunk Free | SIEM وتحليل Logs | 3, 5, 6, 10, 11, 12 |
| Wireshark | تحليل Network Traffic | 4, 6, 12 |
| Suricata | IDS - كشف التطفل | 5, 6 |
| Volatility 3 | تحليل Memory | 8, 12 |
| CyberChef | فك تشفير وتحويل | 9, 11 |
| VirusTotal | فحص IOCs | 7, 9, 10 |
| Any.Run | تحليل Malware (Sandbox) | 9 |
| MITRE ATT&CK Navigator | تصنيف TTPs | 10, 12 |
| URLScan.io | فحص URLs | 7, 10 |
| AbuseIPDB | فحص IPs | 10 |

---

## 📋 ملخص: ماذا يُجهّز لكل محاضرة

| الأسبوع | سلايدات | ملفات لاب | أدوات | تقييم |
|---------|---------|-----------|-------|-------|
| 1 | ✅ سلايدات شرح + أمثلة Logs | ❌ | ❌ | - |
| 2 | ✅ خطوات التثبيت | ✅ ملفات VM (.ova) | VirtualBox, Splunk | - |
| 3 | ✅ مختصرة (SPL basics) | ✅ Dataset (Logs) | Splunk | تسليم |
| 4 | ✅ مختصرة (Filters) | ✅ PCAP files | Wireshark | تسليم |
| 5 | ✅ مختصرة (Rule syntax) | ✅ PCAP + Rules | Suricata | تسليم |
| 6 | ❌ | ✅ Dataset كامل | الكل | **اختبار** |
| 7 | ✅ مختصرة (IR lifecycle) | ✅ Phishing samples | VT, URLScan | تسليم |
| 8 | ✅ مختصرة (Vol commands) | ✅ Memory Dump | Volatility | تسليم |
| 9 | ✅ مختصرة (Analysis steps) | ✅ Malware samples | Any.Run, PE Studio | تسليم |
| 10 | ✅ مختصرة (ATT&CK) | ✅ IOCs list | VT, ATT&CK Nav | تسليم |
| 11 | ✅ مختصرة (Report template) | ✅ Hunt queries | Splunk, CyberChef | تسليم |
| 12 | ❌ | ✅ Dataset شامل | الكل | **نهائي** |

---

## 💡 نصائح أخيرة

```
✅ قبل كل محاضرة:
  - جرّب اللاب بنفسك بالكامل
  - جهّز Solution Key
  - حضّر خطة B لو الأداة ما اشتغلت

✅ أثناء المحاضرة:
  - ابدأ بقصة حقيقية أو خبر اختراق
  - امشِ بين الطلاب وساعدهم
  - شجع الأسئلة والنقاش

✅ بعد المحاضرة:
  - سجّل ملاحظاتك (ماذا نجح، ماذا يحتاج تحسين)
  - أعطِ feedback سريع على التسليمات
  - تواصل مع الدكتور النظري لمواءمة المحتوى
```

---

> **📌 ملاحظة**: هذه الخطة مرنة. عدّلها بناءً على مستوى الطلاب وتنسيقك مع الدكتور النظري.
