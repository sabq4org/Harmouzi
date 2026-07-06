# 🌸 يومي — تطبيق المواعيد الشخصي

## الفكرة
صفحة تسجيل مواعيد يومية بطريقة **مبتكرة** — اليوم يُعرض كـ **منظر طبيعي** (Horizon Timeline) بدل الجدول التقليدي.

## المسارات
- **النسخة الأصلية:** `~/.openclaw/workspace/projects/yawmi/index.html`
- **النسخة في Home:** `~/yawmi/index.html`

## الفلسفة البصرية
- **اسم اللوحة الفنية:** "Sunrise Dunes"
- **الألوان:** pastel ناعمة
  - خوخي (#fce4d6)
  - خزامى (#e8e0f3)
  - نعناعي (#d9ebe0)
  - سماوي (#d6e8f5)
  - كريم (#faf6f0)
- **الإحساس:** فجر سعودي هادئ

## المكونات
1. **Greeting Header** — السلام عليكم + اسم المستخدم بتدرج ذهبي/طيني
2. **4 Stats Cards:**
   - 🌅 اليوم (عدد المواعيد + القادم بعد X)
   - ⏳ الأسبوع
   - ✨ وقت حر
   - 🎯 هدف الإنجاز
3. **Horizon Timeline** — أهم ابتكار:
   - SVG curved line يمثل اليوم (6ص → 10م)
   - مواعيد بطاقات تطفو على الأفق
   - "الآن" يضيء بنبضة دافئة
   - علامات وقت أسفل الأفق
4. **Day Schedule List** — قائمة بطاقات أنيقة + Quick Add
5. **Mood of the Day** — مؤشر شعوري
6. **Categories** — 4 فئات (عمل، اجتماعات، شخصي، صحة)
7. **FAB** — زر عائم يدور عند hover

## التقنيات
- HTML/CSS/JS standalone
- localStorage للحفظ
- Glassmorphism (`backdrop-filter: blur`)
- Ambient blobs متحركة
- Grain texture (SVG noise filter)
- Quick Add يفهم لغة طبيعية بسيطة (يستخرج الوقت)

## تقييم أبو محمد
> "جميل جداً" ✅

## فرص التطوير
- [ ] عرض أسبوعي بنفس النمط
- [ ] مزامنة مع Google Calendar
- [ ] اقتراحات AI لأفضل وقت لمهمة
- [ ] تذكيرات push notifications
