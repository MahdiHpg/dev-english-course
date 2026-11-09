# فصل ۹ — دواپس و Production: زبان دنیای واقعی

> 🎯 **صحنه:** «Prod is down, roll back, page the on-call, and write the postmortem.» وحشتناک به نظر می‌رسد؟ نه — فقط واژه‌ها را یاد بگیر. این فصل ادبیات «دنیای واقعی» است.

---

## ۹.۱ — محیط‌ها: dev تا prod

| اصطلاح | یعنی | جمله |
|---|---|---|
| **environment (env)** | محیط اجرا | «Works in all environments?» |
| **local / dev** | سیستم خود دولوپر / محیط توسعه مشترک | «It's broken in dev already.» |
| **staging / QA** | محیط آزمایشی شبیه production | «Test it on staging first.» |
| **production (prod)** | محیط واقعی کاربران | «Don't test on prod! 😅» |
| **pre-prod / canary** | پیش از prod / نسخه آزمایشی روی درصدی از کاربران | «Canary at 5% first.» |
| **promotion** | ارتقای نسخه از یک محیط به بعدی | «Promote staging build to prod.» |

> 🔑 «It works in dev» = شوخی/شکایت همیشگی: «روی سیستم من کار می‌کند!» — و جواب حرفه‌ای: «Then it's an environment config issue.»

## ۹.۲ — استقرار (deployment)

| اصطلاح | یعنی | جمله |
|---|---|---|
| **deploy / release** | استقرار / انتشار | «Deploying to prod now.» |
| **roll out / roll back** | پیش‌بردن / برگرداندن نسخه | «Roll out gradually; roll back fast.» |
| **rollback** | بازگشت به نسخه قبلی | «Rollback took 2 minutes, pain gone.» |
| **downtime / uptime** | زمان ازکارافتادگی / در دسترس بودن | «Zero downtime deploys only.» |
| **SLA (99.9% uptime)** | توافق سطح سرویس | «The SLA promises 99.9% uptime.» |
| **blue-green / rolling deploy** | استقرار دو محیط موازی / نوبتی | «We do blue-green deploys.» |
| **feature flag (toggle)** | کلید خاموش/روشن قابلیت | «Ship it behind a feature flag.» |
| **infrastructure as code (IaC)** | زیرساخت به صورت کد (Terraform) | «All infra is IaC now.» |
| **provision** | آماده‌سازی زیرساخت | «Provision a new staging server.» |
| **scale up / scale out** | قوی‌تر کردن / بیشتر کردن ماشین‌ها | «Scale out to 5 instances.» |

## ۹.۳ — حادثه (incident): زبان اضطراری 🚨

| اصطلاح | یعنی | جمله |
|---|---|---|
| **incident / outage** | حادثه / قطعی | «Prod outage — all hands!» |
| **on-call / pager** | نوبت‌داری هشدار / پیجر | «You're on-call this week.» |
| **page someone** | هشدار زدن (بیدار کردن!) | «Page the on-call engineer.» |
| **severity (sev1/sev2)** | شدت حادثه | «This is a sev1 — payments down.» |
| **mitigation** | کاهش اثر (قبل از حل ریشه) | «Mitigation first: disable the feature.» |
| **root cause analysis (RCA)** | تحلیل ریشه‌ای | «RCA shows a missing index.» |
| **postmortem** | گزارش پس از حادثه (بدون سرزنش!) | «Postmortem doc due Friday.» |
| **blameless** | بی‌سرزنش (فرهنگ postmortem درست) | «Blameless retro — focus on process.» |
| **single point of failure (SPOF)** | نقطه خرابی واحد | «That queue is a SPOF.» |
| **status page** | صفحه وضعیت عمومی | «Update the status page!» |

> 🔑 فرهنگ واقعی: در postmortem **blameless** یعنی «بگرد دنبال فرایند خراب، نه مقصر» — «Human error» علت نیست، علامت فرایند خراب است.

