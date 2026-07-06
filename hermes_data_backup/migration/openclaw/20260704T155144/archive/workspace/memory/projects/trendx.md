# 📊 TRENDX — منصة البيانات والاستطلاعات

## نظرة عامة
- **النوع:** تطبيق iOS (SwiftUI)
- **المسار:** `/Users/alialhazmi/TRENDX`
- **الحالة:** تحت التطوير + مرفوع على App Store Connect (Internal builds 8-16)
- **Bundle ID:** `mizan.TRENDX`
- **Simulator:** iPhone 17 — `id=F55A4145-9D93-42A0-BCA9-48830C71DBDF`

## الفكرة الأساسية
منصة سعودية موثوقة متخصصة في الاستطلاعات والاستبيانات وتحليل البيانات لدعم اتخاذ القرار. شعار: **#في_كل_اتجاه** (نجمع.. نحصر.. نقيس.. نحلل)

## Stack التقني
- **Framework:** SwiftUI + Swift
- **State:** AppStore (ObservableObject)
- **Storage:** UserDefaults (local)
- **Theme:** TrendXTheme.swift

## لوحة الألوان (الحالية)
```
Primary:    #3B5BDB  (أزرق Mantine)
Accent:     #FA7C12  (برتقالي)
Background: #F4F5FA  (رمادي فاتح)
Surface:    #FFFFFF
Ink:        #1A1B25
```

## هيكل الملفات
```
TRENDX/
├── Models/
│   ├── Models.swift          # كل الـ models + Poll/Survey samples
│   └── SurveySamples.swift   # استبيانات 4 و 5 (techSamples)
├── Screens/
│   ├── HomeScreen.swift
│   ├── PollsScreen.swift         # استطلاعات + استبيانات + مركز الذكاء
│   ├── PollDetailView.swift      # تفاصيل الاستطلاع + زر إحصائيات
│   ├── PollAnalyticsView.swift   # لوحة إحصائيات الاستطلاع (7 أقسام)
│   ├── SurveyDetailView.swift    # تفاصيل الاستبيان + أسئلته
│   ├── SurveyAnalyticsView.swift # التحليل الشامل للاستبيان (7 tabs)
│   ├── CategoryInsightView.swift # مركز الذكاء القطاعي
│   ├── AccountScreen.swift
│   ├── GiftsScreen.swift
│   └── CreatePollSheet.swift
├── Stores/
│   ├── AppStore.swift        # State management
│   └── TrendXAI.swift        # AI copy + insights engine
├── Components/
│   └── SharedComponents.swift
└── Theme/
    └── TrendXTheme.swift
```

## الميزات المبنية

### استطلاعات (Polls)
- بطاقة خبر بتصميم احترافي
- تصويت مع تحديث فوري للنسب
- Stack View (تصفح Tinder-style)
- نظام نقاط ومكافآت

### PollAnalyticsView — 7 أقسام
1. **الأداء العام** — معدل التحويل، مستوى الثقة، مرات الظهور، البنشمارك القطاعي
2. **الديموغرافيا** — جنس + عمر + توزيع جغرافي بنسب صحيحة
3. **سلوك التصويت** — ساعات الذروة + وقت القرار + موبايل/ويب + درجة الانقسام
4. **الانتشار والتأثير** — مشاركات + حفظ + إعادة نشر + زيارات + متابعون
5. **تحليل TRENDX AI** — قراءة ذكية + بنشمارك + جودة العيّنة
6. **أثر المجتمع** — نقاط + مساهمون + معدل العودة
7. **منحنى الزمن** — تراكم الأصوات يومياً

### استبيانات (Surveys) — 5 في قطاع التقنية/AI
1. الذكاء الاصطناعي في حياتنا اليومية (5 أسئلة، 500 مشارك)
2. ثقة المجتمع بتقنيات AI في اتخاذ القرار (4 أسئلة، 500 مشارك)
3. ذكاء اصطناعي في التعليم: تحوّل أم تهديد؟ (4 أسئلة، 420 مشارك)
4. الخصوصية الرقمية في عصر الذكاء الاصطناعي (4 أسئلة، 500 مشارك)
5. مستقبل العمل في ظل انتشار الذكاء الاصطناعي (5 أسئلة، 480 مشارك)

### SurveyAnalyticsView — 7 Tabs
1. **الملخص** — معدل الإكمال الدائري + 4 KPIs + قائمة الأسئلة
2. **المشاركون** — المشارك النموذجي + جنس + عمر + جغرافيا
3. **الإجماع** — خريطة التوافق/الانقسام لكل سؤال
4. **الروابط** — Cross-analysis بين الأسئلة + حسب الجنس والمنطقة
5. **الشخصيات** — 3 أنماط مجيبين مكتشفة بـ AI + donut chart
6. **الزمن** — منحنى الرأي 14 يوم + تطور الموقف
7. **الاكتشافات** — 5 نقاط AI + توصيات + أزرار تصدير

### CategoryInsightView — مركز الذكاء القطاعي
- مقياس التوجه العام (Sentiment Gauge دائري)
- مؤشرات: ثقة بـ AI / قلق وظيفي / قبول التنظيم / حماية البيانات
- مقارنة الاستبيانات الخمسة مع معدل إكمال لكل واحد
- أعلى 4 أسئلة توافقاً عبر كل الاستبيانات
- أعلى 3 أسئلة انقساماً في القطاع
- إحصائية الأجهزة: iOS 57% / Android 30% / iPad 8% / Web 5%
- 6 اكتشافات AI قطاعية + 4 توصيات استراتيجية
- روابط مباشرة لكل استبيان

### إحصائية الأجهزة
موجودة في: SurveyAnalytics.deviceBreakdown + CategoryInsightView
- iPhone/iOS, Android, iPad, Web/Desktop

## الأهداف الاستراتيجية للمشروع
1. تسهيل التعرف على توجهات الرأي العام وسلوكياتهم
2. تكوين قاعدة بيانات ضخمة موثوقة ومتنامية
3. مساعدة المؤسسات على الوصول لعيناتهم بشكل أسرع
4. بناء مجتمع بمكافآت وShare Revenue

## ما يجعل الشركات تدفع (USPs)
- **Cross Analysis:** ربط الخيارات بالجنس/المنطقة/الجهاز
- **بصمة المشارك النموذجي:** "ذكر 25-34 من الرياض يجيب مساءً من iOS"
- **بنشمارك القطاع:** "استطلاعك أعلى من 87% من المشابهة"
- **هامش الخطأ الإحصائي:** ±3.2% — يعطي مصداقية علمية
- **مركز الذكاء القطاعي:** تقرير شامل لكل استبيانات القطاع

## Git Log
- `8ad22b6` — feat: 5 tech surveys + CategoryInsightView + device analytics
- `fc0e3f2` — feat: PollAnalyticsView + Mantine colors + polls fix

## ملاحظات التطوير
- امسح UserDefaults عند تغيير samples: `xcrun simctl uninstall ... && reinstall`
- App Store Connect: Internal builds موجودة (8-16) — جاهز للنشر
- RTL: كل الشاشات الجديدة فيها `.environment(\.layoutDirection, .rightToLeft)`
- لا يوجد remote git مرتبط حالياً

## الخطوات القادمة المقترحة
- [ ] ربط Backend حقيقي (API)
- [ ] نشر على TestFlight
- [ ] إضافة Onboarding للمستخدم الجديد
- [ ] نظام إنشاء استبيانات للمؤسسات
- [ ] تصدير PDF للتقارير
- [ ] Cross-analysis حقيقي مبني على بيانات فعلية
