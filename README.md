# ماسة الشام للحوالات المالية — مشروع VS Code

هذا مشروع Next.js + PostgreSQL + Prisma + Auth.js (JWT sessions) كبداية حقيقية قابلة للتطوير.

## قبل التشغيل

المشروع لا يحتوي على أي أسعار صرف أو عمولات أو أسماء محافظ وهمية. أضفها من قاعدة البيانات/لوحة الإدارة.

### 1) المتطلبات
- Node.js حديث
- Docker Desktop (للتشغيل المحلي بسهولة)
- حساب Google Cloud لإعداد Google OAuth إذا أردت تسجيل Google

### 2) التثبيت

```bash
npm install
copy .env.example .env
docker compose up -d
```

على macOS/Linux:
```bash
cp .env.example .env
```

أنشئ قيمة قوية لـ `AUTH_SECRET`.

### 3) قاعدة البيانات

```bash
npx prisma db push
npm run db:seed
```

لتشغيل التطبيق:
```bash
npm run dev
```

ثم افتح:
http://localhost:3000

## Google OAuth

في Google Cloud Console أنشئ OAuth Client من نوع Web Application.

Local redirect URI:
`http://localhost:3000/api/auth/callback/google`

ضع القيم في:
- AUTH_GOOGLE_ID
- AUTH_GOOGLE_SECRET

في الإنتاج استخدم نطاق موقعك الحقيقي وHTTPS.

## حساب المدير

ضع:
- ADMIN_EMAIL
- ADMIN_PASSWORD

في `.env` ثم:
```bash
npm run db:seed
```

لا تضع كلمة مرور حقيقية داخل Git.

## ملاحظات مهمة للإنتاج

هذه نسخة أساس قوية وليست اعتماداً نهائياً لخدمة مالية قبل مراجعة أمنية واختبارات.

يجب قبل الإطلاق إضافة:
- استعادة كلمة المرور عبر بريد إلكتروني حقيقي.
- التحقق من البريد.
- MFA للمدير.
- Rate limiting وWAF.
- CSRF/XSS/security headers حسب بنية النشر.
- مزود بريد موثوق.
- تخزين الأسرار في Secret Manager.
- نسخ احتياطي PostgreSQL ومراقبة.
- سجلات تدقيق كاملة وغير قابلة للتلاعب قدر الإمكان.
- سياسة خصوصية وشروط استخدام ومتطلبات الامتثال المناسبة للجهة المرخصة.
- WhatsApp Business API إذا كان المطلوب إرسال الرسائل آلياً من الخادم.
- مراجعة قانونية وأمنية متخصصة قبل استخدام النظام مع بيانات مالية حقيقية.

## بيانات الشركة المستخدمة

- الاسم: ماسة الشام للحوالات المالية
- English: Masa Al-Sham Financial Transfers
- التأسيس: 2020
- الموقع: بغداد، العراق
- الهاتف/WhatsApp: +9647772073950
- الدول: سوريا، مصر، لبنان، تركيا

لا توجد في المشروع أرقام ترخيص أو بريد إلكتروني أو أسعار صرف أو عمولات مخترعة.
