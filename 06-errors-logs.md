# فصل ۶ — ارورها و لاگ‌ها: زبان دیباگ

> 🎯 **صحنه:** ساعت ۱۱ شب، stack trace داری و تیکت‌ها می‌بارند. واژه‌های ارور و لاگ — هم برای فهمیدن پیام‌ها، هم برای **گزارش‌دادن باگ به تیم/آپ‌استریم**.

---

## ۶.۱ — آناتومی یک ارور

| اصطلاح | تلفظ | یعنی | نمونه پیام |
|---|---|---|---|
| **stack trace** | اِستَک تریس | زنجیره فراخوانی‌ها لحظه خطا | «Paste the full stack trace.» |
| **exception** | اِکس-سِپ-شن | استثنا (خطای قابل پرتاب) | «Uncaught exception at line 42.» |
| **throw / catch** | ثرو / کچ | پرتاب / گرفتن خطا | «Throw a specific error, not a generic one.» |
| **fatal error** | فی-تِل | خطای مرگبار (برنامه می‌میرد) | «A fatal error killed the process.» |
| **warning** | وار-نینگ | هشدار (کار می‌کند ولی...) | «Fix the deprecation warning.» |
| **deprecated** | دِپ-ری-کِی-تِد | منسوخ — جایگزین دارد | «This API is deprecated since v3.» |
| **timeout** | تایم-آوت | زمان انتظار تمام شد | «Request timed out after 30s.» |
| **memory leak** | مِم-ری لیک | نشت حافظه | «The server leaks memory over hours.» |
| **race condition** | ریس کِن-دی-شن | شرایط مسابقه (دو پروسه همزمان) | «It's a classic race condition.» |
| **deadlock** | دِد-لاک | بن‌بست دوطرفه | «Two transactions deadlocked.» |
| **segfault (segmentation fault)** | سِگ-فالت | دسترسی به حافظه ممنوعه (C/C++) | «Random segfaults in prod.» |
| **crash / freeze** | کْرَش / فریز | سقوط / هنگ | «The tab crashes; the app freezes.» |
| **silent failure** | سای-لِنت فی-لیور | شکست بی‌صدای اطلاع | «Worst kind: silent failure.» |

## ۶.۲ — ادبیات گزارش باگ (bug report)

گزارش باگ حرفه‌ای همیشه این ۵ بخش را دارد:

```text
**Steps to reproduce (repro steps):**
1. Open /checkout
2. Apply coupon "SALE10"
3. Click Pay

**Expected behavior (انتظار):**
Payment completes with 10% off.

**Actual behavior (واقعیت):**
500 error; user charged full price.

**Environment (محیط):**
Chrome 129, Windows 11, production
```

اصطلاح‌های کلیدی:

| اصطلاح | معنی |
|---|---|
| **steps to reproduce** | گام‌های بازتولید — بدون این، باگ تقریباً قابل حل نیست |
| **expected / actual behavior** | رفتار مورد انتظار / واقعی |
| **environment / repro rate** | محیط / نرخ بازتولید (همیشه؟ ۱ از ۵ بار؟) |
| **intermittent** | متناوب — گاه‌به‌گاه (سخت‌ترین باگ‌ها!) |
| **regression** | بازگشت باگ قدیمی (قبلاً فیکس بود، دوباره شکسته) |
| **hotfix** | فیکس اضطراری |
| **mitigation** | کاهش اثر (قبل از حل ریشه‌ای) |

> 🔑 جمله‌ای که هر دولوپری می‌ترسد بشنود: **«This is a regression!»** — یعنی چیزی که فیکس بود دوباره شکسته؛ اولویت یک.

## ۶.۳ — ادبیات لاگ و مانیتورینگ

