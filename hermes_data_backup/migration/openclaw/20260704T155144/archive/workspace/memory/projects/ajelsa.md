# 🍷 ajelsa — صحيفة عاجل (Full-Stack)

## نظرة عامة
- **المالك:** أبو محمد (علي الحازمي)
- **الريبو:** https://github.com/sabq4org/ajelsa
- **النشر:** Vercel
- **المسار المحلي:** `~/Ajel`
- **تاريخ البدء:** 2026-05-01
- **تاريخ آخر تحديث كبير:** 2026-05-02

## التقنيات
- **Frontend:** Next.js 15 (App Router) + React 19 + Tailwind CSS
- **Backend:** Next.js API Routes + Drizzle ORM
- **Database:** Neon PostgreSQL (Serverless)
- **Editor:** TipTap (محرر الأخبار)
- **Auth:** JWT-based
- **Storage:** Cloudinary (الصور) + Cloudflare R2 (احتياطي)
- **Cache:** Upstash Redis (اختياري)

## خدمات الذكاء الاصطناعي
- **التحرير الذكي:** GPT-4o من OpenAI (`/api/ai/smart-edit`)
  - smart: عنوان + ملخص + كلمات مفتاحية + SEO + تصنيف
  - rewrite: إعادة صياغة احترافية
  - titles: 3 عناوين بديلة
- **توليد الصور:**
  - **رسومية:** DALL-E 3 (OpenAI) — أفضل نموذج للـ flat illustration
  - **واقعية:** Imagen 4 (Google) — الأفضل للصور الفوتوغرافية
- **endpoint:** `/api/ai/generate-image` يأخذ `style: "photorealistic" | "illustration"`

## لوحة التحكم (15+ ميزة مكتملة)
1. ✅ إدارة الأخبار (إنشاء/تعديل/حذف)
2. ✅ Mobile responsive layout
3. ✅ SEO Manager + Article Preview
4. ✅ Version History
5. ✅ Audit Log
6. ✅ Breaking News Desk
7. ✅ Workflow Kanban
8. ✅ Dark Mode
9. ✅ Scheduling Calendar
10. ✅ Ad Manager
11. ✅ RBAC (الأدوار والصلاحيات)
12. ✅ Polls (التصويت)
13. ✅ Newsletter
14. ✅ Drag & Drop Homepage Ordering
15. ✅ Smart Edit Bar (AI) فوق المحرر
16. ✅ AI Image Generator مع toggle (واقعية/رسومية)
17. ✅ نظام النشر المُتدرج (مميز / عادي / لا يظهر في الرئيسية)

## الواجهة العامة
- **الصفحة الرئيسية:** Hero (Lead + 4 Side) + Latest News + Most Read
- **صفحات الأقسام:** `/category/[slug]` ديناميكية
- **صفحات الكلمات المفتاحية:** `/keyword/[keyword]` للبحث
- **صفحة الخبر:** `/article/[slug]` مع SEO + كلمات مفتاحية قابلة للنقر + ليبل AI
- **الهيدر:** زخارف عنابية + التاريخ الهجري + مؤشر تاسي + Hover animations

## بنية النشر (3 مستويات)
| الوضع | الصفحة الرئيسية | داخل القسم |
|-------|----------------|------------|
| ⭐ مميز | Hero + Side | ✓ |
| 📰 عادي | Latest News | ✓ |
| 🚫 مخفي | ✗ | ✓ |

## التواريخ
- **الإدارة:** ميلادي + أرقام لاتينية (`src/lib/format.ts`)
- **الواجهة:** ميلادي + هجري في الهيدر (`Intl.DateTimeFormat("ar-SA-u-ca-islamic")`)

## الأداء
- **ISR:** revalidate 30s للرئيسية، 60s للأقسام والمقالات
- **Cloudinary CDN:** سرعة تحميل عالمية + ضغط تلقائي (auto:good)
- **Edge Caching:** Vercel Edge Network

## دروس تقنية مهمة
1. **Drizzle ORM + PostgreSQL enum:** يوجد bug في Vercel — الحل استخدام SQL خام عبر `db.execute(sql\`...\`)` بدلاً من Drizzle builder
2. **Vercel ISR limit:** الصفحة المخزنة لا تتجاوز 19 ميغابايت — استخدام Base64 للصور كارثة، الحل CDN خارجي
3. **Next.js 15 params:** أصبحت Promise — يجب `await params`
4. **Vercel filesystem:** read-only ما عدا `/tmp` — لا يمكن كتابة ملفات في `/var/task/public/`
5. **Force-dynamic vs ISR:** `force-dynamic` يقتل الأداء بسبب Neon cold starts — ISR أسرع 10×
6. **Gemini 3 Pro Image:** ضعيف في الـ illustration — DALL-E 3 أفضل
7. **عزل النماذج:** كل مهمة لها أفضل نموذج (Claude للنص الإعلامي، GPT-4o للتحرير الذكي، DALL-E للرسومات، Imagen للصور)

## ملاحظات أمنية
- جميع API Keys محفوظة في Vercel Environment Variables
- Cloudinary keys تم تجديدها في 2026-05-02 بعد ظهورها في محادثة (إجراء وقائي)
- لا توجد secrets في الكود المصدري

## ميزات قيد التطوير المحتملة
- 🔜 سكريبت لتحويل الصور القديمة (Base64 في DB) إلى Cloudinary
- 🔜 RSS Feed
- 🔜 Sitemap.xml ديناميكي
- 🔜 Push Notifications للأخبار العاجلة
- 🔜 Comments System
- 🔜 Reading Time Tracker
- 🔜 Related Articles AI

## معلومات الاتصال بالخدمات
- **Cloudinary Cloud:** dszjidciv (المفاتيح في Vercel فقط)
- **Database:** Neon (eu-central-1)
- **Domain:** ajelsa على Vercel (لم يُربط بدومين مخصص بعد)

## حالة المشروع
🟢 **منشور وشغّال** — صحيفة كاملة الميزات تعمل في الإنتاج
