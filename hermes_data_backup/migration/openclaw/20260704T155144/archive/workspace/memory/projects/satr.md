# 📰 سطر — الصحيفة الذكية المختصرة

## 🎯 الفكرة الأساسية

**صحيفة إلكترونية تقدم كل خبر في 3 أسطر فقط — لا أكثر.**

ليست مجرد اختصار، بل **ذكاء تحريري مكثف** يحوّل كل خبر إلى منتج تحريري كامل بحجم تغريدة:
- السطر 1: **الحدث** — ماذا حدث (الخبر)
- السطر 2: **السياق** — لماذا الآن، الخلفية
- السطر 3: **المعنى** — التأثير، ماذا يعني للقارئ

### مثال:
```
📌 أرامكو تخفض إنتاجها 500 ألف برميل يومياً
   الثالث منذ 2024، رد على ضعف الطلب الصيني
   النفط بيرتفع، السوق السعودي بيتأثر إيجاباً
```

---

## 🚦 حالة المشروع — 2026-05-05 (مساء) — Production Ready 🚀

### ✅ النسخة 0.2.0 "صحيفة حقيقية" — كاملة ومرفوعة

**القفزة الكبيرة (مايو 5، مساءً):**
- 🎴 **Stack View** (`/stack`) — تصفّح Tinder-style بـ Framer Motion (الميزة المميزة)
- 📰 **صفحة خبر مفردة** (`/article/[id]`) + OG meta كامل
- 📡 **LiveBar** — شريط عاجل يدوّر آخر 24 ساعة
- 🎯 **HeroBreaking** + قسم الترند (الأكثر قراءة)
- 📊 **Reading Progress** + **Floating ShareBar**
- 🔐 **Auth كامل** — password + signed JWT cookie + middleware
- ✏️ **Edit/Delete** عبر `/admin/edit/[id]` + ArticleEditor موحّد
- 🌐 **RSS** + **Sitemap** + **robots** + **404** + favicon SVG
- 📄 **/manifesto** + **/about** + **/tag/[name]**
- 🎨 لمسات بصرية (أرقام ١٢٣ للأسطر، quote-bar للسطر الثالث)
- ✅ **0 أخطاء TypeScript** | 21 مسار | ~5,500 سطر جديد
- **commit:** `9f90f98` على GitHub

---

### ✅ ما تم تنفيذه (MVP كامل ومرفوع)

**📂 المسار المحلي:** `~/Satr`
**🌐 GitHub:** https://github.com/sabq4org/satr
**🔗 يشتغل على:** http://localhost:3007 (`PORT=3007 npm run dev`)
**🗄️ قاعدة البيانات:** Neon (cloud) — متصل ومبذور بـ 10 أخبار

### Stack المنفذ:
- **Next.js 16** (Turbopack) + React 19 + TypeScript
- **Tailwind v4** + lucide-react + framer-motion
- **Drizzle ORM** + **Neon PostgreSQL**
- **OpenAI** (مع طبقة Mock للأوفلاين)
- **Total:** 1247 سطر كود في 15 ملف

### الميزات الجاهزة:
- ✅ **AI محلي 100% عبر Ollama** (qwen2.5-coder:14b/32b أو gemma4:26b)
- ✅ طبقة AI ثلاثية: ollama (محلي) → openai (سحابي) → mock (احتياطي)
- ✅ صفحة الموجز اليومي (Hero + featured + latest)
- ✅ 7 صفحات أقسام (محلي/عالمي/اقتصاد/رياضة/تقنية/ثقافة/منوعات)
- ✅ بطاقة خبر بـ 3 أسطر بنسق بصري واضح
- ✅ شارة عاجل + شارة ثقة المصدر (🟢🟡🔵)
- ✅ AI Deepen inline (وضّح أكثر) — يخزن في DB بعد أول توليد
- ✅ توقيت عربي نسبي ("قبل ساعة")
- ✅ لوحة تحرير `/admin` + جدول كامل بالأخبار
- ✅ محرر `/admin/new` بـ:
  - عدّاد كلمات حي لكل سطر
  - تحقق فوري لقاعدة (15-20 / 15-20 / 10-15)
  - زر "لخّص بالذكاء" من نص خام
  - معاينة لحظية
  - نشر/مسودة
- ✅ AI Mock يشتغل أوفلاين كامل (`USE_AI_MOCK=true`)

### الملفات الرئيسية:
```
~/Satr/
├── src/lib/db/schema.ts        # Drizzle schema (articles, users, savedArticles)
├── src/lib/ai/index.ts         # AI + Mock layer
├── src/lib/utils.ts            # arabicTimeAgo, CATEGORY_LABELS
├── src/app/page.tsx            # الموجز
├── src/app/admin/new/page.tsx  # المحرر الذكي
├── src/components/ArticleCard.tsx
├── src/components/Header.tsx
├── src/components/Logo.tsx
├── scripts/seed.ts             # 10 أخبار تجريبية
├── drizzle.config.ts           # يقرأ .env.local عبر dotenv
├── .env.local                  # Neon URL (مخفي عن git)
├── .env.example                # توثيق
└── README.md                   # دليل كامل
```

