# المعمل 03: تحليل هجمات التصيد الاحتيالي - الجزء الثاني: التحقيق المتقدم في الترويسات والروابط (Phishing Analysis II)

> **المقرر:** عمليات الأمن السيبراني (مختبر الـ SOC - Cybersecurity Operations)  
> **المحاضر:** Hussein Al-Selwi  
> **إجمالي عدد الشرائح:** 15 شريحة  
> **العرض التقديمي المصدري:** `Lab3_Phishing_Analysis_2_AR.html`  

### 📋 نبذة عامة وأهداف الوحدة التدريبية
خطوات إجرائية وعملية للتحقيق الجنائي في رسائل البريد المشبوهة: المقارنة المعمقة بين الترويسات السليمة والمزيفة، تتبع قفزات خوادم النقل (Received Headers) من الخادم الأصلي في الأسفل وحتى الوصول، كشف تزييف العناوين، وتحييد الروابط الخبيثة عبر تقنية إبطال المفعول (Defanging).

---

## 📑 جدول المحتويات

- [الشريحة 01: المقدمة](#slide-01-المقدمة)
- [الشريحة 02: Recap & Objectives](#slide-02-recap-objectives)
- [الشريحة 03: تشريح هيكل الرابط (URL)](#slide-03-تشريح-هيكل-الرابط-url)
- [الشريحة 04: مسار عمل تحليل الروابط](#slide-04-مسار-عمل-تحليل-الروابط)
- [الشريحة 05: أدوات فحص وتحليل الروابط](#slide-05-أدوات-فحص-وتحليل-الروابط)
- [الشريحة 06: التحليل الثابت مقابل التحليل الديناميكي](#slide-06-التحليل-الثابت-مقابل-التحليل-الديناميكي)
- [الشريحة 07: التحليل الثابت (Static Analysis) Techniques](#slide-07-التحليل-الثابت-static-analysis-techniques)
- [الشريحة 08: التحليل الديناميكي (Dynamic Analysis) & Sandboxing](#slide-08-التحليل-الديناميكي-dynamic-analysis-sandboxing)
- [الشريحة 09: أدوات تحليل التصيد المؤتمتة](#slide-09-أدوات-تحليل-التصيد-المؤتمتة)
- [الشريحة 10: نظرة عامة على إجراءات الدفاع](#slide-10-نظرة-عامة-على-إجراءات-الدفاع)
- [الشريحة 11: الدفاع التفاعلي (Reactive Defense) Actions](#slide-11-الدفاع-التفاعلي-reactive-defense-actions)
- [الشريحة 12: الدفاع الاستباقي (Proactive Defense) Measures](#slide-12-الدفاع-الاستباقي-proactive-defense-measures)
- [الشريحة 13: Documentation & Reporting](#slide-13-documentation-reporting)
- [الشريحة 14: هيكل تقرير الحادثة الأمنية](#slide-14-هيكل-تقرير-الحادثة-الأمنية)
- [الشريحة 15: ملخص المنهجية الكاملة من البداية للنهاية](#slide-15-ملخص-المنهجية-الكاملة-من-البداية-للنهاية)

---

## الشريحة 01: المقدمة

> **التصنيف / الفئة:** `كشف التهديدات والاستجابة للحوادث · IDR`

### Phishing Analysis Part II

استكمال المنهجية — تشريح الروابط والمرفقات، واستخدام أدوات الفحص المؤتمتة، وإغلاق دائرة الاستجابة بالدفاع وإعداد التقارير.

المعمل 03 — الأدوات والدفاع وكتابة التقارير

> [!NOTE] 🎙️ **ملاحظات وتوجيهات المحاضر (Instructor Lecture Notes)**
> رحب بعودة الطلاب للجزء الثاني من معمل تحليل التصيد الاحتيالي (Phishing Analysis). غطى المعمل الثاني أساسيات البريد الإلكتروني، وتقنيات الهجوم، وخطوات تحليل الـ Header والمحتوى. تواصل هذه الجلسة المسار بتحليل الروابط (الروابط (URLs)) والمرفقات، والأدوات الآلية الداعمة، وإجراءات الدفاع، وإعداد التقارير الأمنية.

---

## الشريحة 02: Recap & Objectives

> **التصنيف / الفئة:** `نظرة عامة على المعمل`

### مراجعة وأهداف جلسة اليوم

استعرض المعمل 2 النصف الأول من منهجية تحليل التصيد. اليوم نستكمل العملية بالكامل — بدءاً من قاعدة عدم النقر على أي شيء، وصولاً للاستجابة الشاملة وإعداد التقارير.

Already Covered — Lab 2 التصنيف الأولي وفرز البلاغ (الفرز والتصنيف الأولي) فحص الـ Header والمرسل فحص نصوص ومحتوى الرسالة تحليل آليات المصادقة (سجل SPF (التحقق من خوادم الإرسال المصرحة) / توقيع DKIM التشفيري للرسائل / سياسة DMARC وتطبيق وضع الرفض (Reject)) Today — Lab 3 فحص الروابط (فحص الروابط بالأدوات) وأدواته فحص المرفقات — تحليل ثابت وديناميكي أدوات الفحص والتحليل المؤتمتة إجراءات الدفاع — التفاعلية والاستباقية التوثيق وكتابة التقارير الأمنية (Reporting)

> [!NOTE] 🎙️ **ملاحظات وتوجيهات المحاضر (Instructor Lecture Notes)**
> راجع سريعاً الخطوات الأربع الأولى من المنهجية التي تم تغطيتها في المعمل 2 (التصنيف الأولي، فحص الـ Header والمرسل، فحص المحتوى، وتحليل المصادقة سجل SPF (التحقق من خوادم الإرسال المصرحة)/توقيع DKIM التشفيري للرسائل/سياسة DMARC وتطبيق وضع الرفض (Reject))، ثم قدّم الخطوات المتبقية اليوم: فحص الروابط، فحص المرفقات، إجراءات الدفاع، والتوثيق وإعداد التقارير.

---

## الشريحة 03: تشريح هيكل الرابط (URL)

> **التصنيف / الفئة:** `FOUNDATIONS`

### تشريح هيكل الـ URL

قبل تحليل أي رابط مشبوه، يحتاج المحلل لمعرفة وتسمية كل جزء من أجزائه بدقة — فالمهاجمون يخفون حيلهم في أجزاء محددة من هذا الهيكل.

Hostname Path https:// academy. tcm-sec. com /courses/ example.php ?t=129 البروتوكول (Protocol) النطاق الفرعي (Subdomain) النطاق الأساسي (Domain) امتداد النطاق (TLD) المسار الفرعي (Path) File Parameter

قارن ذلك الآن برابط تصيد احتيالي حقيقي — نفس الهيكل، ولكن تم استغلال كل جزء فيه كسلاح:

Hostname — Spoofed Path http:// apple-login. dnsdyn. net /ODFTY/ index.php ?email=asimpson@example.com البروتوكول (Protocol) النطاق الفرعي (Subdomain) Real domain امتداد النطاق (TLD) المسار الفرعي (Path) File Victim's email

> [!WARNING]
> قراءة وفحص كل جزء: "apple-login" is just a subdomain label, not proof of Apple — the real domain is dnsdyn.net , a dynamic-DNS provider no legitimate company uses for login pages. "ODFTY" is a random, auto-generated subdirectory. And the highlighted parameter pre-fills the victim's own email into the fake login form, both to look more convincing and to let the attacker track exactly who clicked.

> [!NOTE] 🎙️ **ملاحظات وتوجيهات المحاضر (Instructor Lecture Notes)**
> قبل البدء بالتحليل، تأكد من قدرة الطلاب على تسمية كل جزء في الـ URL: البروتوكول، النطاق الفرعي (النطاق الفرعي (Subdomain))، النطاق الأساسي (النطاق الأساسي (Domain))، امتداد النطاق (امتداد النطاق (TLD))، المجلد الفرعي، الملف، والمعاملات (المعاملات (Parameters)). ثم اعرض رابط تصيد حقيقي ووضح كيف تم استغلال كل جزء.

---

## الشريحة 04: مسار عمل تحليل الروابط

> **التصنيف / الفئة:** `METHOD DEEP DIVE`

### مسار عمل المحلل في فحص الروابط (URL Analysis)

بعد فهم بنية الرابط، يتعامل المحلل مع الروابط المشبوهة عبر ثلاث مراحل منظمة — الاستخراج، الفحص، ثم الفحص بالأدوات:

1 1. الاستخراج (Extract) the URL استخراج كل رابط من ترويسة الرسالة ومحتواها. 2 Check for Red Flags البحث عن محاولات الانتحال — النطاقات الشبيهة (Typosquatting) وسوء استخدام الـ Subdomains. الحذر من خدمات تقصير الروابط (bit.ly وغيرها) التي تخفي الوجهة الحقيقية. الانتباه لتقنيات التشفير والترميز (Hex, URL Encoding, IP formats) لإخفاء الرابط. 3 3. الفحص بالأدوات (Scan) With Tools Submit the URL in its original form — scanning tools need the real link, not a defanged one Cross-reference results to reach a verdict

> [!WARNING]
> قاعدة ذهبية: إياك أن تفتح أو تزور رابطاً مشبوهاً من متصفحك مباشرة! Always use an isolated analysis VM, a dedicated sandbox tool, or a URL-scanning service.

> [!NOTE] 🎙️ **ملاحظات وتوجيهات المحاضر (Instructor Lecture Notes)**
> شرح متعمق للخطوة 4 من المنهجية. استعرض مسار العمل عبر مراحله الثلاث: أولاً استخراج كافة الروابط من الـ Header والمحتوى، ثانياً فحص كل رابط للبحث عن الانتحال أو الروابط المختصرة أو التشفير، وأخيراً الفحص بالأدوات المتخصصة قبل إصدار الحكم النهائي.

---

## الشريحة 05: أدوات فحص وتحليل الروابط

> **التصنيف / الفئة:** `TOOLING`

### أدوات فحص وتحليل الروابط المشبوهة

تتيح هذه الخدمات للمحلل فحص الروابط بأمان تام دون تشغيلها أو فتحها على جهازه الشخصي:

- **URL2PNG** `[SCREENSHOT]`: التقاط صورة شاشة آمنة لصفحة الهبوط دون تشغيلها محلياً — نظرة أولى سريعة وآمنة لمعاينة شكل الصفحة.
- **urlscan.io** `[FULL SCAN]`: تحميل الصفحة في بيئة معزولة، والتقاط هيكل الـ DOM الكامل، وكل الاتصالات الشبكية، وسلسلة التحويلات (Redirects).
- **VirusTotal** `[REPUTATION]`: فحص الرابط عبر أكثر من 70 محرك مكافحة فيروسات وقوائم حظر في وقت واحد لتحديد درجة الخطورة.
- **PhishTank** `[PHISHING DB]`: قاعدة بيانات مجتمعية توثق مواقع التصيد المؤكدة — للتحقق مما إذا كان الرابط قد أُبلغ عنه مسبقاً.

> [!IMPORTANT]
> نصيحة للمحلل: A "clean" result from one tool is not proof of safety — brand-new malicious domains are often not yet indexed anywhere. Cross-reference at least two independent sources before clearing a URL.

> [!NOTE] 🎙️ **ملاحظات وتوجيهات المحاضر (Instructor Lecture Notes)**
> قدّم الأدوات الأربع الأساسية لفحص الروابط المشبوهة: URL2PNG لأخذ لقطة شاشة آمنة دون فتح الصفحة محلياً، urlscan.io للفحص التقني العميق للـ DOM والشبكة، VirusTotal لفحص السمعة عبر عشرات المحركات، و PhishTank للتحقق من قواعد بيانات التصيد المجتمعية.

---

## الشريحة 06: التحليل الثابت مقابل التحليل الديناميكي

> **التصنيف / الفئة:** `METHOD DEEP DIVE`

### تحليل المرفقات — التحليل الثابت مقابل الديناميكي

Once an attachment is securely extracted, hash it and search that hash's reputation first — a known-bad hit alone can be enough for a verdict. From there, an analyst has two complementary approaches to dig deeper.

التحليل الثابت (Static Analysis) Examines the file without running it Safe, fast, and repeatable at scale PDF: pdfid / pdf-parser to pull out embedded الروابط (URLs) and objects Office doc: oledump to find and extract macros التحليل الديناميكي (Dynamic Analysis) Executes the file in an isolated sandbox Reveals real runtime behavior and intent Process, file system, registry, network activity Slower, and some malware detects and evades sandboxes

> [!IMPORTANT]
> Scope note: Full malware analysis process is outside this course. The goal here is triage — pull out embedded الروابط (URLs), objects, and macros to confirm intent, or hand the file to a sandbox and read its report.

> [!NOTE] 🎙️ **ملاحظات وتوجيهات المحاضر (Instructor Lecture Notes)**
> Deep-dive into methodology step 5, attachment examination. 1. الاستخراج (Extract) the attachment, hash it, and search that hash's reputation first. From there: static analysis (format-specific tools, no execution) versus dynamic analysis (detonating in a sandbox to observe behavior). Note that full malware reverse engineering is out of scope for this course — the goal is triage.

---

## الشريحة 07: التحليل الثابت (Static Analysis) Techniques

> **التصنيف / الفئة:** `STATIC ANALYSIS`

Start every file the same way — hash it and search that hash's reputation. If it comes back unknown, the next tools depend on the file type.

> [!IMPORTANT]
> Hash & Search: Compute the file's MD5 / SHA-1 / SHA-256 and search it on VirusTotal and other reputation sources — the fastest check, and often enough to reach a verdict on its own.

PDF Files 1 pdfid Quick triage count of risky keywords — JavaScript, embedded files, launch actions 2 pdf-parser Digs into the flagged objects to pull out embedded الروابط (URLs) and payloads Office Documents 1 oledump 2. الفحص البصري (Inspect)s the OLE structure of Word/Excel files to detect embedded VBA macros 2 1. الاستخراج (Extract) & Review Pull out the macro code and read it without ever letting it run

> [!WARNING]
> Scope note: The goal is triage, not full reverse engineering — extract the indicator (a URL, an object, a macro), then decide whether it's worth escalating to a sandbox.

> [!NOTE] 🎙️ **ملاحظات وتوجيهات المحاضر (Instructor Lecture Notes)**
> Cover the practical static triage workflow: hash the file and search reputation databases first for every file type. Then split by format — pdfid and pdf-parser for malicious PDFs (triage keywords, then extract embedded الروابط (URLs)/objects), and oledump plus manual extraction for Office documents (detect and pull VBA macros). Emphasize this is triage, not full reverse engineering, which is out of scope for this course.

---

## الشريحة 08: التحليل الديناميكي (Dynamic Analysis) & Sandboxing

> **التصنيف / الفئة:** `DYNAMIC ANALYSIS`

The file is detonated inside an isolated, monitored environment — an analyst watches what it actually does, rather than guessing from its code alone.

- **Process Behavior**: Which child processes spawn, what commands run, and whether the sample tries to inject into or hollow out other processes.
- **File System & Registry Changes**: New or modified files, dropped payloads, and registry keys added for persistence across reboots.
- **Network Traffic**: Command-and-control callbacks, DNS requests, and any second-stage payload downloads captured with full packet detail.
- **Sandbox-Evasion Checks**: Some malware detects it's being watched — checking for a mouse, a real user, or specific VM artifacts — and stays dormant to avoid analysis.

- **Any.Run** `[SANDBOX]`: Interactive, browser-based sandbox with live process, network, and screen visibility during detonation.
- **Joe Sandbox** `[SANDBOX]`: Deep behavioral reports covering process trees, network activity, and MITRE ATT&CK technique mapping.
- **Hybrid Analysis / Cuckoo** `[SANDBOX]`: Free and open-source options for automated detonation with detailed behavioral reports.

> [!NOTE] 🎙️ **ملاحظات وتوجيهات المحاضر (Instructor Lecture Notes)**
> Explain dynamic analysis: detonating the file in an isolated sandbox and observing what it actually does — process creation, file system and registry changes, and network traffic. Mention that this is essential when static analysis is inconclusive, e.g. against packed or obfuscated malware.

---

## الشريحة 09: أدوات تحليل التصيد المؤتمتة

> **التصنيف / الفئة:** `TOOLING`

### منصات وأدوات التحليل المؤتمتة والشاملة

Manual analysis doesn't scale to hundreds of reported emails a day — these two tools automate the repetitive parts of the process.

- **eioc.py** `[SCRIPT]`: Parses a raw email file and extracts every IOC in one pass — sender and reply-to addresses, الروابط (URLs), IPs, and attachment hashes — turning what would be several manual steps into a single command.
- **PhishTool** `[WEBSITE]`: A web-based triage platform — upload the email and it pulls header, URL, and attachment analysis into one case, with a verdict and case management built in.

> [!IMPORTANT]
> نصيحة للمحلل: Automation accelerates triage but doesn't replace judgment — a tool's verdict is one input into the analyst's own conclusion, not a substitute for it.

> [!NOTE] 🎙️ **ملاحظات وتوجيهات المحاضر (Instructor Lecture Notes)**
> Introduce the two main automated tools used in this course: eioc.py, a script that extracts every IOC from an email in one pass, and PhishTool, a web-based platform that runs a full triage workflow on an uploaded email.

---

## الشريحة 10: نظرة عامة على إجراءات الدفاع

> **التصنيف / الفئة:** `METHOD DEEP DIVE`

### إجراءات الدفاع — التفاعلية مقابل الاستباقية

Once a phishing email is confirmed malicious, the response splits into two tracks: contain what already happened, and reduce the chance it happens again.

الدفاع التفاعلي (Reactive Defense) Taken after a confirmed threat is found Focused on containment and eradication Time-sensitive — every minute counts e.g. blocking, quarantining, resetting credentials الدفاع الاستباقي (Proactive Defense) Put in place before an attack occurs Focused on reducing likelihood and blast radius Ongoing, not tied to a single incident e.g. سياسة DMARC وتطبيق وضع الرفض (Reject) enforcement, training, threat intel

> [!IMPORTANT]
> نصيحة للمحلل: A mature security program treats every reactive response as an input to the proactive program — each incident should improve the defenses that prevent the next one.

> [!NOTE] 🎙️ **ملاحظات وتوجيهات المحاضر (Instructor Lecture Notes)**
> Deep-dive into methodology step 6, defense measures. Introduce the two categories: reactive defense, taken after a phishing email has already been identified in the environment, and proactive defense, put in place ahead of time to reduce the likelihood and impact of future attacks.

---

## الشريحة 11: الدفاع التفاعلي (Reactive Defense) Actions

> **التصنيف / الفئة:** `REACTIVE DEFENSE`

### مراحل الدفاع التفاعلي عند اكتشاف الحادثة

بمجرد تأكيد هجوم التصيد، تتحرك الاستجابة عبر خمس مراحل متتالية — من وقف الانتشار وحتى تدريب المستخدمين:

1 1. الاحتواء (Containment) تحديد نطاق الحادثة والأجهزة المتأثرة حجر الرسائل وسحبها فوراً حظر مؤشرات المرسل (Sender Artifacts) حظر مؤشرات الروابط (Web Artifacts) حظر مؤشرات الملفات (File Hashes) 2 2. الاستئصال (Eradication) Remove malicious emails البحث الموسع في البريد عبر eDiscovery حذف كافة الملفات المترسبة في الأجهزة تقديم بلاغات إساءة الاستخدام لمزودي الخدمة تغيير فوري لكلمات المرور وتصفير الجلسات إعادة تهيئة الأجهزة المصابة إن لزم الأمر 3 3. التعافي (Recovery) استعادة الأنظمة والخدمات للعمل الطبيعي وتأكيد سلامتها 4 4. التواصل (Communication) إشعار المستخدمين المتأثرين وتوجيههم إحاطة الإدارة وفرق العمل المعنية بمجريات الحادثة 5 5. التوعية (Education) تقديم تدريب توعوي فوري مخصص للمستخدم المستهدف لمنع التكرار

> [!NOTE] 🎙️ **ملاحظات وتوجيهات المحاضر (Instructor Lecture Notes)**
> Cover the five phases of reactive phishing defense: containment (determine scope, quarantine, block sender/web/file artifacts), eradication (remove malicious emails and files, including content search and eDiscovery, plus abuse form submissions, credential changes, and reimaging), recovery (restore systems), communication (notify affected users, update stakeholders), and user education (end-user training).

---

## الشريحة 12: الدفاع الاستباقي (Proactive Defense) Measures

> **التصنيف / الفئة:** `PROACTIVE DEFENSE`

### تدابير الدفاع الاستباقي لحماية المؤسسة

ضوابط دفاعية دائمة تُدار باستمرار عبر خمس طبقات متكاملة لتقليل احتمالية وتأثير هجمات التصيد القادمة:

1 1. تصفية البريد (Filtering) بوابات أمن البريد المتطورة (SEG) وضع علامة تنبيهية على الرسائل الخارجية 2 URL 3. الفحص بالأدوات (Scan)ning & Blocking فحص الروابط في الوقت الفعلي عند النقر حظر النطاقات حديثة التسجيل (NRDs) تلقائياً 3 3. تصفية المرفقات حظر الامتدادات الخطرة (.exe, .iso, .scr, .vbs) فحص المرفقات في بيئة Sandbox قبل التسليم 4 Email 4. المصادقة (Auth) Methods سجل SPF (التحقق من خوادم الإرسال المصرحة) توقيع DKIM التشفيري للرسائل سياسة DMARC وتطبيق وضع الرفض (Reject) 5 5. تدريب المستخدمين برامج التوعية الأمنية المستمرة تجارب محاكاة تصيد دورية وعملية توفير زر إبلاغ سريع عن الإيميلات المشبوهة

> [!IMPORTANT]
> نصيحة للمحلل: No single layer is enough on its own — these five work together, so a phish that slips past filtering can still be stopped by authentication checks, sandboxing, or a trained user reporting it.

> [!NOTE] 🎙️ **ملاحظات وتوجيهات المحاضر (Instructor Lecture Notes)**
> غطّ الأركان الخمسة للدفاع الاستباقي: تصفية البريد (بوابات الحماية وتمييز الرسائل الخارجية)، فحص وحظر الروابط (الفحص اللحظي وحظر النطاقات الجديدة)، تصفية المرفقات (حظر الامتدادات الخطرة)، مصادقة البريد (سجل SPF (التحقق من خوادم الإرسال المصرحة), توقيع DKIM التشفيري للرسائل, سياسة DMARC وتطبيق وضع الرفض (Reject))، وتدريب المستخدمين (محاكاة التصيد وزر الإبلاغ عن الرسائل المشبوهة).

---

## الشريحة 13: Documentation & Reporting

> **التصنيف / الفئة:** `METHOD DEEP DIVE`

### التوثيق وكتابة التقارير الأمنية (Reporting)

لا تُغلق أي حادثة أمنية حتى يتم توثيقها رسمياً — التقرير يحول الاستجابة الفردية إلى معرفة مؤسسية يستفيد منها الفريق بأكمله:

- **الذاكرة المؤسسية (Institutional Memory)**: قد يتعامل محلل آخر مع هجوم مماثل غداً. التقرير الممتاز يمكّنه من التعرف على الهجوم وربطه فوراً.
- **Compliance & Accountability**: جهات التدقيق، شركات التأمين السيبراني، والهيئات التنظيمية تتطلب إثباتات رسمية لما تم اكتشافه وكيف تم التعامل معه.
- **Metrics & Trends**: تراكم التقارير يوضح الإدارات الأكثر استهدافاً، ويقيس مدى فاعلية برامج التدريب والتوعية.
- **Handoff & Escalation**: يتيح التقرير الواضح تسليم الحادثة لفرق أخرى (مثل الـ IR أو الهندسة) أو للإدارة دون الحاجة لإعادة الشرح الشفهي.
- **Justify the Response**: نصيحة ذهبية: لا تكتفِ بسرد ما فعلته فقط — بل اشرح "لماذا" فعلته. وضّح المنطق الأمني وراء كل قرار، ليفهم كل من يقرأ التقرير أسباب الإجراء وليس نتيجته فقط.

> [!IMPORTANT]
> نصيحة للمحلل: Write for a reader who knows nothing about this incident — spell out acronyms, give a clear timeline, and don't rely on memory only you have.

> [!NOTE] 🎙️ **ملاحظات وتوجيهات المحاضر (Instructor Lecture Notes)**
> شرح متعمق للخطوة الأخيرة من المنهجية: التوثيق وإعداد التقارير. اشرح لماذا يعد التوثيق أمراً جوهرياً حتى بعد احتواء التهديد: الذاكرة المؤسسية، الامتثال والتدقيق، قياس مؤشرات الأداء، وتسليم المهام بين الفرق، مع تبرير سبب اتخاذ كل إجراء أمني.

---

## الشريحة 14: هيكل تقرير الحادثة الأمنية

> **التصنيف / الفئة:** `REPORT TEMPLATE`

### الهيكل النموذجي لتقرير حادثة التصيد

التنسيق المنظم والموحد يجعل قراءة التقرير سريعة تحت ضغط العمل، ويسهل مقارنته بالحوادث السابقة:

1 الوصف العام (Description) ملخص بلغة واضحة ومباشرة لما يحتويه الإيميل وسبب الاشتباه به. 2 الترويسات (Headers) التاريخ، الموضوع، المرسل، المرسل إليه، مسار الرد، عنوان IP للمرسل، ومعرف الرسالة. 3 الروابط (URLs) حصر وتوثيق كل رابط تم استخراجه من ترويسة ومحتوى الرسالة. 4 المرفقات (Attachments) اسم كل مرفق، وقيم الهاش التشفيرية له (MD5, SHA1, SHA256). 5 تحليل المؤشرات (Artifact Analysis) نتائج الفحص التفصيلية لكل من: فحص المرسل، فحص الروابط، وفحص المرفقات. 6 الحكم والتصنيف (Verdict) التصنيف النهائي القاطع للحادثة — خبيث (Malicious)، مشبوه (Suspicious)، أو سليم (Benign). 7 إجراءات الدفاع المتخذة (Actions Taken) توثيق كافة الخطوات والإجراءات التفاعلية التي تم تنفيذها لاحتواء التهديد.

> [!WARNING]
> أفضل الممارسات (Defanging): Defang every URL and IP written into the report — hxxp[://]evil[.]com , 1.2.3[.]4 — so nothing in the document is clickable or gets auto-parsed as a live indicator by whoever reads it next.

> [!NOTE] 🎙️ **ملاحظات وتوجيهات المحاضر (Instructor Lecture Notes)**
> استعرض قالب تقرير الحادثة الذي سيعبئه الطلاب: الترويسات، الروابط، المرفقات، الوصف العام، تحليل المؤشرات (المرسل، الرابط، المرفق)، الحكم النهائي، وإجراءات الدفاع. أكد على أفضل ممارسة: إلغاء فاعلية الروابط وعناوين IP (Defanging) في التقرير لحمايته من النقر العرضي.

---

## الشريحة 15: ملخص المنهجية الكاملة من البداية للنهاية

> **التصنيف / الفئة:** `WRAP-UP`

### المنهجية الشاملة لتحليل التصيد من البداية للنهاية

سبع خطوات محكمة في مسار عملي واحد — من لحظة وصول إيميل مشبوه وحتى إغلاق وتوثيق القضية بالكامل:

- **التصنيف الأولي وفرز البلاغ (الفرز والتصنيف الأولي)** `[STEP 1]`: STEP 1
- **فحص الـ Header والمرسل** `[STEP 2]`: STEP 2
- **فحص نصوص ومحتوى الرسالة** `[STEP 3]`: STEP 3
- **فحص الروابط بالأدوات** `[STEP 4]`: STEP 4
- **فحص المرفقات (ثابت وديناميكي)** `[STEP 5]`: STEP 5
- **Defense Measures** `[STEP 6]`: STEP 6
- **التوثيق وكتابة التقارير الأمنية (Reporting)** `[STEP 7]`: STEP 7

> [!IMPORTANT]
> الآن أصبحت تمتلك المنهجية الاحترافية المتكاملة لمحلل الـ SOC. The hands-on exercise will apply all seven steps to a real suspicious email — from first glance to a fully documented, defensible report.

> [!NOTE] 🎙️ **ملاحظات وتوجيهات المحاضر (Instructor Lecture Notes)**
> اختم المعمل بمراجعة المنهجية الكاملة المكونة من 7 خطوات من البداية للنهاية، والتي جمعت المعملين 2 و 3، لترسيخ كيفية ترابط كل مرحلة في عملية احترافية قابلة للتكرار في بيئة الـ SOC الحقيقية.

---

## 🎯 الخلاصة ومخرجات التعلم

- **الوحدة التدريبية:** المعمل 03: تحليل هجمات التصيد الاحتيالي - الجزء الثاني: التحقيق المتقدم في الترويسات والروابط (Phishing Analysis II)

- **المهارات المكتسبة:** فهم عملي وتطبيقي عميق لكيفية الكشف، التحقيق، الاستجابة، وإدارة التهديدات الأمنية باحترافية داخل بيئة العمليات.

- **مرجع التدريب:** مختبر عمليات الأمن السيبراني العملي — إعداد وتقديم: **Hussein Al-Selwi**.
