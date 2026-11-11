# بيئة SOC-LAB

> الحالة: خط أساس معماري مسودة؛ لم يُنشر أو يُتحقق منه عملياً.

## خط أساس التصميم

- مختبر افتراضي معزول واحد لكل طالب على VMware Workstation.
- Splunk Enterprise فقط؛ ولا يعتمد على Splunk Enterprise Security.
- يوفر pfSense التوجيه والتقسيم؛ وتُثبت Suricata داخل pfSense.
- مصدر قياس الأجهزة الطرفية هو Windows 10/11 مع Sysmon.
- يستضيف Ubuntu Server عبء عمل الويب في DMZ.
- يوجد Kali Linux على الشبكة `10.0.90.0/24`.
- Mailpit اختياري لتمارين البريد المحلية.

## خريطة الوثائق

- `architecture/topology.md` — مناطق الثقة والبنية المنطقية
- `network/addressing-plan.md` — توزيع IPv4 ومتطلبات VMnet
- `network/traffic-flows-and-firewall-policy.md` — تدفقات أقل صلاحية
- `virtual-machines/inventory.md` — أدوار الآلات الافتراضية والبرامج
- `virtual-machines/resource-planning.md` — تخطيط السعة
- `deployment/deployment-guide.md` — التثبيت المرحلي
- `deployment/telemetry-pipeline.md` — تصميم انتقال المصدر إلى SIEM
- `validation/validation-checklist.md` — اختبارات القبول
- `validation/reset-and-recovery.md` — التراجع وإعادة البناء

## مناطق الثقة المقترحة

| المنطقة | الشبكة الفرعية | الغرض |
|---|---|---|
| الإدارة | `10.0.10.0/24` | إدارة مضبوطة |
| SOC | `10.0.30.0/24` | Splunk Enterprise ومجمّعات البيانات |
| DMZ | `10.0.20.0/24` | عبء عمل ويب Ubuntu |
| الأجهزة الطرفية | `10.0.40.0/24` | Windows وSysmon |
| Kali | `10.0.90.0/24` | محاكاة مصرح بها |

هذه نطاقات داخلية مقترحة للمختبر. تحقق من عدم تداخلها مع شبكة LAN أو VPN أو Docker أو VMware لدى كل طالب قبل النشر.

## السلامة والحالة

لا تربط آلات توليد الهجمات بشبكات فعلية أو إنتاجية. استخدم حسابات اصطناعية ولقطات وأهدافاً محددة وأدلة منقحة. لا تودع بيانات اعتماد أو ملفات ترخيص أو مفاتيح خاصة أو بيانات طلاب أو صور آلات افتراضية.

كل الإجراءات مسودات إلى أن تنفذ على مضيف مرجعي نظيف وتدعمها أدلة تحقق. راجع `curriculum/lab-dependency-map-ar.md` لتبعيات الوحدات.