## ۹.۴ — CI/CD و پایش

| اصطلاح | یعنی | جمله |
|---|---|---|
| **CI (Continuous Integration)** | یکپارچه‌سازی مداوم (تست خودکار هر push) | «CI is red — fix before merge.» |
| **CD (Continuous Delivery/Deployment)** | تحویل/استقرار مداوم | «We do CD to staging on every merge.» |
| **pipeline** | خط لوله (build→test→deploy) | «The pipeline takes 8 minutes.» |
| **artifact** | خروجی بیلد (فایل نهایی) | «Download the build artifact.» |
| **smoke test / e2e** | تست دود / تست انتها-به-انتها | «E2e suite runs nightly.» |
| **flaky test** | تست بی‌ثبات | «A flaky test breaks CI randomly.» |
| **metrics / alerting** | متریک‌ها / هشداردهی | «Alert on p95 latency.» |
| **observability** | مشاهده‌پذیری (لاگ+متریک+تریس) | «We need better observability.» |
| **p95 / latency** | صدک ۹۵ تاخیر / تاخیر | «p95 latency is 800ms — too slow.» |

> 💡 **p95** یعنی: ۹۵٪ درخواست‌ها سریع‌تر از این بودند — بهانه‌ای که میانگین (average) گول‌زننده است و صدک‌ها واقعیت را می‌گویند.

---

## ✅ جمع‌بندی فصل

- محیط‌ها: local → dev → staging/QA → prod (+canary)
- استقرار: deploy → feature flag → roll out/roll back؛ zero downtime با blue-green
- حادثه: sev1 → mitigation → RCA → blameless postmortem؛ SPOF را پیدا کن
- CI/CD: pipeline سبز؛ flaky test دشمن اعتماد؛ p95 > average

## 📝 تمرین فصل ۹

1. فرق staging و prod و چرا روی prod تست نمی‌کنیم؟
2. درک: «Sev1: checkout outage. Mitigation: feature flag off. Postmortem tomorrow — blameless.» سه جمله را ترجمه مفهومی کن.
3. حالت‌سازی: دیپلویت را دیروز منتشر کردی، ارور ۵۰۰ هزارتایی امروز. با ۳ اصطلاح (rollback، feature flag، RCA) نقشه نجات بنویس (انگلیسی).
4. چرا flaky test از باگ بدتر است؟ (به CI فکر کن)
5. معنی: p95 latency = 2s، average = 200ms. چه چیزی را نشان می‌دهد که average پنهان می‌کند؟

<details><summary>جواب‌ها</summary>

1. staging = کپی شبیه‌سازی‌شده prod با داده تستی — جایی برای شکستن امن؛ prod = داده واقعی کاربران و پول واقعی. تست روی prod = ریسک مستقیم درآمد و اعتبار.
2. «حادثه سطح ۱: چک‌اوت از کار افتاده. کاهش اثر: قابلیت را با feature flag خاموش کردیم. جلسه postmortem فردا — بی‌سرزنش.»
3. نمونه: «Rolling back to the last known-good release now. Long-term fix goes behind a feature flag. I'll start the RCA doc — root cause looks like a missing env var.»
4. چون اعتماد به CI را می‌کشد: بقیه‌ی تست‌ها را بی‌اعتبار نشان می‌دهد، تیم شروع به ignore کردن قرمزی‌ها می‌کند و باگ‌های واقعی از لای‌لای رد می‌شوند.
5. ۵٪ از درخواست‌ها بیش از ۲ ثانیه طول می‌کشند (شاید حتی ۱۰ ثانیه!) — میانگین ۲۰۰ms این دُم سنگین توزیع را پنهان می‌کند؛ تجربه‌ی بد کاربران در صدک‌های بالا است.
</details>

➡️ **فصل بعد:** معماری و اصول کدنویسی — SOLID، monolith، anti-pattern.
