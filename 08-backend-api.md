# فصل ۸ — بک‌اند، API و دیتابیس: زبان سمت سرور

> 🎯 **صحنه:** جلسه با بک‌اندکار: «Expose a REST endpoint for orders, paginate with cursor, and make sure the payload is small — we're hitting rate limits.» ادبیات سمت سرور برای فرانت‌کارها.

---

## ۸.۱ — API و ارتباط

| اصطلاح | تلفظ | یعنی | جمله |
|---|---|---|---|
| **endpoint** | اِند-پوینت | آدرس قابل فراخوانی API | «Hit the /orders endpoint.» |
| **request / response** | ری-کوِست / ری-اسپانس | درخواست / پاسخ | «The request returns 200.» |
| **payload** | پِی-لود | بدنه داده‌ی درخواست/پاسخ | «Keep the payload small.» |
| **CRUD** | کْراد | Create، Read، Update، Delete | «Expose full CRUD on products.» |
| **status code** | استِیتوس کُد | کد پاسخ (200/404/500...) | «It returns a 404 when missing.» |
| **headers** | هِدرز | سرآیندها (auth، type...) | «Pass the token in headers.» |
| **authentication / authorization** | اَو-ثِن-تی-کِیشن / اَو-ثُر-ای-زِیشن | احراز هویت (کی هستی؟) / مجوز (اجازه داری؟) | «AuthN vs AuthZ — different things!» |
| **token / session** | تُو-کِن / سِش-ن | شناسه دسترسی / نشست کاربر | «Token expired — refresh it.» |
| **rate limit** | رِیت لی-میت | سقف تعداد درخواست | «We hit the rate limit — 429s everywhere.» |
| **throttle** | ثرو-تِل | کند کردن عمدی درخواست‌ها | «Throttle the endpoint to 10 req/min.» |
| **webhook** | وب-هوک | URL که سرویس دیگر به آن خبر می‌دهد | «The payment gateway calls our webhook.» |
| **polling** | پول-ینگ | مدام پرسیدن «آماده شدی؟» | «Polling every 5s — prefer webhooks.» |
| **idempotent** | آی-دِم-پُو-تِنت | تکرارش بی‌ضرر است | «Make the webhook handler idempotent!» |
| **backward compatible** | بَک-وِرد کُم-پَت-ابل | سازگار با نسخه‌های قبلی | «Keep it backward compatible.» |
| **deprecate / sunset** | دِپ-ری-کِیت / سان-سِت | منسوخ‌کردن / تعطیلی تدریجی | «We're sunsetting v1 in Q3.» |

## ۸.۲ — دیتابیس و داده

| اصطلاح | یعنی | جمله |
|---|---|---|
| **schema** | اسکِیما | ساختار جداول/مدل‌ها | «The schema needs a migration.» |
| **migration** | مای-گری-شن | تغییر نسخه‌ای ساختار دیتابیس | «Run migrations on deploy.» |
| **seed** | سید | داده اولیه | «Seed the dev database.» |
| **query / N+1 problem** | کْوِری | پرس‌وجو / مشکل پرس‌وجوهای زنجیره‌ای | «The list page has an N+1 problem.» |
| **index** | ایندکس | نمایه جستجوی سریع | «Add an index on user_id.» |
| **normalize / denormalize** | نُر-مَل-ایز | نرمال‌سازی / عمدی تکرار برای سرعت | «We denormalized for read speed.» |
| **transaction** | ترَن-زَک-شن | بسته همه‌یا‌هیچ | «Wrap both writes in a transaction.» |
| **constraint** | کان-ستْرِینت | قید داده (unique/not null) | «A unique constraint would prevent this bug.» |
| **lookup table** | لاک-آپ تیبل | جدول مرجع (کد→عنوان) | «Move statuses to a lookup table.» |
| **backup / restore** | بَک-آپ / ری-استور | پشتیبان / بازگردانی | «Restore from last night's backup.» |
| **read replica** | رید رِپ-لی-کا | کپی فقط‌خواندنی دیتابیس | «Reads go to a replica.» |

