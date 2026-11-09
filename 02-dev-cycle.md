# فصل ۲ — چرخه کدنویسی روزمره: از feature تا silver bullet

> 🎯 **صحنه:** روز کاری معمولی — «این feature رو بگیر، این bug رو fix کن، ولی حواست به technical debt باشه». پرکاربردترین ~۲۰ اصطلاحی که هر روز می‌شنوی.

---

## ۲.۱ — هسته کار: bug، feature، fix

| اصطلاح | تلفظ | معنی | جمله واقعی |
|---|---|---|---|
| **feature** | فی-چِر | قابلیت جدید | «This feature ships next sprint.» |
| **bug** | باگ | خطای نرم‌افزار | «There's a nasty bug in checkout.» |
| **fix** | فیکس | رفع باگ | «Hotfix is deployed.» |
| **issue** | ایشو | مسئله/گزارش (در tracker) | «Open an issue, please.» |
| **reproduce / repro** | ری-پرو-دیوس / ریپرو | بازتولید خطا | «I can't reproduce it on my machine.» |
| **root cause** | روت کاز | ریشه اصلی مشکل | «We found the root cause — it's a race condition.» |
| **workaround** | ورک-ا-راوند | راه‌حل موقتی | «It's a workaround, not a real fix.» |
| **patch** | پَچ | وصله کوچک | «Security patch coming today.» |

> 🔑 جمله‌ی طلایی که در هر تیم می‌شنوی: «Works on my machine!» — شوخی معروف وقتی باگی فقط روی سیستم یک نفر است. و جواب استانداردش: «Then it's an environment issue.»

## ۲.۲ — کیفیت و بزرگی: edge case تا spaghetti

| اصطلاح | تلفظ | معنی | صحنه |
|---|---|---|---|
| **edge case** | اِج کِیس | حالت مرزی/نادر | «What about edge cases — empty cart? null user?» |
| **corner case** | کورنر کِیس | حالت خیلی حاشیه‌ای | «That's an extreme corner case, skip it for now.» |
| **happy path** | ها-پی پَث | مسیر بدون خطا | «The happy path works; errors are a mess.» |
| **smoke test** | اسموک تست | تست اولیه دود (کار می‌کند یا نه؟) | «Run a smoke test before pushing.» |
| **technical debt** | تِک-نیکل دِت | بدهی فنی (کد سریعِ کثیف) | «We're accumulating technical debt.» |
| **refactor** | ری-فَک-تِر | بازسازی بدون تغییر رفتار | «Refactor now or cry later.» |
| **legacy** | لِگِسی | قدیمی و موروثی | «Nobody touches that legacy module.» |
| **spaghetti code** | اسپاگِتی کُد | کد درهم‌وبرهم | «That file is spaghetti code.» |
| **hardcoded** | هارد-کُدِد | ثابت‌نویسی در کد | «The API URL is hardcoded — bad.» |
| **scalable** | اسکِیل-ابل | مقیاس‌پذیر | «This design isn't scalable.» |
| **robust** | رو-بَست | مقاوم/محکم | «Make it robust against bad input.» |
| **flaky** | فلِی-کی | بی‌ثبات (گاهی پاس، گاهی fail) | «These tests are flaky.» |

> 🔑 تصویر ذهنی‌ها: **technical debt** = وام گرفتن زمان از آینده (سریع کد بزن، بعداً بهره‌اش رو پرداخت کن)؛ **edge case** = لبه‌ی صندلی که کاربر می‌افته؛ **happy path** = جاده‌ی صاف بدون چاله.

## ۲.۳ — چرخه انتشار: MVP تا deprecate