| اصطلاح | معنی | جمله |
|---|---|---|
| **log level** | سطح لاگ: error/warn/info/debug | «Log at debug level, not prod-info spam.» |
| **tail the logs** | دنبال کردن زنده لاگ | «Tail the logs while I click.» |
| **grep the logs** | جستجو در لاگ‌ها | «Grep for 'timeout' in yesterday's logs.» |
| **verbose** | پرحرف (لاگ مفصل) | «Enable verbose logging temporarily.» |
| **trace ID / correlation ID** | شناسه ردیابی یک درخواست در همه سرویس‌ها | «Find by trace ID: 8f3a.» |
| **spike / dip** | جهش / افت ناگهانی | «Latency spike at 3 AM.» |
| **flaky connection** | اتصال بی‌ثبات | «Network is flaky in the container.» |
| **hot path** | مسیر پرمصرف کد | «Don't log JSON in the hot path.» |
| **noise** | لاگ‌های بی‌ارزش | «Too much noise hides real errors.» |

## ۶.۴ — مکالمه دیباگ (چت واقعی)

```text
Dev:  Prod is throwing 500s on /checkout.
Lead: Stack trace? Paste it here.
Dev:  "TypeError: cannot read properties of undefined (reading 'total')"
Lead: That's the coupon object — the API returns null when no coupon.
Dev:  Confirmed. Shipping a null check now. ETA 10 min.
Lead: 🙏 Add a test so it's not a regression.
```

واژه‌های ریز این چت: `throwing 500s` = ارور ۵۰۰ می‌دهد؛ `cannot read properties of undefined` = معروف‌ترین پیام JS دنیا (null/undefined را خوانده‌ای!)؛ `Confirmed` = تأیید/تکرار خطا؛ `null check` = چک کردن قبل استفاده.

---

## ✅ جمع‌بندی فصل

- آناتومی: stack trace/exception/throw-catch/timeout/race condition/deadlock
- گزارش باگ: steps to reproduce + expected/actual + environment + repro rate
- «regression» = ترسناک‌ترین کلمه؛ «intermittent» = سخت‌ترین باگ
- لاگ: log level، tail، grep، trace ID، noise
- پیام‌های معروف: «cannot read properties of undefined»

## 📝 تمرین فصل ۶

1. این پیام را به زبان آدمیزاد توضیح بده: `ECONNREFUSED 127.0.0.1:5432`
2. باگ کاربر گزارش می‌دهد: «کار نمی‌کنه!» — سه چیز که در bug report ازش بخواهی (اصطلاحات انگلیسی + معنی).
3. حالت‌سازی: باگی intermittent است (۱ از ۱۰ بار). به لیدت انگلیسی توضیح بده که چرا زمان‌بر است.
4. ترجمه مفهومی: «Enable verbose logging on staging and grep for 'timeout' — let's find the root cause, not another workaround.»
5. کدام یک regression است؟ (الف) باگ جدید کشف شد در کد قدیمی (ب) قابلیتی که هفته پیش فیکس شده بود دوباره خراب شده (ج) محدودیت شناخته‌شده API

<details><summary>جواب‌ها</summary>

1. «اتصال رد شد (connection refused) روی آدرس لوکال پورت ۵۴۳۲» — یعنی هیچ پروسه‌ای روی آن پورت گوش نمی‌دهد: دیتابیس خاموش است یا پورت/آدرس غلط است.
2. steps to reproduce (گام‌های بازتولید)، expected vs actual behavior (انتظار در برابر واقعیت)، environment/repro rate (محیط و نرخ وقوع).
3. نمونه: «It's intermittent — reproduces maybe 1 in 10 times, which makes the root cause hard to pin down. I'll add verbose logging and a trace ID to catch it when it happens.» (متناوب است — شاید ۱ از ۱۰ بار؛ ریشه‌یابی سخت می‌شود؛ لاگ verbose و trace ID می‌گذارم تا موقع وقوع بگیرمش.)
4. «روی staging لاگ verbose روشن کن و دنبال 'timeout' بگرد — برویم سراغ ریشه مشکل، نه یک workaround دیگر.»
5. (ب) — بازگشت باگِ فیکس‌شده = regression.
</details>

➡️ **فصل بعد:** فرانت و UI/UX — ادبیات طراحی و رابط کاربری.
