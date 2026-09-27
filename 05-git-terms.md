# فصل ۵ — Git و ورژن کنترل: ادبیات دستورات و مکالمات

> 🎯 **صحنه:** همکارت می‌گوید «I rebased on main, force-pushed, now your branch has conflicts — cherry-pick the hotfix first.» از دوره Git دستورات را بلدی؛ الان **ادبیات مکالمه‌ای** را می‌گیری.

---

## ۵.۱ — اصطلاحات شاخه و همگام‌سازی

| اصطلاح | یعنی در مکالمه | جمله واقعی |
|---|---|---|
| **branch off** | شاخه زدن از | «Branch off main, please.» |
| **cut a branch** | (همان) شاخه ساختن | «I cut a branch from develop.» |
| **up to date** | به‌روز با ریموت | «My fork is up to date.» |
| **out of sync** | ناهماهنگ با ریموت | «Your branch is out of sync with main.» |
| **pull in changes** | تغییرات را کشیدن | «Pull in the latest changes first.» |
| **rebase on top of** | ری‌بیس روی | «Rebase on top of main.» |
| **fast-forward** | ادغام خطی بدون کامیت merge | «The merge will fast-forward.» |
| **diverged** | دو شاخه از هم جدا افتاده‌اند | «Our branches have diverged — merge or rebase?» |
| **stale** | قدیمی/متروک‌شده | «This PR is stale — close it?» |
| **force push (with lease)** | بازنویسی ریموت | «Force-pushed my feature branch — careful.» |
| **revert the merge** | برگرداندن اثر merge با کامیت معکوس | «We reverted the merge in prod.» |
| **cherry-pick** | برداشتن یک کامیت خاص | «Cherry-pick that fix into release/2.1.» |

## ۵.۲ — دردسرها و اصطلاحات نجات

| اصطلاح | یعنی | جمله واقعی |
|---|---|---|
| **detached HEAD** | سرگردانی روی کامیت (نه شاخه) | «You're in detached HEAD — create a branch!» |
| **lost commits** | کامیت‌های «گم‌شده» | «Don't panic — reflog finds lost commits.» |
| **dirty working tree** | تغییرات ذخیره‌نشده | «Stash your dirty tree first.» |
| **stash** | انبار موقت تغییرات | «Stash, pull, pop.» |
| **hotfix** | فیکس اضطراری روی پروداکشن | «Cut a hotfix branch now.» |
| **squash the WIP commits** | تمیزکردن کامیت‌های زشت | «Squash your WIP commits before the PR.» |
| **conflict resolution** | حل تعارض | «The conflict resolution is trivial — take ours.» |
| **take ours / take theirs** | نسخه من / نسخه او را نگه دار | «Resolve with ours for now.» |
| **green build / red build** | بیلد موفق / شکست‌خورده | «Keep the build green.» |
| **break the build** | شکستن بیلد برای همه | «Who broke the build?! 😅» |

> 🔑 مکالمه واقعی نجات (بخوان و ترجمه کن):

```text
Dev:  Help! I did a hard reset and lost three commits.
Lead: Don't panic — check the reflog. Nothing is truly lost for 90 days.
Dev:  Found them. Now what?
Lead: Create a branch from that commit and cherry-pick onto your PR.
```

ترجمه روان: «ریست سخت زدم و سه کامیت گم شد!» → «پنیک نکن — reflog را چک کن؛ ۹۰ روز هیچی واقعاً گم نمی‌شه» → «پیدا شد» → «از اون کامیت شاخه بساز و cherry-pick کن روی PR‌ت.»

## ۵.۳ — اصطلاحات README و contribution

| اصطلاح | یعنی |
|---|---|
| **contribution guidelines** | قوانین مشارکت در پروژه |
| **fork / upstream** | کپی مخزن در اکانتت / مخزن اصلی |
| **signed-off commit** | کامیت امضاشده (DCO) |
| **conventional commit** | قالب `feat:/fix:/chore:` |
| **semantic versioning (semver)** | MAJOR.MINOR.PATCH |
| **changelog** | تاریخچه تغییرات هر نسخه |
| **release notes** | توضیحات انتشار نسخه |
| **maintainer** | نگهدارنده پروژه (مسئول merge) |
| **good first issue** | ایشوی ساده برای تازه‌واردها ⭐ (برای contribution اول!) |

## ۵.۴ — جمله‌های پرکاربرد گیت در چت تیم

```text
"Pushed — please review."                     (پوش کردم — ریویو کن)
"Rebased and force-pushed. 🙏"                 (ری‌بیس و فورس‌پوش کردم)
"It'll conflict with #42 — merge that first." (با #42 تداخل داره — اول اون رو merge کن)
"Squashing now, then it's green."              (الان اسکواش می‌کنم، بعد سبک)
"Reverted the deploy commit — we're back to green."
"Sorry, broke the build — fixing now."         (بیلد رو شکستم — دارم درست می‌کنم)
"Can you re-request review? New commits up."   (دوباره درخواست ریویو کن — کامیت‌های جدید اومده)
```

---

## ✅ جمع‌بندی فصل

- شاخه‌ها: branch off، rebase on top of، diverged، out of sync، stale
- نجات: detached HEAD، reflog، dirty tree → stash، hotfix، take ours/theirs
- وضعیت بیلد: green/red — «Who broke the build?!» شوخی همیشگی
- مخزن‌بازی: fork/upstream، maintainer، good first issue، semver، changelog
- جمله‌های چت: Pushed — please review / Sorry, broke the build

## 📝 تمرین فصل ۵

1. درک: «The PR is stale and diverged — close it and cut a fresh branch off main.» یعنی چی؟
2. حالت‌سازی: همکارت می‌گوید سه کامیت WIP دارد و می‌خواهد PR باز کند. با دو اصطلاح از این فصل راهنمایی‌اش کن (انگلیسی).
3. کدام جمله گیت-صحیح‌تر است و چرا؟ (الف) «I pushed to main!» (ب) «I opened a PR targeting main.»
4. ترجمه مفهومی: «Keep the main branch green at all costs — hotfix first, cleanup later.»
5. (عملی) توی مخزن real خودت: یک PR با قالب What/Why/How/Testing باز کن و لینکش را ذخیره کن.

<details><summary>جواب‌ها</summary>

1. «PR قدیمی و متروک شده و با main واگرا افتاده — ببندش و یک شاخه تازه از main بساز.»
2. نمونه: «Rebase on main first, then squash your WIP commits into meaningful ones — reviewers shouldn't see 'wip', 'fix typo', 'wip2'.»
3. (ب) — پوش مستقیم به main در تیم‌ها ممنوع/قفل است؛ PR یعنی ریویو و checks.
4. «شاخه main را به هر قیمتی سبک نگه دار — اول hotfix، بعداً تمیزکاری.»
</details>

➡️ **فصل بعد:** ارورها و لاگ‌ها — ادبیات stack trace و دیباگ.
