# sabq.org Google Indexing — تشخيص شامل
**التاريخ:** 2026-05-30
**الحالة:** الإصلاحات التقنية تمت، يحتاج إجراءات تشغيلية من أبو محمد

## المشكلة الأصلية
خبر "وسمية الكليب" نُشر في سبق منذ 32 دقيقة ولم يظهر في Google، بينما مواقع منافسة أصغر تظهر خلال 7 دقائق.

## التشخيص النهائي (من Agent خارجي + Live verification)

### السبب الجذري: **discovery + crawl-priority + trust**
- ليس مشكلة rendering
- ليس مشكلة on-page SEO (HTML كامل + meta + JSON-LD ممتازين)
- ليس مشكلة sitemap (موجود ويتحدّث)

### الأسباب الفرعية:
1. **Sitemaps غير مُسلّمة في Google Search Console** ⭐ الأهم
2. **صفر روابط داخلية قابلة للزحف** — homepage + /category/* + /local + /news ما فيها ولا رابط خبر واحد للـ Googlebot
3. **Crawl trust منخفض** — 3 ترحيلات hosting خلال 3 أسابيع
4. **1.64 مليون صفحة غير مفهرسة** (legacy junk + redirects + 404s)

## أوهام تم كشفها (مهم جداً)

### 1. Google Indexing API ما تدعم أخبار!
- API بس لـ JobPosting و BroadcastEvent
- لا تدعم NewsArticle
- كل الجهد في `GOOGLE_INDEXING_PRIVATE_KEY` كان **مضيعة وقت**
- لكن مهم نخليه لو سبق ينشر JobPosting لاحقاً

### 2. Google /ping?sitemap ميت من يونيو 2023
- كان no-op يعطي false confidence
- اتشال في commit e46b15e

### 3. robots.txt كان فيه `Googlebot-News: Disallow: /`
- يبلوك الصفحة الرئيسية والأقسام
- Google News ما يلقى من وين يجيب الأخبار!
- اتصلح

### 4. pages.dev و sabq.news كانوا duplicate content
- يكسروا الثقة عند Google
- الحين noindex لأي host ≠ sabq.org

## الإصلاحات التقنية المُطبّقة

| Commit | الإصلاح |
|---|---|
| `e46b15e` | إزالة pingGoogleSitemap الميت |
| `24c3f7a` | إزالة indexArticle (ما تدعم news) |
| (نفسه) | إصلاح robots.txt (إزالة Googlebot-News Disallow) |
| (نفسه) | حماية ضد duplicate content (pages.dev + sabq.news = noindex) |
| `699f904` | semantic HTML بروابط داخلية للـ crawlers (60 خبر للهوم، 40 للأقسام) |
| `c5c64b7` | حل ازدواج /opinion/ ↔ /article/ + englishSlug للرأي |
| `70a1a41` | (سابق) إصلاح CORS لتطبيق iOS (Capacitor WebView) |

### Commits اللي عملتها أنا في الجلسة:
- `70a1a41` — fix CORS for Capacitor (iOS app)
- `3525e86` — bulk re-indexing script (مع إن Google Indexing API لا تدعم news!)

## ما يلزم من أبو محمد (Operational Levers)

### الأولوية القصوى:
1. **Submit sitemaps في GSC**:
   - sitemap.xml
   - sitemap-news.xml
   - sitemap-articles-1.xml (وأمثالها)
2. **URL Inspection → Request Indexing** للأخبار المهمة (10 يومياً)
3. **Google News Publisher Center**: تأكد سبق مسجّل وما فيه تحذيرات
4. **توقف عن ترحيل hosting** — خلّي Google يستقر شهر على الأقل

### قبل ترحيل أي شي تاني:
- ⚠️ Cloudflare Pages migration is staged (EDGE_SEO=off)
- ⚠️ التشخيص يقول: stop migrating
- الترحيلات الثلاثة كسرت crawl trust

## معلومات سبق التقنية (للمرجع)

### Cache Strategy
- HTML: `private, no-store` (anti white-page)
- نتيجة: zero edge cache + كل Googlebot hit يضرب الـ origin
- **تعمد كسر crawl-rate** لمنع bugs بعد deploy

### الـ Architecture
- Frontend: Cloudflare Pages (migrated from Vercel recently)
- Backend: Railway
- API: api.sabq.org
- Frontend: sabq.org
- Mobile (iOS + Android): Capacitor WebView يفتح sabq.org/lite

### الـ SEO Workers
- `cloudflare-worker/frontend-edge-worker.js` — لسا يحقن SEO meta
- `functions/_middleware.js` — proxy + (مع EDGE_SEO=on) يحقن SEO
- حالياً: middleware proxy-only، الـ worker القديم لسا يحقن

### Active Files
- ✅ `edgeMeta.ts` — يولّد meta + semanticHtml (هذا اللي يشتغل)
- ❌ `seoInjector.ts` — dormant (مسار قديم في Replit)

### Counter-intuitive facts
- Sitemap URLs are englishSlug (مش Arabic) — clean canonicals
- 140k redirects claim كان غلط
- New articles **يفهرسون بسرعة لما تطلب Request Indexing يدوي**
- المشكلة في الـ batch discovery، مش في الـ priority

## التواريخ المهمة
- 2026-05-30 ~10:04 GMT: نشر خبر hciEyfA (وسمية الكليب)
- 2026-05-30 ~13:50 GMT: إصلاح GOOGLE_INDEXING_PRIVATE_KEY (لكن ما له فائدة لأن API ما تدعم news)
- 2026-05-30 ~15:15 GMT: استلام التشخيص الشامل من Agent خارجي

## الدرس المستفاد
- ❌ ما تثق في "feature flags" ظاهرها صحيح بدون verification (Google Indexing API)
- ❌ ما تثق في docs Google القديمة (/ping?sitemap)
- ✅ verify everything live with Googlebot user-agent
- ✅ GSC URL Inspection يكشف الحقيقة بسرعة
- ✅ الـ link graph أهم من on-page SEO

## كلمات مفتاحية للبحث المستقبلي
sabq seo, google indexing, sitemap submission, crawl trust, cloudflare pages migration, link graph, semantic html, edge meta injection, robots.txt googlebot-news, indexing api joppposting only
