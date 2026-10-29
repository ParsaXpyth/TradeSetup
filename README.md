# TradeSetup — نسخهٔ سازگارتر با شبکه‌های ایران
# TradeSetup — Iran Network Compatibility Notes

## فارسی

### معرفی
این راهنما تغییرات نسخهٔ سازگارتر TradeSetup با شرایط ناپایدار شبکه را توضیح می‌دهد. این تغییرات تضمین نمی‌کنند که سایت روی همهٔ اپراتورها و شبکه‌های ایران کار کند؛ دسترسی به سرویس‌های خارجی همچنان به وضعیت شبکه بستگی دارد.

### فایل‌های بسته
- `TradeSetup-upgraded-iran-compatible.html` — فایل اصلی صفحه.
- `sw.js` — سرویس‌ورکر برای ذخیرهٔ پوستهٔ استاتیک سایت.
- `iran-network-compatibility.md` — توضیحات فنی تغییرات سازگاری شبکه.
- `README.md` — همین راهنمای فارسی و انگلیسی.

### تغییرات اصلی
- حذف وابستگی مستقیم به Google Fonts و استفاده از فونت‌های محلی/سیستمی.
- مهلت زمانی برای درخواست داده‌های بازار و یک بار تلاش مجدد برای خطاهای موقت، timeout و خطاهای سرور 5xx.
- اعتبارسنجی اولیهٔ داده‌های بازار.
- ذخیرهٔ بهترین‌تلاشِ آخرین پاسخ معتبر در `localStorage` با کلید `ts-market-cache-v1` و امکان نمایش دادهٔ ذخیره‌شده هنگام قطعی.
- مدیریت وضعیت آفلاین و اتصال مجدد.
- بارگذاری TradingView فقط در صورت نیاز، همراه با timeout و پیام جایگزین.
- مدیریت خطا برای API اخبار؛ اگر API تنظیم نشده باشد، پیوندی به صفحهٔ اخبار فوری ارزدیجیتال نمایش داده می‌شود.
- سرویس‌ورکر برای ذخیرهٔ فایل‌های استاتیک هم‌مبدأ؛ پاسخ‌های API خارجی را ذخیره نمی‌کند.

### استقرار در GitHub Pages
1. از فایل HTML یک کپی به نام `index.html` تهیه کنید.
2. فایل `index.html` و فایل `sw.js` را در پوشهٔ ریشهٔ مخزن قرار دهید.
3. تغییرات را commit و push کنید.
4. در تنظیمات مخزن، GitHub Pages را برای شاخه و پوشهٔ موردنظر فعال کنید.
5. سایت را در مرورگر باز کنید و درخواست‌های شبکه و کنسول را بررسی کنید.

سرویس‌ورکر معمولاً پس از اولین بازدید موفق آنلاین می‌تواند پوستهٔ سایت را برای بازدیدهای بعدی ذخیره کند. مسیر استقرار و محدودهٔ سرویس‌ورکر را بررسی کنید تا با مسیر سایت در GitHub Pages مطابقت داشته باشد.

### محدودیت‌ها
- پاسخ‌های API خارجی از طریق سرویس‌ورکر cache نمی‌شوند.
- داده‌های بازار ذخیره‌شده ممکن است قدیمی باشند؛ نشانگر تازگی را بررسی کنید.
- بارگذاری TradingView، APIهای بازار و اخبار همچنان به دسترسی شبکه و در دسترس بودن سرویس‌های مربوطه وابسته است.
- سازگاری با تمام اپراتورها، ISPها یا شرایط فیلترینگ آزمایش و تضمین نشده است.
- این بسته به‌خودی‌خود به GitHub ارسال یا در مخزن commit نشده است.
- در این بسته مجوز نرم‌افزاری (license) مشخصی تعریف نشده است.

### وضعیت بررسی
طبق بررسی قبلی، ۲۰ آزمون و بررسی ایستای کد موفق گزارش شده بود. آزمون واقعی در مرورگر و روی اپراتورها/ISPهای مختلف انجام نشده است.

---

## English

### Overview
This guide describes a TradeSetup variant with improved network-error handling and fewer external dependencies. These changes do not guarantee availability on every Iranian carrier or network; access to external services still depends on network conditions.

### Package files
- `TradeSetup-upgraded-iran-compatible.html` — main page.
- `sw.js` — service worker for caching the same-origin static shell.
- `iran-network-compatibility.md` — technical notes about the compatibility changes.
- `README.md` — this bilingual guide.

### Main changes
- Removed the direct Google Fonts dependency and uses local/system font fallbacks.
- Market requests have a timeout and one retry for transient failures, timeouts, and server-side 5xx errors.
- Basic validation of market data.
- Best-effort caching of the last valid response in `localStorage` under `ts-market-cache-v1`, allowing saved data to be shown during outages.
- Offline and reconnect handling.
- Loads TradingView on demand, with a timeout and fallback messaging.
- Handles news API errors; when no API is configured, it provides a link to the ArzDigital breaking-news page.
- The service worker caches the same-origin static shell and does not cache external API responses.

### Deploying to GitHub Pages
1. Copy or rename the HTML file to `index.html`.
2. Put `index.html` and `sw.js` in the repository root.
3. Commit and push the changes.
4. Enable GitHub Pages for the desired branch and directory in repository settings.
5. Open the site and inspect network requests and the browser console.

The service worker generally needs a successful online visit before it can cache the site shell for later visits. Check the deployment path and service-worker scope against the repository's GitHub Pages URL.

### Limitations
- External API responses are not cached by the service worker.
- Cached market data may be stale; check its freshness indicator.
- TradingView, market APIs, and news services still depend on network access and service availability.
- Compatibility with every carrier, ISP, or filtering condition has not been tested or guaranteed.
- This package has not itself been pushed or committed to GitHub.
- No software license terms are specified in this package.

### Validation status
A previous check reported 20 passing tests and successful static checks. Real-browser testing and testing across different carriers/ISPs were not performed.
