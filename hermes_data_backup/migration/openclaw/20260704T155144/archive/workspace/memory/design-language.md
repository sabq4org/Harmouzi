# 🎨 لغة التصميم — قاعدة بصرية لكل أعمالنا

## الفلسفة العامة (مهمة جداً)

أبو محمد لا يحب:
- الألوان الصاخبة والثقيلة
- التصاميم المزدحمة
- خطوط ديكورية في الواجهات الصحفية
- صور كرتونية أو emojis كبدائل للصور
- أي شيء "صبياني" أو "غير ناضج"

أبو محمد يحب:
- الهدوء البصري
- التايبوغرافي القوي
- المساحات البيضاء (تنفس)
- اللون يستخدم بحكمة وقياس
- الحس التحريري الراقي (نيويورك تايمز عربية)

## القاعدة الذهبية

> **اللون يخدم المحتوى، والمحتوى يخدم القارئ.**
> أي شيء يصرخ "أنا تصميم!" غلط. التصميم الناجح يختفي.

---

## 🍷 لوحة الألوان "Burgundy" (الأنجح لأبو محمد)

```
الخلفيات:
--bg:        #fbf7f4   كريم دافئ (الخلفية الرئيسية)
--bg-2:      #f5efe9   كريم أعمق (للأقسام الفرعية)
--paper:     #ffffff   أبيض (للبطاقات)
--paper-2:   #faf5f1   شبه أبيض

البورجوندي (لون الهوية):
--burgundy:       #8c1d2b   الأساسي (CTAs، التأكيدات، الـ accents)
--burgundy-dark:  #6b1421   هوفر، تدرجات
--burgundy-soft:  #b53d4a   تأكيد ثانوي
--rose:           #d8a5aa   روز ناعم
--rose-soft:      #f0d4d6   روز فاتح
--cream-rose:     #fce8e9   كريم وردي (للخلفيات اللينة)

الحبر (النصوص):
--ink:        #1f1a1c    حبر أساسي (لا أسود قاسي)
--ink-2:      #4a3f43    حبر متوسط
--ink-soft:   #7a6d72    حبر هادئ (للوصف)
--ink-faint:  #b3a8ac    حبر خافت (للtimes والـ meta)

الخطوط الفاصلة:
--line:       #ede4dd
--line-soft:  #f3ebe3

ألوان مساعدة (نادرة الاستخدام):
--gold:  #b8924a   ذهبي (للـ luxury accents)
--sage:  #7a9081   مرمري (للقطاعات الإيجابية)
--navy:  #3a4a5e   كحلي (للقطاعات الجادة)
```

## 🌸 لوحة الألوان "Sunrise Dunes" (للتطبيقات الشخصية)

```
خلفيات pastel:
--cream:    #faf6f0
--peach:    #fce4d6
--rose:     #f5d6d6
--lavender: #e8e0f3
--mint:     #d9ebe0
--sky:      #d6e8f5
--sand:     #f0e6d2
--warmth:   #ffd9b8

نصوص:
--ink:       #3a3338
--ink-soft:  #6e6770
--ink-faint: #a89fa6

accents:
--gold:  #c9a96e
--terra: #c97b6e   (نسخة دافئة من البورجوندي)
--sage:  #8aa893
```

---

## ✍️ التايبوغرافي

### القاعدة المقدّسة:
**خط واحد رئيسي = Tajawal**
- لا تستخدم Reem Kufi (ديكوري — للشعارات فقط)
- لا تستخدم خطوط متعددة في صفحة واحدة

### الاستخدام:
- **Tajawal** — كل النصوص (headings + body + UI)
- **Amiri** — حالات خاصة فقط:
  - الشعار الرسمي للجريدة
  - الأرقام العربية الكبيرة (١، ٢، ٣) في القوائم
  - الاقتباسات الصحفية

### الأحجام والأوزان:
```
H1 رئيسي:     32-36px / 800
H2 قسم:       22-26px / 700-800
H3 بطاقة:     16-20px / 700
Body:         14px / 400-500
Meta/Caption: 11-12px / 400
KPIs:         32-36px / 700 (font-feature: tnum)
```

### المسافات:
- letter-spacing: -0.3px للعناوين (للتقارب)
- line-height: 1.7 للنصوص (للراحة)
- line-height: 1.3-1.4 للعناوين

---

## 🎴 البطاقات والحدود

### القاعدة:
- بطاقات بيضاء (`--paper`) على خلفية كريم
- حدود ناعمة (`1px solid var(--line)`)
- زوايا مدورة (`border-radius: 14-16px`)
- shadows خفيفة جداً (لا shadows ثقيلة)

```css
.card {
  background: var(--paper);
  border: 1px solid var(--line);
  border-radius: 16px;
  padding: 22px;
}

/* Hover */
.card:hover {
  transform: translateY(-2px);
  box-shadow: 0 12px 32px rgba(31, 26, 28, 0.08);
}

/* Shadows القياسية */
--shadow-1: 0 1px 2px rgba(31, 26, 28, 0.04), 0 4px 12px rgba(31, 26, 28, 0.04);
--shadow-2: 0 2px 4px rgba(31, 26, 28, 0.06), 0 12px 32px rgba(31, 26, 28, 0.08);
--shadow-red: 0 8px 24px rgba(140, 29, 43, 0.12);
```

---

## 🎨 العناصر التفاعلية

### الأزرار:
- **Primary:** بورجوندي + abyad + shadow أحمر خفيف
- **Secondary:** أبيض + حدود + ink soft
- **Hover:** translateY(-1 to -2px) + shadow أعمق

### الـ Pills والـ Tags:
- خلفية كريمية فاتحة (`--cream-rose`)
- نص بورجوندي
- padding صغير (4px 12px)
- border-radius كامل

