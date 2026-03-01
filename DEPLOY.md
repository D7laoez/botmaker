# تعليمات نشر مشروع BotMaker

## المتطلبات
- Node.js 18 أو أحدث
- قاعدة بيانات SQLite أو PostgreSQL
- نطاق (Domain) مع HTTPS (مهم للـ Telegram Webhook)

## خطوات النشر

### 1. رفع الملفات
```bash
# انسخ هذه الملفات إلى السيرفر:
# - src/
# - prisma/
# - public/
# - package.json
# - .env
# - next.config.ts
# - tailwind.config.ts
# - tsconfig.json
```

### 2. تثبيت المتطلبات
```bash
npm install
# أو
bun install
```

### 3. إعداد قاعدة البيانات
```bash
npx prisma generate
npx prisma db push
```

### 4. إعداد متغيرات البيئة
أنشئ ملف `.env`:
```
DATABASE_URL="file:./db/botmaker.db"
NEXT_PUBLIC_APP_URL="https://your-domain.com"
```

### 5. البناء
```bash
npm run build
```

### 6. التشغيل
```bash
npm run start
```

## النشر على منصات مختلفة

### Vercel (الأسهل)
1. اربط المشروع بـ GitHub
2. استورد في Vercel
3. أضف متغيرات البيئة
4. سيتم النشر تلقائياً

### Railway
1. اربط المشروع بـ GitHub
2. أنشئ مشروع جديد
3. أضف PostgreSQL
4. أضف متغيرات البيئة

### سيرفر خاص (VPS)
```bash
# استخدم PM2 للإدارة
npm install -g pm2
pm2 start npm --name "botmaker" -- start
pm2 save
pm2 startup
```

## إعداد Telegram Webhook
- عند إنشاء بوت، سيتم إعداد الـ Webhook تلقائياً
- يجب أن يكون النطاق HTTPS
- الـ Webhook URL سيكون: `https://your-domain.com/api/webhook/[bot-id]`

## ملاحظات مهمة
1. تأكد من أن `NEXT_PUBLIC_APP_URL` يشير لنطاقك الفعلي
2. استخدم HTTPS للـ Webhook
3. قاعدة البيانات SQLite مناسبة للبداية، انتقل لـ PostgreSQL للإنتاج
