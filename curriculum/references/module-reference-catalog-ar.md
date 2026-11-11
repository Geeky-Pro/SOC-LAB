# فهرس مراجع الوحدات

> **الحالة:** مسودة — نقاط انطلاق منتقاة لإعداد الدروس؛ أعد التحقق من الصفحة والإصدار المناسبين عند إنتاج المواد التعليمية النهائية.  
> **تاريخ المراجعة:** 2026-11-10  
> **القاعدة:** المرجع نقطة بداية للبحث، وليس دليلاً على التحقق من إعداد مختبر بعينه أو إصدار برنامج معين. استشهد فقط بالصفحة أو الطبعة التي اطلعت عليها فعلياً لدعم الادعاء التعليمي.

## أسس مشتركة للبرنامج

- إطار الأمن السيبراني NIST (CSF) 2.0 — https://www.nist.gov/cyberframework
- NIST SP 800-61 الإصدار 3 (أبريل 2025) — https://csrc.nist.gov/pubs/sp/800/61/r3/final
- MITRE ATT&CK، البدء — https://attack.mitre.org/resources/
- مركز موارد إطار NIST NICE — https://www.nist.gov/itl/applied-cybersecurity/nice/nice-framework-resource-center

## الوحدة 01 — أساسيات SOC والعمليات الأمنية

الدروس ذات الصلة: L01-01 إلى L01-06.

- NIST CSF 2.0 — https://www.nist.gov/cyberframework
- إطار NIST NICE — https://www.nist.gov/itl/applied-cybersecurity/nice/nice-framework-resource-center
- NIST SP 800-61 الإصدار 3 — https://csrc.nist.gov/pubs/sp/800/61/r3/final
- البدء مع MITRE ATT&CK — https://attack.mitre.org/resources/

استخدم هذه المراجع لتأطير الوظائف الأمنية وقدرات القوى العاملة ومصطلحات الحوادث والعمليات المستندة إلى الأدلة. مستويات الخطورة التعليمية ليست سياسة عالمية موحدة.

## الوحدة 02 — معمارية مختبر SOC ونشره

الدروس ذات الصلة: L02-01 إلى L02-06.

- Broadcom: تثبيت VMware Workstation Pro — https://knowledge.broadcom.com/external/article/387947
- Broadcom: تنزيل وترخيص VMware Desktop Hypervisor — https://knowledge.broadcom.com/external/article/368667
- وثائق Netgate pfSense — https://docs.netgate.com/pfsense/en/latest/
- قائمة حزم Netgate (تشمل Suricata) — https://docs.netgate.com/pfsense/en/latest/packages/list.html
- وثائق Splunk Enterprise — https://help.splunk.com/en/splunk-enterprise
- درس Splunk Search — https://help.splunk.com/en/splunk-enterprise/search/search-tutorial/9.2/introduction/about-the-search-tutorial
- نظرة عامة على Microsoft Sysmon — https://learn.microsoft.com/en-us/windows/security/operating-system-security/sysmon/overview

تحقق من الإصدارات الدقيقة وشروط الترخيص وإجراءات التثبيت ودعم الحزم وطرق إعادة التوجيه والمنافذ والفهارس وأنواع المصادر والحقول مقابل البيئة المنشورة.

## الوحدة 03 — كشف تهديدات الأجهزة الطرفية والتحقيق فيها

الدروس ذات الصلة: L03-01 إلى L03-06.

- نظرة عامة على Microsoft Sysmon — https://learn.microsoft.com/en-us/windows/security/operating-system-security/sysmon/overview
- فهم أحداث Sysmon — https://learn.microsoft.com/en-us/windows/security/operating-system-security/sysmon/sysmon-events
- تمكين Sysmon وإعداده — https://learn.microsoft.com/en-us/windows/security/operating-system-security/sysmon/how-to-enable-sysmon
- سجل أحداث Windows — https://learn.microsoft.com/en-us/windows/win32/wes/windows-event-log
- درس Splunk Search — https://help.splunk.com/en/splunk-enterprise/search/search-tutorial/9.2/introduction/about-the-search-tutorial

يسجل Sysmon الملاحظات؛ لكنه لا يحدد وحده ما إذا كان النشاط ضاراً ولا يحظره.

## الوحدة 04 — التصيد والتحقيق في أمن البريد الإلكتروني

الدروس ذات الصلة: L04-01 إلى L04-06.

- RFC 5321 SMTP — https://www.rfc-editor.org/rfc/rfc5321
- RFC 5322 تنسيق رسائل الإنترنت — https://www.rfc-editor.org/rfc/rfc5322
- RFC 7208 SPF — https://www.rfc-editor.org/rfc/rfc7208
- RFC 6376 DKIM — https://www.rfc-editor.org/rfc/rfc6376 (راجع إحالات التحديث والتصويبات)
- RFC 9989 DMARC — https://www.rfc-editor.org/rfc/rfc9989 (صدر عام 2026؛ يحل محل RFC 7489)
- RFC 9990 تقارير DMARC المجمعة — https://www.rfc-editor.org/rfc/rfc9990
- RFC 9991 تقارير إخفاق DMARC — https://www.rfc-editor.org/rfc/rfc9991
- وثائق Mailpit — https://mailpit.axllent.org/docs/

استخدم مواصفة DMARC الحالية (RFC 9989) ومواصفات التقارير (RFC 9990/9991)، لا RFC 7489 المتقادمة. توضح RFC 9989 أن توافق SPF/DKIM يتحقق من تفويض النطاق، لكنه لا يضمن سلامة الرسالة. استخدم عناوين URL معطلة وعناصر بيانات وصفية لمرفقات خاملة أو منقحة. لا تطلب من المتعلمين فتح روابط مجهولة أو تشغيل مرفقات.

