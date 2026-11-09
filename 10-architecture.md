# فصل ۱۰ — معماری و اصول کدنویسی: زبان آرشیتکت‌ها

> 🎯 **صحنه:** جلسه معماری: «The monolith is fine for now, but let's at least decouple payments. Follow SOLID, avoid premature abstraction — KISS!» — واژه‌های طراحی نرم‌افزار که در code reviewهای معماری و مصاحبه‌های senior همه‌جاست.

---

## ۱۰.۱ — شکل سیستم: monolith تا microservices

| اصطلاح | یعنی | جمله |
|---|---|---|
| **monolith** | مونولیت — همه‌چیز در یک اپ | «It's a monolith, and that's fine for now.» |
| **microservices** | مایکروسرویس‌ها — سرویس‌های کوچک مستقل | «Split payments into a microservice.» |
| **decouple / coupling** | جداسازی / وابستگی | «Payments and auth are tightly coupled.» |
| **tightly coupled** | چسبیده به هم (تغییر یکی، می‌شکند دیگری) | «This is tightly coupled to the DB schema.» |
| **loosely coupled** | جداشده (سالم) | «Aim for loosely coupled modules.» |
| **modular** | ماجولار | «Keep it modular — swap-in components.» |
| **monorepo / polyrepo** | چند پروژه در یک ریپو / هر پروژه یک ریپو | «UI and API live in a monorepo.» |
| **serverless** | بدون سرور (توابع managed) | «Auth goes serverless.» |
| **event-driven** | رویدادمحور (کوئری و event) | «The flow is event-driven via the queue.» |
| **distributed system** | سیستم توزیع‌شده | «Debugging distributed systems is hard.» |
| **trade-off** | ترید-آف — معاوضه (این را بگیر، آن را بده) | «Every architecture is a trade-off.» |
| **over-engineering** | اِو-اِنجینیرینگ | مهندسی بیش از حد | «This abstraction is over-engineering.» |

> 🔑 جمله‌ی کلاسیک آرشیتکت‌ها: «**It depends.**» — هر انتخاب معماری یک trade-off دارد؛ جواب مطلق وجود ندارد. و هشدار مشهور: **premature optimization is the root of all evil** (بهینه‌سازی زودهنگام ریشه همه شرارت‌ها — دونالد کنوث!).

## ۱۰.۲ — اصول کدنویسی (مخفف‌های مقدس)

| اصل | یعنی | جمله |
|---|---|---|
| **SOLID** | ۵ اصل طراحی شیءگرا (Single responsibility, Open-closed, Liskov, Interface segregation, Dependency inversion) | «This violates the Single responsibility principle.» |
| **DRY** | Don't Repeat Yourself — تکرار ممنوع | «DRY it up — extract a helper.» |
| **KISS** | Keep It Simple, Stupid — ساده نگه دار | «KISS! Why the generic factory for one case?» |
| **YAGNI** | You Ain't Gonna Need It — چیز الان‌لازم‌نشده نساز | «YAGNI — we don't need 3 themes yet.» |
| **Separation of Concerns (SoC)** | جداسازی دغدغه‌ها | «Keep UI, logic and data separate.» |
| **Single source of truth** | یک منبع حقیقت واحد | «The config file is the single source of truth.» |
| **readability > cleverness** | خوانایی بر هوشمندی | «Don't be clever — be readable.» |
| **clean code** | کد تمیز (کتاب رابرت مارتین) | «Small functions, meaningful names.» |

> 💡 **SOLID باز شده (برای مصاحبه):**
> **S**ingle responsibility = هر کلاس یک دلیل برای تغییر داشته باشد
> **O**pen-closed = برای افزودن قابلیت باز، برای تغییر بسته
> **L**iskov substitution = زیرنوع باید جای نوع پدر بنشیند
> **I**nterface segregation = interface های بزرگ پرچرب ممنوع
> **D**ependency inversion = به abstraction وابسته باش، نه پیاده‌سازی

## ۱۰.۳ — الگوها و ضدها

