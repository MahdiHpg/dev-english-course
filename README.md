<div dir="rtl">

# 🎓 دوره جامع اصطلاحات انگلیسی برنامه‌نویسان — صفر تا آماده‌ی شرکت

<div align="center">

[![Language](https://img.shields.io/badge/Language-%D9%81%D8%A7%D8%B1%D8%B3%DB%8C-success?style=for-the-badge)](#)
[![Format](https://img.shields.io/badge/Format-PDF%20%2B%20Markdown-orange?style=for-the-badge)](#)
[![License](https://img.shields.io/badge/License-MIT-purple?style=for-the-badge)](#)

</div>

> **مخاطب:** برنامه‌نویس فارسی‌زبان که انگلیسی‌اش برای داکیومنت کافیه ولی در **تیم، جلسه، Code Review و مصاحبه** به اصطلاح‌ها برمی‌خوره و نمی‌فهمه یا بلد نیست درست تلفظ کنه
> **ساختار:** ۱۳ فصل — مرتب‌شده بر اساس «کجا به اصطلاح برمی‌خوری»: چرخه کدنویسی، جلسه، ریویو، گیت، ارور، فرانت، بک، دواپس، معماری، چت، استخدام

---

## 🎯 چرا این دوره؟

تو کد می‌زنی، داکیومنت می‌خونی، stack trace می‌بینی — ولی توی **standup فردا صبح** وقتی لید می‌گه «This is a blocker, let's touch base after the sprint» و می‌خوای جواب بدی، گیر می‌کنی. مشکل تو گرامر نیست؛ **اصطلاحات شغلی‌ان** که توی هیچ دوره‌ی زنی teaching نمی‌شن.

این دوره:
- **۲۵۰+ اصطلاح پرتکرار** واقعی تیم‌های نرم‌افزاری — با **تلفظ درست به فارسی** (cache = «کَش» نه «کاچه»!)
- معنی + جمله‌ی واقعی از محل استفاده (جلسه، چت، PR)
- دیالوگ‌های واقعی تیمی + تمرین با جواب
- مرتب‌شده بر اساس *صحنه‌ی برخورد* — نه الفبایی

---

## 🗺️ نقشه دوره

| فصل | صحنه | اصطلاح‌های نمونه |
|---|---|---|
| [فصل ۱](./01-principles.md) | اصول: چطور فکر و تلفظ کنیم | قواعد تلفظ، compound nouns، اشتباهات رایج ایرانی‌ها |
| [فصل ۲](./02-dev-cycle.md) | چرخه کدنویسی روزمره | bug، edge case، technical debt، deprecate |
| [فصل ۳](./03-meetings-agile.md) | جلسات و Scrum | standup، blocker، MVP، touch base |
| [فصل ۴](./04-code-review.md) | Code Review و PR | LGTM، nit， request changes، approve |
| [فصل ۵](./05-git-terms.md) | Git و ورژن کنترل | rebase، cherry-pick، upstream، force push |
| [فصل ۶](./06-errors-logs.md) | ارورها و لاگ‌ها | stack trace، race condition، timeout |
| [فصل ۷](./07-frontend-ui.md) | فرانت و UI/UX | breakpoint، pixel-perfect، skeleton |
| [فصل ۸](./08-backend-api.md) | بک‌اند و API و دیتابیس | payload، endpoint، CRUD، webhook |
| [فصل ۹](./09-devops-prod.md) | دواپس و production | staging، rollback، downtime، incident |
| [فصل ۱۰](./10-architecture.md) | معماری و اصول کدنویسی | SOLID، monolith، anti-pattern |
| [فصل ۱۱](./11-chat-polite.md) | چت و مکاتبه | FYI، ASAP، TL;DR + جملات مؤدبانه |
| [فصل ۱۲](./12-jobs-interview.md) | استخدام و مصاحبه | senior، offer، notice period |
| [فصل ۱۳](./13-cheatsheet.md) | چیت‌شیت جامع + گلاساری + نقشه راه | — |

---

## 🧪 روش استفاده از دوره

- **هر فصل = یک صحنه.** قبل از جلسه بعدی تیم، فصل جلسات رو بخون؛ قبل از اولین PR، فصل ریویو رو.
- تلفظ‌ها **تقریبی به فارسی**‌ان (کَش، آجایل) — هدف اول «فهمیدن و گفتن بدون لکنت» است؛ تلفظ دقیق native بعداً با تمرین می‌آید.
- تمرین‌های هر فصل ۳ نوع‌ان: **درک** (این جمله یعنی چی؟)، **حالت‌سازی** (در این موقعیت چه می‌گویی؟)، **تشخیص** (کدام اصطلاح مناسب‌تر است؟). جواب‌ها داخل بلوک‌های تاشو.

**قانون طلایی:** اصطلاح رو وقتی «بلدی» که بتونی توی جمله خودت استفاده‌ش کنی — نه فقط معنیش رو بدونی. هر اصطلاح جدید، امروز توی چت یا جلسه واقعی ازش استفاده کن.

---

## 📄 نسخه PDF

نسخه PDF رنگی راست‌به‌چپ (فونت وزیرمتن) در همین پوشه: **«دوره کامل اصطلاحات انگلیسی برنامه‌نویسان.pdf»**. بازسازی: `python build/build_pdf.py` + رندر Chrome headless.

---

## 🏷️ کلمات کلیدی و برچسب‌های سئو (SEO Keywords & Tags)

> **تگ‌های پیشنهادی برای مخزن گیت‌هاب (Topics):**
> `english-for-developers, dev-english, vocabulary, soft-skills, remote-work, persian-tutorial, farsi, انگلیسی-برنامه-نویسی`

**کلمات کلیدی جستجو:**  
آموزش زبان انگلیسی تخصصی برنامه نویسی, اصطلاحات انگلیسی دولوپرها pdf, مکالمه انگلیسی برای مصاحبه و دورکاری, واژگان تخصصی مهندسی کامپیوتر

---

## 📥 دانلود مستقیم نسخه نهایی کتاب (PDF)

برای دریافت نسخه کامل کتاب الکترونیکی، می‌توانید فایل PDF زیر را با بالاترین کیفیت دانلود کنید:

👉 **[دانلود کتاب کامل PDF (حجم ۵.۴ مگابایت)](https://github.com/MahdiHpg/dev-english-course/releases/download/v1.0/dev-english-course.pdf)**