| اصطلاح | تلفظ | معنی | صحنه |
|---|---|---|---|
| **MVP** | اِم-وی-پی | Minimum Viable Product — کمینه‌ی قابل‌عرضه | «Ship the MVP first.» |
| **ship / ship it** | شیپ | منتشر کن! | «Ship it! 🚀» |
| **release** | ری-لیس | انتشار نسخه | «Release 2.0 is out.» |
| **breaking change** | بریکینگ چِینج | تغییر شکست‌دهنده (نسخه قبلی‌ها را می‌شکند) | «This is a breaking change — major bump.» |
| **deprecated** | دِپ-ری-کِی-تِد | منسوخ‌شده (هنوز کار می‌کند، ولی نرو سمتش) | «This method is deprecated.» |
| **sunset** | سان-سِت | تعطیلی تدریجی محصول/قابلیت | «We're sunsetting the old dashboard.» |
| **out of scope** | آوت اِو اسکوپ | خارج از دامنه پروژه | «That's out of scope for this sprint.» |
| **scope creep** | اسکوپ کریپ | خزیدنِ دامنه (کارِ اضافه‌ی ناخواسته) | «Beware of scope creep.» |
| **quick win** | کوئیک وین | دستاورد سریع | «Let's grab some quick wins first.» |
| **low-hanging fruit** | لو-هَنگینگ فروت | میوه‌ی آسان (کار آسانِ پربازده) | «Fix the low-hanging fruit first.» |
| **silver bullet** | سیل-وِر بولِت | راه‌حل جادویی (که وجود ندارد!) | «There's no silver bullet for performance.» |
| **bikeshedding** | بایک-شِدینگ | بحث بی‌مورد روی جزئیات | «This is bikeshedding — move on.» |

> 🔑 دیالوگ واقعی جلسه (فهم کن، بعد بلند بخوان):

```text
PM:  We need payments by Friday.
Dev: Full payments are out of scope for Friday. The MVP is a
     manual invoice flow; proper integration is next sprint.
PM:  That's a hard blocker for the launch...
Dev: We can ship a quick win: Zarinpal-only, no refunds. The rest
     is technical debt we'll pay down later.
PM:  Deal. But no scope creep!
```

ترجمه روان: مدیر محصول پرداخت تا جمعه می‌خواهد؛ دولوپر می‌گوید پرداخت کامل خارج از دامنه است، MVP فاکتور دستی است؛ بعد راه‌حل میان‌برِ زرین‌پال‌فقط را می‌گذارد و بقیه را بدهی فنی می‌کند.

---

## ✅ جمع‌بندی فصل

- هسته: feature/bug/fix/issue/reproduce/root cause — «works on my machine» شوخی رایج
- کیفیت: edge case، happy path، technical debt، refactor، legacy، flaky
- انتشار: MVP، ship it، breaking change، deprecated، sunset
- مدیریت دامنه: out of scope، scope creep، quick win، low-hanging fruit
- جادو وجود ندارد: no silver bullet؛ جزئیات‌بازی = bikeshedding

## 📝 تمرین فصل ۲

1. درک: «I hacked together a workaround, but it's accumulating technical debt.» یعنی چه؟
2. چه اصطلاحی مناسب‌تر است؟ «The user typed 5000 chars in the name field and the app crashed» → این یک ... است. (bug عادی / edge case / breaking change)
3. تلفظ‌ها را بنویس: deprecate، scalable، robust، legacy
4. حالت‌سازی: لیدت می‌گوید «Can you ship the search feature by Wednesday?» ولی می‌دانی Wednesday عدد واقعی نیست. با سه اصطلاح از این فصل جواب حرفه‌ای بده (انگلیسی + ترجمه).
5. تشخیص: کدام‌یک technical debt است؟ (الف) تست خودکار نوشتن (ب) برای سرعت، validation را skip کردن با توضیح TODO (ج) مستندسازی

<details><summary>جواب‌ها</summary>

1. «یک راه‌حل موقتی سریع‌وساخت درآوردم، ولی داره بدهی فنی جمع می‌کنه» — یعنی الان کار می‌کند ولی بعداً باید درستش کنی.
2. **edge case** — ورودی نادر/مرزی که مسیر عادی را می‌شکند.
3. دِپ-ری-کِی-تِد / اسکِیل-ابل / رو-بَست / لِگِسی
4. نمونه: «Full search is out of scope by Wednesday, but I can ship a quick win — a basic title-only search. The advanced filters are next sprint; anything more would be scope creep.» (ترجمه: جستجوی کامل تا سه‌شنبه خارج از دامنه است، ولی یک برنده‌ی سریع — جستجوی ساده عنوان — می‌توانم بدهم؛ فیلترهای پیشرفته اسپرینت بعدی است؛ بیشتر از این scope creep می‌شود.)
5. (ب) — skip کردن با TODO یعنی «سریع الان، پرداخت بعداً» = دقیقاً بدهی فنی.
</details>

➡️ **فصل بعد:** جلسات و Scrum — standup، blocker، sprint و ادبیات جلسات.
