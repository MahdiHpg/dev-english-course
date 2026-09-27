# فصل ۴ — Code Review و Pull Request: ادبیات دروازه کیفیت

> 🎯 **صحنه:** PR زدی؛ کامنت‌ها داره میان: «LGTM 🎉»، «nit: rename this variable»، «Blocking: this leaks the API key». ادبیات ریویو — هم خواندن و هم **نوشتن**.

---

## ۴.۱ — چرخه PR و وضعیت‌هایش

| اصطلاح | تلفظ | معنی | جمله |
|---|---|---|---|
| **PR (Pull Request) / MR** | پی-آر / اِم-آر | درخواست ادغام (MR = اصطلاح گیت‌لب) | «Open a PR when ready.» |
| **draft PR / WIP** | درَفت | PR ناتمام — هنوز ریویو نخواه | «It's a draft PR, still WIP.» |
| **open a PR** | — | باز کردن PR | «I'll open a PR today.» |
| **review** | ری-ویو | بازبینی | «PR needs review.» |
| **approve** | اِپ-روو | تأیید | «It's approved — merge it.» |
| **request changes** | ری-کوِست چِینجس | درخواست اصلاح قبل merge | «He requested changes.» |
| **address feedback** | اَدرس فی-دبک | رسیدگی به کامنت‌های ریویو | «I addressed all the feedback.» |
| **merge** | مرج | ادغام به شاخه اصلی | «Merged and deployed.» |
| **squash** | اسکواش | له‌کردن کامیت‌ها به یک کامیت | «Squash and merge, please.» |
| **rebase** | ری-بِیس | بازپایه‌گذاری روی شاخه جدید | «Rebase on main first.» |
| **conflict** | کان-فلیکت | تعارض ادغام | «Fix the conflicts and re-request review.» |
| **re-request review** | — | دوباره درخواست ریویو بعد اصلاح | «Re-requested review after fixes.» |

## ۴.۲ — ادبیات کامنت‌های ریویو (هر کامنت یک وزن دارد ⭐)

| اصطلاح | یعنی | وزن |
|---|---|---|
| **LGTM** (Looks Good To Me) | از نظر من خوبه — تأیید | تأیید نهایی |
| **nit / nitpick** | نیت‌پیک — ایراد جزئی (سلیقه‌ای) | غیرالزامی |
| **blocking** | مانع — باید قبل merge اصلاح شود | الزامی |
| **non-blocking** | غیرمانع — بعداً هم می‌شود | پیشنهاد |
| **suggestion** | پیشنهاد آماده اعمال (دکمه apply دارد) | سریع |
| **question** | سوال — توضیح بده | گفتگو |
| **FYI** | برای اطلاعت | اطلاع |
| **TODO** | کار باقی‌مانده در کد | یادآور |
| **scope creep!** | این خارج از دامنه PR است | اخلاق ریویو |

> 🔑 چطوری **بخوانی**‌شان (چیزی که فقط با تجربه فهمیده می‌شود):
> «nit:» یعنی اعصابم خرد نشده، فقط نظر سلیقه — نگران نشو.
> «Blocking:» یعنی merge نکن تا اصلاح شه.
> بدون پیشوند ولی لحن سوال = گفتگو؛ با «please» = مودبانه الزامی.

## ۴.۳ — چطوری **بنویسی** (نه فقط بخوانی) — توضیحات PR

قالب توضیحات PR (همان که در دوره گیت دیدی، با اصطلاحات کامل‌شده):

```text
## What
Adds password reset flow (emails + token validation).

## Why
Closes #231 — users can't recover accounts.

## How
- New endpoint /auth/reset (rate-limited)
- Reuses the email template service

## Testing
- Unit tests for token expiry ✅
- Manual test on staging ✅

## Risk
Touches auth middleware — @sara please double-check.
```

اصطلاح‌های این قالب: `closes #231` (تیکِت خودکار بسته می‌شود)، `rate-limited` (محدود به تعداد درخواست)، `on staging` (روی محیط آزمایشی — فصل ۹).

## ۴.۴ — ریویو **دادن** با ادبیات درست

```text
✅ سخت روی کد، مهربان با آدم:
"Nice use of a lookup table here! 🎉"
"nit: `usr` → `user` for readability? (non-blocking)"
"Question: what happens if the API returns an empty array?"
"Blocking: this logs the raw token — please mask it."
"FYI: we have a shared util for this — `formatDate()`."

❌ هرگز:
"This is wrong."              ← بدون توضیح
"Why did you do it this way??" ← لحن بازخواست
"LGTM" بدون خواندن             ← خیانت به تیم
```

و جواب دادن به ریویو:

```text
"Good catch — fixed in 8f3a2b1."      (نکته خوبی بود — اصلاح شد)
"Fair point. I kept it as-is because... (توضیح) — happy to change if you prefer."
"Done ✅" / "Addressed in the latest commit."
"Not sure I follow — could you elaborate?"   (نفهمیدم — بیشتر توضیح می‌دی؟)
```

(`Good catch` = پرکاربردترین تشکر ریویو؛ `elaborate` = بازتر توضیح بده.)

---

## ✅ جمع‌بندی فصل

- چرخه: draft → open → review → (address feedback → re-request) → approve → squash merge
- وزن کامنت‌ها: LGTM تأیید / nit سلیقه / blocking الزامی / non-blocking پیشنهاد
- توضیحات PR: What/Why/How/Testing/Risk + `Closes #231`
- دادن ریویو: تعریف کن، nit را برچسب بزن، blocking را شفاف؛ جواب دادن: Good catch / Addressed

## 📝 تمرین فصل ۴

1. درک: کامنت «nit: use early return here (non-blocking)» یعنی چه؟ باید قبل merge اصلاحش کنی؟
2. حالت‌سازی: ریویوچی گفته «Blocking: no error handling on the fetch». جواب حرفه‌ای + کار بعدی‌ات را بنویس.
3. ترجمه مفهومی جمله لیدت: «Squash it and I'll approve — but address the nits first.»
4. کدام‌یک blocking است؟ (الف) variable name کوتاه (ب) API key هاردکد شده (ج) کامنت بدون نقطه
5. یک PR واقعی از پروژه‌ات باز کن و توضیحاتش را با قالب فصل ۴ بنویس (What/Why/How/Testing/Risk).

<details><summary>جواب‌ها</summary>

1. «اینجا return زودهنگام استفاده کن (ایراد جزئی، غیرالزامی)» — نه، قبل merge لازم نیست؛ ولی چون ارزان است معمولاً همان‌جا اعمالش می‌کنیم و Resolve می‌زنیم.
2. «Good catch! Added try/catch with a user-facing error message and a retry — addressed in commit a1b2c3d. Ready for re-review.» (و در PR، دوباره Re-request review.)
3. «کامیت‌ها را له کن (squash merge) تا approve کنم — ولی اول نیت‌ها (ایرادهای جزئی) را اصلاح کن.»
4. فقط (ب) blocking است — راز لو رفته = امنیت. (الف) nit، (ج) بی‌اهمیت.
</details>

➡️ **فصل بعد:** ادبیات Git — rebase، cherry-pick، upstream و بقیه.