### Live Indicators:
- نقطة بورجوندي 6px
- animation pulse (نبضة كل 1.5-2 ثواني)

---

## 🖼️ الصور والإيقونات

### القاعدة الذهبية (للمشاريع الصحفية):
**استخدم صور حقيقية. لا تستخدم emojis كبدائل عن الصور.**

### للتجارب والـ Prototypes:
- استخدم placeholders بسيطة (لون موحد + نص "صورة")
- إذا لازم gradient → استخدم gradient من نفس لوحة الألوان
- لا تخلط ألوان كثيرة في صورة واحدة

### الإيقونات:
- SVG line icons (stroke-width: 2)
- بسيطة وموحّدة
- بحجم 14-18px في الـ UI
- emojis مسموحة في الـ UI الداخلي (lights، badges)
- emojis ممنوعة في المحتوى الصحفي الجاد

---

## 📐 المسافات والـ Layout

### القاعدة:
**مساحة بيضاء = ذكاء بصري**

```css
/* الأقسام الكبيرة */
.section { padding: 32-40px 0; }

/* المحتوى الرئيسي */
.wrap { max-width: 1280-1320px; padding: 0 24-32px; }

/* الـ gap بين العناصر */
gap: 16px (مكثف)
gap: 24px (افتراضي)
gap: 32-40px (متباعد)
```

### الـ Grid:
- استخدم `auto-fit` للـ responsive
- minmax للحد الأدنى
- تجنب الـ grid المعقد المتداخل

---

## ✨ الـ Animations

### القاعدة:
**نعومة + هدف. لا حركة بدون سبب.**

```css
/* Standard transitions */
transition: all 0.2s ease;          /* تفاعل سريع */
transition: all 0.3s ease;          /* hover */
transition: transform 0.6s ease;    /* صور */

/* Cubic bezier للحركات الجميلة */
cubic-bezier(0.34, 1.56, 0.64, 1)   /* للأزرار والـ FAB */
```

### الـ Animations المسموحة:
- **Pulse** للـ live indicators
- **Hover lift** (translateY -2px)
- **Scale** (1.04-1.05) للصور عند hover
- **Subtle glow** لعناصر الـ "now"

### الـ Animations الممنوعة:
- حركات سريعة جداً
- bounce excessive
- shake
- flicker

---

## 🔤 اللغة العربية والـ RTL

### الأساسيات:
- `<html lang="ar" dir="rtl">`
- استخدم `right` و `left` بحذر مع RTL
- الأرقام: `tnum` feature للجداول المنظمة
- font-feature-settings: "tnum"

### الاحترام:
- اكتب الكلمات الكاملة (لا اختصارات)
- "قبل ساعة" بدل "قبل 1 ساعة"
- "الأكثر قراءة" بدل "Most Read"
- المصطلحات التقنية مسموحة لما لا يوجد بديل

---

## 🎯 الأنماط الناجحة

### للداشبوردات (نقطة قوتي):
1. KPIs Row في الأعلى (4 بطاقات بيضاء)
2. Charts كبيرة + Sidebar للقوائم
3. Activity feeds + Leaderboards
4. Heatmaps للوقت
5. Donut charts للنسب

### للتطبيقات الشخصية:
1. Greeting شخصي في الأعلى
2. Stats Cards صغيرة
3. عرض رئيسي مبتكر (مثل Horizon)
4. قوائم منظمة + Quick Add
5. FAB في الزاوية

---

## ⚠️ الدروس المستفادة

### من محاولة واجهة الصحيفة:
- ❌ Reem Kufi غلط للواجهات الصحفية
- ❌ Gradients ملونة لكل قسم = فوضى
- ❌ Emoji كصور رئيسية = طفولي
- ❌ الهيدر بفلسفة SaaS غلط للصحف
- ✅ خط واحد + ألوان قليلة + صور حقيقية

### نقاط قوتي (التزم بها):
- داشبوردات وبيانات
- لوحات تحكم تحريرية
- Stats + KPIs
- تنظيم بصري للأرقام

### نقاط ضعفي (تجنبها أو استعن بمصمم):
- الواجهات الصحفية الإبداعية
- صور editorial حقيقية
- الـ art direction الصحفي

---

## 🛠️ الأدوات التقنية

```html
<!-- Fonts -->
<link href="https://fonts.googleapis.com/css2?family=Tajawal:wght@200;300;400;500;700;800;900&family=Amiri:wght@400;700&display=swap" rel="stylesheet">

<!-- Reset -->
* { margin: 0; padding: 0; box-sizing: border-box; }

<!-- Body -->
font-family: 'Tajawal', -apple-system, sans-serif;
color: var(--ink);
background: var(--bg);
line-height: 1.7;
```

### Grain Texture (subtle paper feel):
```html
body::before {
  content: '';
  position: fixed;
  inset: 0;
  background-image: url("data:image/svg+xml;utf8,<svg ...><filter id='n'><feTurbulence baseFrequency='0.85'.../><feColorMatrix values='0 0 0 0 0 ... 0.025 0'/></filter>...");
  pointer-events: none;
  z-index: 0;
  opacity: 0.7;
}
```

---

## 📁 الأمثلة المرجعية

- **لوحة عاجل (نجاح):** `~/.openclaw/workspace/projects/ajel-dashboard/index.html`
- **يومي (نجاح):** `~/.openclaw/workspace/projects/yawmi/index.html`
- **واجهة عاجل (تعلم):** `~/.openclaw/workspace/projects/ajel-news/index.html`

---

## القاعدة الأخيرة

> **في الشك، اختار الأقل.**
> لون أقل، خطوط أقل، عناصر أقل، حركات أقل.
> الفخامة في الهدوء.
