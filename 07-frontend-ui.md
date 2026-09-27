# فصل ۷ — فرانت‌اند و UI/UX: زبان دیزاینرها و رابط کاربری

> 🎯 **صحنه:** دیزاینر می‌گوید «Make it pixel-perfect, add a skeleton while loading, and the tooltip shouldn't be a modal!» — ادبیات رابط کاربری که در جلسات با دیزاینرها همیشه هست.

---

## ۷.۱ — طراحی و تحویل دیزاین

| اصطلاح | تلفظ | یعنی | جمله |
|---|---|---|---|
| **wireframe** | وایر-فریم | طرح خطی اولیه (سیاه‌قلم) | «First wireframes are up.» |
| **mockup** | ماک-آپ | طرح گرافیکی نهایی‌نما | «The mockup differs from the wireframe.» |
| **prototype** | پرو-توتایپ | نمونه تعاملی (Figma) | «Try the clickable prototype.» |
| **design system** | دیزاین سیستِم | کیت اجزای تکرارشونده (رنگ/فونت/کامپوننت) | «Follow our design system.» |
| **design token** | دیزاین تُوکن | متغیرهای طراحی (رنگ/فاصله) | «Tokens live in CSS variables.» |
| **pixel-perfect** | پیکسل-پِرفِکت | مو‌به‌مو مثل طرح | «Make it pixel-perfect against the Figma.» |
| **handoff** | هند-آف | تحویل طرح به دولوپر | «Design handoff is Friday.» |
| **spec / redlines** | اسپک / رِدلاین‌ز | مشخصات دقیق (فاصله/رنگ‌ها) | «Check the redlines in Figma.» |
| **favicon** | فَوی-کُن | آیکون تب مرورگر | «Favicon is 404-ing.» |
| **responsive** | ری-اسپان-سیو | سازگار با همه اندازه‌ها | «Is it responsive on mobile?» |
| **breakpoint** | بریک-پوینت | نقطه شکست چیدمان (مثلاً 768px) | «The breakpoint hides the sidebar.» |
| **viewport** | ویو-پورت | ناحیه دید مرورگر | «It's wider than the viewport.» |
| **above the fold** | اَباو ذِ فولد | بالای فولد — بدون اسکرول دیده می‌شود | «CTA must be above the fold.» |

## ۷.۲ — اجزای رابط کاربری (UI elements)

| اصطلاح | یعنی | جمله |
|---|---|---|
| **modal** | پنجره روی‌صفحه (با قفل پس‌زمینه) | «Don't use a modal for this — a toast is enough.» |
| **toast** | اعلان کوچک گذرا گوش صفحه | «Show a success toast.» |
| **tooltip** | راهنمای شناور روی hover | «Add a tooltip for the icon.» |
| **dropdown / select** | لیست بازشو | «Country picker as a dropdown.» |
| **checkbox / radio** | تیک چندانتخابی / تک‌انتخابی | «Switch to radio buttons.» |
| **toggle / switch** | کلید روشن/خاموش | «Dark mode toggle in settings.» |
| **accordion** | آکاردئونی (باز/بسته شونده) | «FAQ as an accordion.» |
| **breadcrumb** | بردکرامب — ردپای مسیر | «Add breadcrumbs to the docs.» |
| **skeleton** | اسکلت لودینگ (خاکستری pulse) | «Show a skeleton instead of a spinner.» |
| **spinner / loader** | چرخان لودینگ | «Inline spinner on the button.» |
| **CTA (Call To Action)** | دکمه اقدام اصلی | «The CTA is invisible — bigger and green!» |
| **form validation** | اعتبارسنجی فرم | «Inline validation, not alerts.» |
| **dark mode / light mode** | حالت تاریک/روشن | «Respect the system dark mode.» |
| **empty state** | حالت خالی (لیست بی‌آیتم) | «Design the empty state — not just a blank page!» |
| **onboarding** | آشناسازی کاربر جدید | «Onboarding wizard for new users.» |

## ۷.۳ — پرفورمنس و رفتار

| اصطلاح | یعنی | جمله |
|---|---|---|
| **lazy loading** | بارگذاری تنبل (هنگام نیاز) | «Lazy-load images below the fold.» |
| **layout shift / CLS** | پرش چیدمان | «That banner causes layout shift — reserve space!» |
| **hydration** | آب‌رسانی (اتصال JS به HTML سرور) | «Hydration takes 2s on mobile.» |
| **flash of unstyled content (FOUC)** | برقِ بدون‌استایل | «We see a FOUC on slow networks.» |
| **sticky header** | هدر چسبان به اسکرول | «Sticky header with backdrop blur.» |
| **smooth scroll** | اسکرول نرم | «Smooth scroll to the section.» |
| **debounce** | تأخیردهی ورودی (سرچ) | «Debounce the search input — 300ms.» |
| **accessibility / a11y** | دسترس‌پذیری (a-eleven-y!) | «a11y: add aria labels.» |
| **cross-browser** | سازگار همه مرورگرها | «Test cross-browser — Safari is sneaky.» |
| **mobile-first** | موبایل-محور طراحی | «Design mobile-first, then desktop.» |

> 💡 **a11y** چنین خوانده می‌شود: «a-eleven-y» — چون بین a و y یازده حرف است. الگوی عددی مشابه: **i18n** (internationalization)، **l10n** (localization)، **k8s** (kubernetes) — دولوپرها حرف اول+تعداد حرف وسط+حرف آخر!

---

## ✅ جمع‌بندی فصل

- تحویل دیزاین: wireframe → mockup → prototype → handoff با spec/redlines
- شعار دیزاینر: pixel-perfect + responsive + a11y
- اجزا: modal ≠ toast ≠ tooltip؛ skeleton برای loading؛ empty state را فراموش نکن
- پرفورمنس: lazy loading، layout shift، debounce، mobile-first
- الگوی عددی: a11y / i18n / k8s

## 📝 تمرین فصل ۷

1. دیزاینر می‌گوید: «The CTA is below the fold on mobile and the hero image causes layout shift.» دو مشکل و علاج را با اصطلاحات فصل توضیح بده.
2. فرق modal، toast و tooltip؟ برای پیام «ذخیره شد ✅» کدام؟ برای «خطای فرم زیر فیلد» کدام؟
3. tلفظ/خوانش: a11y، i18n، FOUC، CTA
4. حالت‌سازی: دیزاینر صفحه لودینگ خالی گذاشته — با ۲ اصطلاح (skeleton، empty state) بازخورد بده.
5. (عملی) در پروژه‌ات یک skeleton برای یکی از لیست‌ها اضافه کن و debounce سرچ را چک کن.

<details><summary>جواب‌ها</summary>

1. (۱) CTA زیر فولد است → CTA را به above the fold ببر یا کلید میانبر بده؛ (۲) عکس hero باعث layout shift می‌شود → width/height (یا aspect-ratio) رزرو کن با next/image و priority.
2. modal = پنجره مسلط با قفل صفحه؛ toast = اعلان گذرا گوش؛ tooltip = راهنمای hover. «ذخیره شد» → toast؛ «خطای زیر فیلد» → inline validation (هیچ‌کدام از آن دو!).
3. a11y = «a-eleven-y»؛ i18n = «i-eighteen-n»؛ FOUC = حرف‌به‌حرف «فاک» یا بگو flash of unstyled content؛ CTA = حرف‌به‌حرف «سی-تی-اِی».
4. نمونه: «Instead of a blank loading screen, can we add a skeleton? And the list needs a designed empty state for first-time users — right now it's just an empty page.»
</details>

➡️ **فصل بعد:** بک‌اند و API و دیتابیس.