| اصطلاح | یعنی | جمله |
|---|---|---|
| **design pattern** | الگوی طراحی (راه‌حل استاندارد مسئله شناخته) | «A factory pattern fits here.» |
| **anti-pattern** | ضدالگو (راه‌حل رایجِ غلط) | «God objects are an anti-pattern.» |
| **singleton / factory / observer / strategy** | الگوهای کلاسیک | «Use an observer for the events.» |
| **god object / god class** | شیء خدا — همه‌چیز را می‌داند | «UserService is a god class — 2000 lines!» |
| **wrapper / adapter** | پوشاننده / مبدل | «Write a thin wrapper over the SDK.» |
| **abstraction** | انتزاع — پنهان‌کردن جزئیات | «The abstraction is leaking!» |
| **leaky abstraction** | انتزاع سوراخ (جزئیاتش پیدا می‌شود) | «Classic leaky abstraction — the ORM exposes SQL.» |
| **boilerplate** | بویلر-پلیت | کد تکراری تشریفاتی | «Too much boilerplate for one API call.» |
| **magic number / magic string** | عدد/رشته جادویی بی‌نام | «What is 86400? Extract a constant!» |
| **code smell** | بوِ کد (نشانه مشکل نه باگ) | «Long parameter list is a code smell.» |

> 🔑 **code smell** = چیزی که «بو می‌دهد» — کار می‌کند ولی نشانه طراحی ناسالم است (تابع ۵۰۰ خطی، کامنت‌های توضیح-دهنده‌ی کد بی‌معنی، conditional های تودرتو). بو → smell → بگرد، معمولاً یک refactor واقعی زیرش پنهان است.

## ۱۰.۴ — فرایند تصمیم معماری

| اصطلاح | یعنی | جمله |
|---|---|---|
| **POC (Proof of Concept)** | نمونه اثبات ایده | «Build a POC first — one week.» |
| **spike** | بررسی سریع بدون تعهد (در اسکرام) | «Time-boxed spike on WebSockets.» |
| **technical spec / RFC** | سند طراحی قبل از کد | «Write an RFC and get feedback.» |
| **benchmark** | بنچمارک — اندازه‌گیری مقایسه‌ای | «Benchmark before you choose the ORM.» |
| **greenfield / brownfield** | پروژه از صفر / پروژه موجود | «Greenfield lets us pick the stack.» |
| **migrate / migration path** | مهاجرت / مسیر مهاجرت | «What's the migration path for users?» |
| **vendor lock-in** | قفل‌شدن به یک فروشنده | «Watch out for vendor lock-in.» |
| **cutting corners** | کوتاه‌روی (کیفیت را فدا کردن) | «We're cutting corners on security.» |

---

## ✅ جمع‌بندی فصل

- شکل: monolith تا microservices؛ decouple کن؛ همه‌چیز trade-off است؛ «It depends»
- مخفف‌ها: SOLID/DRY/KISS/YAGNI — بازشده‌شان را برای مصاحبه بلد باش
- الگو: design pattern ✅ / anti-pattern ❌؛ code smell یعنی «بو»؛ god object ممنوع
- فرایند: POC/spike → RFC → benchmark؛ greenfield/brownfield؛ vendor lock-in

## 📝 تمرین فصل ۱۰

1. درک: «We're over-engineering — a POC with no abstraction would answer the question in a day.» یعنی چی؟
2. کدام اصل نقض شده؟ «تابعی که هم به دیتابیس وصل می‌شود، هم HTML می‌سازد، هم ایمیل می‌فرستد.»
3. حالت‌سازی: lead می‌گوید «Rewrite everything in Rust.» تو با ۳ اصطلاح (trade-off، greenfield، premature) ریسک را بگو.
4. YAGNI با یک مثال واقعی از پروژه‌هایت توضیح بده.
5. کدام یک code smell است؟ (الف) تابع ۴۰۰ خطی با ۱۲ پارامتر (ب) تابع ۱۰ خطی با اسم معنادار (ج) کامنت توضیح الگوریتم پیچیده

<details><summary>جواب‌ها</summary>

1. «داریم مهندسی‌بیش‌ازحد می‌کنیم — یک نمونه اثبات ایده بدون انتزاع، جواب سوال را در یک روز می‌دهد.»
2. نقض Single responsibility (و Separation of Concerns) — سه دلیل تغییر متفاوت در یک تابع.
3. نمونه: «That's a trade-off, not a free win — a rewrite is a greenfield project with real risk. We'd cut corners on features for months, and Rust expertise is a hiring constraint. Let's benchmark the bottleneck first — optimizing the wrong layer is premature.»
4. مثال: ساخت سیستم theme switcher سه‌گانه وقتی هیچ مشتری ازش نخواسته (فقط «شاید بعداً»)؛ کد می‌میرد قبل از مصرف.
5. (الف) — طول + پارامترهای زیاد = smell کلاسیک (Long method / Long parameter list).
</details>

➡️ **فصل بعد:** چت و مکاتبه — مخفف‌ها و جملات مؤدبانه.