## الوحدة 05 — مراقبة أمن الشبكات وتحليلها

الدروس ذات الصلة: L05-01 إلى L05-06.

- دليل مستخدم Wireshark — https://www.wireshark.org/docs/wsug_html/
- مرشحات العرض في Wireshark — https://www.wireshark.org/docs/wsug_html_chunked/ChWorkDisplayFilterSection
- RFC 791 IPv4 — https://www.rfc-editor.org/rfc/rfc791
- RFC 9293 TCP — https://www.rfc-editor.org/rfc/rfc9293
- RFC 1035 DNS — https://www.rfc-editor.org/rfc/rfc1035
- RFC 9110 دلالات HTTP — https://www.rfc-editor.org/rfc/rfc9110

تحقق من حالة RFC وتحديثاتها أثناء إعداد الدروس. ميّز إمكانية رؤية الحزم عن إمكانية رؤية حمولة التطبيق، خصوصاً في الجلسات المشفرة.

## الوحدة 06 — كشف التسلل الشبكي ومنعه

الدروس ذات الصلة: L06-01 إلى L06-06.

- دليل مستخدم Suricata — https://docs.suricata.io/
- وثائق قواعد Suricata — https://docs.suricata.io/en/latest/rules/
- مخرجات EVE JSON في Suricata — https://docs.suricata.io/en/latest/output/eve/eve-json-output.html
- وثائق Netgate pfSense — https://docs.netgate.com/pfsense/en/latest/

تحقق من وثائق حزمة Suricata الحالية في pfSense ومن دعم وضع IPS/inline للإصدار والواجهة والمنصة المحددة. لا تستنتج قدرة المنع من قياس التنبيهات فقط.

## الوحدة 07 — مراقبة أمن الويب والتحقيق فيه

الدروس ذات الصلة: L07-01 إلى L07-06.

- RFC 9110 دلالات HTTP — https://www.rfc-editor.org/rfc/rfc9110
- OWASP Top 10:2025 — https://owasp.org/Top10/
- ورقة إرشادات التسجيل من OWASP — https://cheatsheetseries.owasp.org/cheatsheets/Logging_Cheat_Sheet.html
- درس Splunk Search — https://help.splunk.com/en/splunk-enterprise/search/search-tutorial/9.2/introduction/about-the-search-tutorial

توفر OWASP مفردات للتوعية والمخاطر، ولا تثبت نجاح طلب مشبوه.

## الوحدة 08 — الاستجابة للحوادث

الدروس ذات الصلة: L08-01 إلى L08-06.

- NIST SP 800-61 الإصدار 3 (2025) — https://csrc.nist.gov/pubs/sp/800/61/r3/final
- NIST CSF 2.0 — https://www.nist.gov/cyberframework
- مشروع الاستجابة للحوادث في NIST — https://csrc.nist.gov/projects/incident-response

يحل SP 800-61 الإصدار 3 محل الإصدار 2.

## الوحدة 09 — محاكاة الهجمات والتحقق من الكشف

الدروس ذات الصلة: L09-01 إلى L09-06.

- MITRE ATT&CK — https://attack.mitre.org/
- وثائق Atomic Red Team — https://www.atomicredteam.io/docs/atomic-red-team
- وثائق MITRE Caldera — https://caldera.readthedocs.io/en/stable/
- NIST SP 800-61 الإصدار 3 — https://csrc.nist.gov/pubs/sp/800/61/r3/final

اختر اختبارات منخفضة المخاطر فقط، مع تصريح صريح ومتطلبات مسبقة ونطاق وآثار جانبية متوقعة وتنظيف وتراجع.

## الوحدة 10 — التحقيق المتكامل في التهديدات: عملية Shadow Access

الدروس ذات الصلة: L10-01 إلى L10-07.

- أحداث Microsoft Sysmon — https://learn.microsoft.com/en-us/windows/security/operating-system-security/sysmon/sysmon-events
- دليل مستخدم Wireshark — https://www.wireshark.org/docs/wsug_html/
- دليل مستخدم Suricata — https://docs.suricata.io/
- RFC 5322 — https://www.rfc-editor.org/rfc/rfc5322
- درس Splunk Search — https://help.splunk.com/en/splunk-enterprise/search/search-tutorial/9.2/introduction/about-the-search-tutorial
- NIST SP 800-61 الإصدار 3 — https://csrc.nist.gov/pubs/sp/800/61/r3/final
- MITRE ATT&CK — https://attack.mitre.org/

حدد لكل عنصر ما إذا كان ملتقطاً أو اصطناعياً أو محاكياً أو مجموعاً في المختبر. يمكن أن يكون دليل البريد ملف `.eml` منقحاً؛ ويظل Mailpit اختيارياً.

## الوحدة 11 — المشروع الختامي لـ SOC

الدروس ذات الصلة: L11-01 إلى L11-05.

استخدم المراجع الخاصة بالوحدات أعلاه وفق مجالات الأدلة المسندة، إلى جانب NIST SP 800-61 الإصدار 3 وNIST CSF 2.0 وMITRE ATT&CK. أدرج المصادر الفعلية في حزمة كل سيناريو.

## صيانة المراجع

- تحقق من الطبعة أو المراجعة الحالية وتاريخ الوصول عند إعداد الدرس.
- فضّل هيئات المعايير والوثائق الأصلية للمورّد أو المشروع.
- اربط كل مصدر بموضوع الدرس أو الادعاء الذي يدعمه.
- لا تستخدم صفحات التسويق وحدها مصدراً للسلوك التقني.
- لا يعني هذا الفهرس التحقق من إصدارات المختبر أو إعداداته الخاصة.
