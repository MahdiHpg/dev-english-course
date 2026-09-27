# فصل ۳ — جلسات و Scrum: ادبیات standup و اسپرینت

> 🎯 **صحنه:** ۹ صبح standup داری؛ لید می‌پرسد «Any blockers?» و تو باید در ۳۰ ثانیه گزارش بدهی. اصطلاحات Scrum و ادبیات جلسات — پرتکرارترین مکالمه شغلی تو از فردا.

---

## ۳.۱ — لغت‌نامه Scrum (چارچوب چرخه کار)

| اصطلاح | تلفظ | معنی | جمله |
|---|---|---|---|
| **sprint** | اسپرینت | دوره کاری ۱-۲ هفته‌ای | «This sprint we ship auth.» |
| **backlog** | بَک-لاگ | لیست کل کارهای باقی | «Add it to the backlog.» |
| **sprint backlog** | — | کارهای این اسپرینت | «It's not in the sprint backlog.» |
| **user story** | یوزر استوری | یک کار به زبان کاربر | «This story needs refinement.» |
| **story points** | استوری پوینتس | واحد سختی/حجم کار | «This is 3 story points.» |
| **velocity** | وِ-لا-سی-تی | سرعت تیم در اسپرینت | «Our velocity dropped this sprint.» |
| **standup** | استَند-آپ | جلسه روزانه ایستاده ۱۵ دقیقه‌ای | «See you at standup.» |
| **retrospective / retro** | رِت-رو-اس-پِک-تیو / رِترو | جلسه «چه شد/چه نشد» آخر اسپرینت | «In the retro, let's discuss the outage.» |
| **demo / sprint review** | دِمُو | نمایش کار انجام‌شده | «Ready for the demo?» |
| **refinement / grooming** | ری-فاین-منت | آماده‌سازی استوری‌های آینده | «Refinement is tomorrow.» |
| **epic** | اِپیک | مجموعه‌ی بزرگ از استوری‌ها | «This belongs to the payments epic.» |
| **assignee / reporter** | اِسای-نی / ری-پور-تر | مسئول کار / گزارش‌دهنده تیکِت | «You're the assignee now.» |
| **sprint goal** | اسپرینت گول | هدف اصلی اسپرینت | «Our sprint goal is onboarding.» |

## ۳.۲ — سه جمله‌ی standup (قالب آماده — حفظ کن!)

فرمت استاندارد: «دیروز / امروز / موانع»

```text
1. Yesterday I finished the login endpoint and started on validation.
   (دیروز اندپوینت لاگین را تمام کردم و validation را شروع کردم)

2. Today I'll continue with validation and start writing tests.
   (امروز validation را ادامه می‌دهم و شروع به نوشتن تست می‌کنم)

3. No blockers. / I'm blocked on the API keys — still waiting on DevOps.
   (مانعی ندارم / روی کلیدهای API قفل هستم — هنوز منتظر DevOps هستم)
```

واژه‌های ریز این گزارش:

| اصطلاح | معنی | مثال |
|---|---|---|
| **blocker / blocked on** | مانع / قفل‌شده روی | «I'm blocked on design approval.» |
| **in progress** | در حال انجام | «The PR is in progress.» |
| **WIP** | work in progress — همان in progress | «It's WIP, don't review yet.» |
| **wrap up** | جمع‌بندی/تمام کردن | «Wrapping up the payment flow today.» |
| **pick up / take over** | برداشتن/تحویل گرفتن کار | «I'll pick up the ticket.» |
| **hand off** | تحویل دادن به دیگری | «I'm handing this off to Reza.» |
| **push back** | مقاومت/رد کردن درخواست | «We pushed back on the deadline.» |
| **align / on the same page** | هم‌نظر شدن / هم‌نظر بودن | «Let's align on the scope.» |
| **ETA** | estimated time of arrival — زمان تخمینی اتمام | «ETA? — End of tomorrow.» |

## ۳.۳ — اصطلاحات «ادبیات جلسه» (سؤال‌برانگیزترین‌ها)