### Environment Variables (في `.env.local`):
```
# وضع محلي 100%
DATABASE_URL=postgres://alialhazmi@localhost:5432/satr
AI_ENGINE=ollama
OLLAMA_URL=http://localhost:11434
OLLAMA_MODEL=qwen2.5-coder:14b

# أو سحابي:
# DATABASE_URL=postgresql://neon...
# AI_ENGINE=openai
# OPENAI_API_KEY=sk-...
```

### نماذج Ollama المتوفرة على جهاز أبو محمد:
- `qwen2.5-coder:32b` (19 GB) — الأقوى
- `qwen2.5-coder:14b` (9 GB) — الأسرع والموصى به ✅
- `gemma4:26b` (17 GB)
- `gemma4:latest` (9.6 GB)
- `llama3:latest` (4.7 GB)

### أداء Ollama المختبر (qwen2.5-coder:14b):
- **تلخيص 3 أسطر:** ~3-5 ثوانٍ
- **AI Deepen:** ~9 ثوانٍ
- **جودة العربية:** ممتازة — تلخيص صحيح وهاشتاقات منطقية

### npm scripts المضافة:
- `npm run dev` — التشغيل (PORT=3007 موصى به)
- `npm run db:push` — تطبيق المخطط
- `npm run db:seed` — بذر 10 أخبار
- `npm run db:studio` — Drizzle Studio (واجهة DB)

---

## 📝 ما ينقص بعد الموجة الثانية (للجلسات القادمة)

### 🔴 الموجة 1 ✅ كاملة (2026-05-05 مساءً)
~~صفحة خبر مفردة، Auth، Edit/Delete، Stack View~~
~~RSS + Sitemap + OG + 404 + Tags + Manifesto~~

### 🟡 الموجة 2 — التميز (التالي)
5. رفع صور Cloudinary widget في المحرر
6. البحث الفعلي + صفحة `/search`
7. النشر على Vercel + Domain (satr.sa)
8. OG images ديناميكية (next/og)
9. مزامنة Like/Save فعلياً في DB

### 🟢 الموجة 3 — الإثارة
9. النشرة الصوتية الصباحية (TTS)
10. Newsletter (Resend) + Push notifications
11. AI Personalization
12. Premium subscription

### الأساسيات الناقصة الأخرى:
- مزامنة الإجراءات (حفظ/إعجاب) في DB — الأزرار client-only حالياً
- Loading states + skeleton
- 404/Error pages مخصصة
- `next/image` بدل `<img>`
- عدّاد مشاهدات فعلي (الحقل موجود لكن ما يزيد)
- Tests + ESLint strict
- Drafts auto-save

---

## 💡 توصيتي للمساء

أقترح **تنفيذ الموجة 1 كاملة** في جلسة واحدة (تقدير: 3-4 ساعات شغل):
1. صفحة خبر مفردة + Share buttons (WhatsApp + Twitter + رابط)
2. Auth بسيط (basic password protection)
3. صفحة تعديل + زر حذف
4. Stack View للموبايل (الميزة المميزة في الـ spec)

بعدها التطبيق يصير **production-ready** للنشر على Vercel.

---

## 🔧 لاستئناف العمل في المساء

```bash
# 1. تشغيل التطبيق
cd ~/Satr
PORT=3007 npm run dev

# 2. افتح المتصفح
# http://localhost:3007        — الموجز
# http://localhost:3007/admin  — لوحة التحرير

# 3. الذاكرة:
cat ~/.openclaw/workspace/memory/projects/satr.md
```

**كلمة السر للذاكرة:** الموجة 1 = صفحة خبر مفردة + Auth + تعديل/حذف + Stack View للموبايل.

---

## 📐 النموذج التحريري — "قاعدة الـ3" (مرجع ثابت)

كل خبر = **3 أسطر فقط، لا أكثر، لا أقل**.

1. **الحدث** (15-20 كلمة): ماذا، من، أين، متى
2. **السياق** (15-20 كلمة): لماذا الآن، خلفية، رابط بأحداث سابقة
3. **المعنى** (10-15 كلمة): التأثير، الدلالة، "ماذا يعني لي"

---

## 🎨 الهوية البصرية (مطبّقة)

- **الخط:** Tajawal
- **اللون الأساسي:** أزرق ليلي `#1a3a5e`
- **الخلفية:** كريم دافئ `#faf7f2`
- **العاجل:** أحمر `#c41e3a` مع نبض
- **اسم العلامة:** سطر — "الخبر زبدة"

---

## 🎯 الجمهور المستهدف

- **المهني المشغول** (25-50 سنة) — الجوهر في 30 ثانية بين الاجتماعات
- **الأم العاملة** — متابعة سريعة
- **الطالب الجامعي** — ثقافة عامة سريعة
- **كبار السن المتعلمون** — بدون تعقيد

---

## 🔑 القرارات النهائية

- ✅ سطر = صحيفة مستقلة (مو قسم في ajelsa)
- ✅ المحرر هجين (AI يقترح + بشري يراجع)
- ✅ Domain مقترح: satr.sa أو satr.app (لم يُسجل بعد)
- ✅ نموذج إيرادات مرحلي (مجاني → Premium → B2B)