## ۸.۳ — الگوهای رایج بک‌اند

| اصطلاح | یعنی | جمله |
|---|---|---|
| **pagination (offset / cursor)** | صفحه‌بندی | «Cursor pagination for the feed.» |
| **filtering / sorting** | فیلتر / مرتب‌سازی | «Support filtering by status.» |
| **soft delete** | حذف منطقی (deletedAt) | «Soft delete — keep the data.» |
| **audit log** | لاگ ممیزی (چه کسی چه کرد) | «Every change needs an audit log.» |
| **idempotency key** | کلید ضدتکرار | «Send an idempotency key with payments!» |
| **retry with backoff** | تلاش مجدد با فاصله فزاینده | «Retry with exponential backoff.» |
| **queue / job** | صف / کار پس‌زمینه | «Emails go to a queue.» |
| **cron / scheduled job** | کار زمان‌بندی‌شده | «A cron cleans expired tokens.» |
| **environment variable (env)** | متغیر محیطی | «Secrets live in env vars.» |
| **health check** | بررسی سلامت سرویس | «Add a /health endpoint.» |

> 🔑 دو جمله‌ای که در جلسات بک‌اند همیشه می‌شنوی:
> «**It's eventual consistency**» — یعنی «الان هنوز همه‌جا یکسان نیست؛ چند لحظه صبر کن» (مثل کش‌ها و صف‌ها).
> «**Make it idempotent**» — یعنی «طوری بساز که اگر دوباره اجرا شد، خراب نشود» (وب‌هوک‌ها دوباره می‌آیند!).

---

## ✅ جمع‌بندی فصل

- API: endpoint/payload/CRUD/status code؛ AuthN ≠ AuthZ
- محدودیت‌ها: rate limit (429)، throttle؛ webhook نیازمند handler ای **idempotent**
- دیتابیس: schema/migration/index/transaction/constraint؛ read replica
- الگوها: cursor pagination، soft delete، audit log، retry with backoff، queue
- عبارت‌های طلایی: eventual consistency / make it idempotent

## 📝 تمرین فصل ۸

1. تفاوت authentication و authorization در یک مثال؟
2. درک: «The webhook isn't idempotent, so duplicate events double-charge users.» چه خطرناکی و علاج؟
3. فرانت‌کار هستی؛ بک‌اندکار می‌گوید «Use cursor pagination, offset breaks at scale.» یعنی چه و چرا؟
4. ترجمه مفهومی: «Add a unique constraint on email, seed a lookup table for statuses, and wrap the transfer in a transaction.»
5. کدام‌یک idempotent است؟ (الف) POST /orders با ساخت سفارش جدید هر بار (ب) PUT /orders/5 با داده کامل (ج) ارسال ایمیل خوش‌آمد

<details><summary>جواب‌ها</summary>

1. Authentication = «تو کی هستی؟» (لاگین/توکن)؛ Authorization = «اجازه این کار را داری؟» (ادمین بودن برای حذف). می‌توانی authN شده باشی ولی authZ نشده باشی.
2. درخواست: دروازه پرداخت برای یک تراکنش، دوبار webhook می‌زند → چون handler idempotent نیست، دوبار شارژ! علاج: idempotency key (ذخیره پردازش‌شده‌ها و رد تکراری‌ها).
3. یعنی به جای skip/take صفحه‌بندی با offset (که در داده بزرگ کند و جابه‌جا می‌شود)، با cursor (موقعیت آخرین آیتم) ادامه بده — برای فیدها و داده حجیم پایدارتر است.
4. «روی ایمیل قید یکتا بگذار، جدول مرجع وضعیت‌ها را با داده اولیه پر کن، و انتقال را داخل یک تراکنش بپیچ.»
5. (ب) — PUT با داده کامل: تکرارش همان نتیجه را می‌دهد. (الف) هر بار سفارش جدید؛ (ج) ایمیل تکراری می‌فرستد (مگر با کلید ضدتکرار).
</details>

➡️ **فصل بعد:** دواپس و production — staging، rollback، incident.