| اصطلاح | تلفظ | یعنی واقعاً چی | مثال |
|---|---|---|---|
| **touch base** | تاچ بِیس | هم‌حرف زدن سریع | «Let's touch base after the demo.» |
| **circle back** | سرکل بَک | بعداً برگردیم سرش | «Good point — let's circle back on pricing.» |
| **deep dive** | دیپ دایو | بررسی عمیق | «We need a deep dive on the perf issue.» |
| **take this offline** | تیک دیس آف-لاین | این را خارج از جلسه حل کنیم | «Let's take this offline — it's blocking everyone.» |
| **action item** | اَکشن آی-تم | کار مشخص خروجی جلسه | «Action items: Ali fixes the build.» |
| **bandwidth** | بَند-ویذ | ظرفیت/وقت خالی | «I don't have the bandwidth this week.» |
| **heads-up** | هِدز-آپ | خبر مقدماتی | «Heads-up: deploy tonight.» |
| **on my plate** | آن مای پِی-ت | روی میزم است (بار کاری) | «I have a lot on my plate.» |
| **double-click on** | دابل-کلیک اون | بازش کنیم بیشتر (تینکریلی!) | «Let's double-click on that idea.» |
| **park it** | پارک ایت | بذاریم کنار فعلاً | «Park it in the backlog.» |
| **make the call** | میک ذِ کال | تصمیم نهایی بگیرد | «The lead will make the call.» |
| **sanity check** | سَن-یتی چِک | چک عقلانی/سریع | «Quick sanity check before we commit.» |

> ⚠️ این‌ها «corporate speak» انگلیسی‌اند — پر از metaphor. «Bandwidth» یعنی اینترنت نیست؛ «double-click» ربطی به موس ندارد؛ «take it offline» یعنی جلسه را رها نکنیم، بعداً خصوصی.

## ۳.۴ — خواستن/پیشنهاد دادن مؤدبانه (برای غریبه‌های انگلیسی!)

```text
پیشنهاد:  How about we split the ticket?          (چطوره تیکت رو بشکنیم؟)
          Maybe we could start with the API first. (شاید اول API رو شروع کنیم)
درخواست:  Could you take a look at my PR?          (می‌شه به PR من نگاه کنی؟)
          Would it be possible to extend the deadline? (ممکنه ددلاین تمدید شه؟)
مخالفت:   I see your point, but there's a risk with... (حرفت درسته، ولی یه ریسک...)
          Not sure about that — what if the API fails? (مطمئن نیستم — اگه API فیل شه چطور؟)
بی‌اطلاع: I'll get back to you on that.             (جوابشو بهت می‌دم)
          I need to check with the team first.       (اول باید با تیم چک کنم)
```

---

## ✅ جمع‌بندی فصل

- چرخه: sprint → backlog → standup (دیروز/امروز/blockers) → demo → retro
- گزارش standup با سه قالب آماده + blocker/in progress/WIP
- corporate speak: touch base، circle back، bandwidth، heads-up، on my plate
- مؤدبانه: How about / Could you / I see your point, but / I'll get back to you

## 📝 تمرین فصل ۳

1. درک: «Let's park it and circle back in the retro.» یعنی چی؟
2. standup سه‌خطی خودت را به انگلیسی بنویس (کار واقعی امروزت!) — با سه اصطلاح از این فصل.
3. حالت‌سازی: PM وسط standup می‌گوید «We also need dark mode this sprint.» تو با two اصطلاح (bandwidth، out of scope یا backlog) جواب بده.
4. کدام‌یک corporate speak است و یعنی چی: (الف) deep dive (ب) sanity check (ج) touch base (د) low-hanging fruit
5. تلفظ‌ها: retrospective، assignee، velocity، ETA

<details><summary>جواب‌ها</summary>

1. «بذاریمش کنار و توی جلسه retro دوباره بریم سراغش.»
2. نمونه: «Yesterday I finished the header component and started the cart logic. Today I'll wrap up the cart and push a draft PR. No blockers, but I need a design review — heads-up!»

3. نمونه: «I hear you, but my bandwidth is full with checkout this sprint — and dark mode is out of scope for the current sprint goal. Can we park it in the backlog for next sprint's refinement?»
(می‌شنوم، ولی ظرفیت من این اسپرینت پر از checkout است — و dark mode خارج از دامنه هدف اسپرینت فعلی است؛ می‌شود در backlog برای refinement بعدی پارکش کنیم؟)
4. همه corporate speak اند! (الف) بررسی عمیق — (ب) چک عقلانی سریع — (ج) هم‌حرفی سریع — (د) کار آسان پربازده (فصل ۲).
5. رِت-رو-اس-پِک-تیو / اِسای-نی / وِ-لا-سی-تی / اِی-تی-اِی (حرف‌به‌حرف)
</details>

➡️ **فصل بعد:** Code Review — ادبیات PR و آن دیسکوهای LGTM!
