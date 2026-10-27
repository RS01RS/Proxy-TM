
# TM Proxy

**Made by (R.S)**

پیدا کردن و تست واقعی پروکسی‌های تلگرام — فقط پروکسی‌هایی که خود سرور تلگرام از داخلشان جواب بدهد

[فارسی](#فارسی) · [English](#english)

[![Download APK](https://img.shields.io/badge/Download-TM--Proxy.apk-1f5eff?style=for-the-badge)](../../releases/latest/download/TM-Proxy.apk)

</div>


---

<div dir="rtl" id="فارسی">


## فارسی

### فهرست

- [معرفی](#معرفی)
- [تأیید از خود تلگرام](#تأیید-از-خود-تلگرام)
- [امکانات](#امکانات)
- [نصب و شروع](#نصب-و-شروع)
- [اسکن چطور انجام می‌شود](#اسکن-چطور-انجام-میشود)
- [تنظیمات](#تنظیمات)
- [لیست، فیلترها و نشان‌ها](#لیست-فیلترها-و-نشانها)
- [اتصال هوشمند و اعلان قطعی](#اتصال-هوشمند-و-اعلان-قطعی)
- [پروکسی دستی و نت ملی](#پروکسی-دستی-و-نت-ملی)
- [خروجی و اشتراک گروهی](#خروجی-و-اشتراک-گروهی)
- [مجوزها و حریم خصوصی](#مجوزها-و-حریم-خصوصی)
- [سؤال‌های رایج](#سؤالهای-رایج)

### معرفی

**TM Proxy** آخرین پروکسی‌های تلگرام را از حدود ۱۰۰ منبع جمع می‌کند (گیت‌هاب، سایت‌ها، کانال‌های تلگرام، بله و ایتا)، همه را تست می‌کند و فقط آن‌هایی را **سالم** نشان می‌دهد که واقعاً به تلگرام وصل می‌شوند. اتصال با یک لمس انجام می‌شود و پروکسی درست قبل از اتصال دوباره بررسی می‌شود.

### تأیید از خود تلگرام

پروکسی فقط وقتی سالم حساب می‌شود که برنامه از داخل آن یک درخواست واقعی تلگرام (`req_pq_multi`) بفرستد و **سرور تلگرام** جواب درست (`resPQ` با همان nonce) بدهد. پروکسی‌ای که فقط ادعای اتصال کند سالم حساب نمی‌شود.

| نوع | تست |
|---|---|
| **FakeTLS** (secret با `ee`) | دست‌دادن کامل TLS و بررسی secret، بعد جواب تلگرام |
| **dd** | لایهٔ obfuscated2 با secret، بعد جواب تلگرام |
| **کلاسیک** | لایهٔ obfuscated2 با secret، بعد جواب تلگرام |
| **SOCKS5** | CONNECT به سرور تلگرام، بعد جواب تلگرام |
| **WEB Proxy** | فقط بالا بودن سایت HTTPS؛ secret این نوع را فقط خود تلگرام می‌سنجد، پس هیچ‌وقت «سالم» نشان داده نمی‌شود |

**وضعیت‌ها:** 🟢 **سالم**: تلگرام از داخل پروکسی جواب داده و پینگ زیر حد است · 🟡 **مشکوک**: پروکسی جواب می‌دهد ولی تلگرام نه، پینگ از حد بیشتر است، یا وب پروکسی است · 🔴 **قطع**: جواب نمی‌دهد، secret اشتباه است یا رد می‌شود.

### امکانات

- **تست واقعی** همهٔ انواع: FakeTLS، dd، کلاسیک، SOCKS5 و WEB
- **اولویت FakeTLS:** پیش‌فرض فقط FakeTLS (مقاوم‌ترین نوع در ایران)؛ در هر حالت FakeTLSها اول تست می‌شوند و دامنهٔ پوششی‌شان کنارشان نوشته می‌شود
- **پرچم کشور** کنار اسم: «🇩🇪 (R.S) 1»؛ ☁️ برای پروکسی‌های پشت CDN (بانک داخل برنامه، روی نت ملی هم کار می‌کند)
- **اسم‌گذاری:** پروکسی‌های سالم به ترتیب بهترین «(R.S) 1»، «(R.S) 2»، …
- **تست دوبارهٔ سالم‌ها** با یک دکمه
- **اعلان قطعی:** اگر پروکسی‌ای که به آن وصل شدی قطع شد، اعلان می‌دهد و بهترین جایگزین را می‌گوید
- **پایداری و علاقه‌مندی:** درصد پایداری روی هر اپراتور، نشان «پایدار»، ستاره برای علاقه‌مندی‌ها
- **پروکسی دستی:** چسباندن یا فایل TXT، با دکمهٔ «فقط همین‌ها را تست کن»
- **منابع داخلی** بله، ایتا و روبیکا برای نت ملی (منبع خودت را هم اضافه کن)
- **اشتراک گروهی:** QR تک‌تک، پیام آماده با اسم و پرچم، صفحهٔ HTML
- **اسکن خودکار** هر ۱۰ دقیقه تا ۱۲ ساعت و اتصال خودکار به بهترین
- وضعیت اینترنت: IP، اپراتور، موقعیت، ISP، پینگ و سرعت
- خروجی TXT / CSV، QR بهترین پروکسی، کپی همه
- به‌روزرسانی از داخل برنامه · فارسی و English · تم تیره، روشن (آبی کم‌رنگ) یا خودکار

### نصب و شروع

1. فایل [TM-Proxy.apk](../../releases/latest/download/TM-Proxy.apk) را دانلود کن، نصب از منابع ناشناس را اجازه بده و نصبش کن (اندروید ۸ به بالا).
2. صبر کن وضعیت اینترنت مشخص شود؛ حالت را «خودکار» بگذار یا خودت انتخاب کن.
3. **شروع اسکن** را بزن.
4. روی یکی از پروکسی‌های سالم **اتصال** را بزن (یا «⚡ اتصال مستقیم به بهترین پروکسی»). تلگرام باز می‌شود؛ آنجا «Connect» را بزن.

### اسکن چطور انجام می‌شود

1. پروکسی وصل‌شدهٔ قبلی، علاقه‌مندی‌ها، پروکسی‌های دستی و حافظهٔ اسکن‌های قبلی اول اضافه می‌شوند.
2. منابع بر اساس حالت انتخاب می‌شوند: نت ملی فقط منابع داخلی؛ اینترنت ضعیف اول منابع سبک.
3. در صورت انتخاب، دامنه‌ها با DNS امن به IP تبدیل می‌شوند.
4. پروکسی‌ها مرتب می‌شوند: پروکسی وصل‌شده، علاقه‌مندی‌ها، FakeTLS، پایداری، تازگی و مقاومت.
5. حداقل ۱۰۰ پروکسی و تا رسیدن به تعداد هدف، با تست هم‌زمان، تست واقعی می‌شوند.
6. سالم‌ها و مشکوک‌ها برای قطعی ذخیره می‌شوند و سابقهٔ هر پروکسی (به تفکیک اپراتور) به‌روز می‌شود.

### تنظیمات

| تنظیم | گزینه‌ها | پیش‌فرض |
|---|---|---|
| حالت اینترنت | خودکار · نت ملی · ضعیف · خوب | خودکار |
| نوع پروکسی | MTProto · WEB · SOCKS5 · همه | MTProto |
| فقط FakeTLS | پیشنهادی برای ایران | روشن |
| آدرس سرور | دامنه · IP · هر دو | هر دو |
| تبدیل دامنه با DNS امن | در برابر DNS دستکاری‌شده | روشن |
| تعداد پروکسی سالم | ۱۰۰ · ۵۰۰ · ۱۰۰۰ · ۲۰۰۰ | ۱۰۰ |
| حداکثر پینگ | زیر ۳۰۰ · ۶۰۰ · ۱۰۰۰ · ۲۰۰۰ میلی‌ثانیه | زیر ۲۰۰۰ |
| تست هم‌زمان | ۵ · ۱۰ · ۵۰ · ۱۰۰ | ۵۰ |
| زمان اتصال و تست | ۶ · ۱۰ · ۱۵ · ۲۰ ثانیه | ۱۰ ثانیه |
| اسکن خودکار | خاموش · ۱۰ دقیقه · ۳۰ دقیقه · ۱ ساعت · ۱۲ ساعت | خاموش |
| اتصال خودکار به بهترین | بعد از اسکن | خاموش |
| 🔔 اعلان قطعی | وقتی پروکسی وصل‌شده قطع شد | روشن |
| اپراتور | خودکار یا دستی (برای سابقهٔ جدا) | خودکار |

### لیست، فیلترها و نشان‌ها

- زبانه‌ها: **سالم**، **مشکوک**، **قطع**، **همه**، **★ علاقه‌مندی**
- جست‌وجوی IP یا دامنه؛ فیلتر نوع (FakeTLS، dd، کلاسیک، WEB، SOCKS5)؛ فقط پورت ۴۴۳؛ فقط ایران؛ فقط مقاوم؛ فقط تازه
- مرتب‌سازی: بهترین (پایداری + پینگ)، کمترین پینگ، بیشترین پایداری، مقاوم‌ترین
- نشان‌ها: **مقاوم** (امتیاز مقاومت ۵ از ۷ به بالا)، **تازه** (کمتر از ۲۴ ساعت)، **پایدار** (حداقل ۳ تست و ۸۰٪ سالم)، **IR** (سرور داخل ایران)
- با لمس هر پروکسی: QR، کشور، نوع، دامنهٔ پوششی، امتیاز مقاومت، سابقه به تفکیک اپراتور، اولین و آخرین تست

### اتصال هوشمند و اعلان قطعی

- قبل از اتصال، پروکسی یک بار سریع تست می‌شود؛ اگر جواب نداد، خودکار سراغ بهترین بعدی می‌رود (تا ۴ پروکسی).
- برنامه پروکسی‌ای را که از داخلش به آن وصل شدی یادش می‌ماند و در هر اسکن اول آن را تست می‌کند.
- اگر در **تست دوباره** یا **اسکن خودکار** قطع باشد، اعلان می‌دهد و بهترین جایگزین را می‌گوید (حداکثر هر نیم ساعت یک اعلان). بار اول اندروید اجازهٔ اعلان می‌خواهد.
- «➕ افزودن ۵ پروکسی برتر» پنج پروکسی را پشت هم به تلگرام اضافه می‌کند تا اگر یکی قطع شد سریع سراغ بعدی بروی.

### پروکسی دستی و نت ملی

- در **وارد کردن پروکسی دستی** لینک‌های `tg://proxy`، `t.me/proxy` یا `tg://socks` را بچسبان یا فایل TXT بده؛ تعدادشان نشان داده می‌شود. **🧪 فقط همین‌ها را تست کن** فقط همان‌ها را تست می‌کند.
- در **منابع داخلی برای نت ملی** هر خط یکی: `eitaa:اسم‌کانال`، `bale:اسم‌کانال`، `rubika:اسم‌کانال` یا آدرس کامل یک صفحه. اگر سرور داخلی داری، آدرس واسطه‌اش را هم می‌شود گذاشت.
- در نت ملی فقط منابع داخلی، حافظهٔ ذخیره‌شده و سرورهای داخل ایران استفاده می‌شوند. یک بار با اینترنت آزاد اسکن کن تا رنج IP ایران و حافظه پر شود.

### خروجی و اشتراک گروهی

- فایل TXT سالم‌ها، TXT سالم + مشکوک، CSV کامل، TXT علاقه‌مندی‌ها (در پوشهٔ Download)
- QR بهترین پروکسی، کپی لینک‌های سالم، اشتراک‌گذاری (با لینک دانلود برنامه)
- **📤 اشتراک گروهی:** QR هر پروکسی با «قبلی / بعدی»، پیام آماده (همهٔ لینک‌ها با اسم، پرچم و پینگ) برای کپی یا فرستادن، و صفحهٔ HTML که دوستت با یک لمس روی هر پروکسی وصل شود

### مجوزها و حریم خصوصی

- `INTERNET`: دریافت منابع و تست پروکسی‌ها · `REQUEST_INSTALL_PACKAGES`: فقط به‌روزرسانی داخل برنامه · `POST_NOTIFICATIONS`: فقط اعلان قطعی پروکسی
- برنامه هیچ اطلاعاتی برای سازنده نمی‌فرستد. تنظیمات، نتیجه‌ها، سابقه و علاقه‌مندی‌ها فقط روی گوشی ذخیره می‌شوند.
- پروکسی‌ها مال افراد دیگرند؛ اطلاعات حساس را با احتیاط بفرست.

### سؤال‌های رایج

**در قطعی کامل کار می‌کند؟** در قطعی کامل اینترنت هیچ پروکسی‌ای کار نمی‌کند. در نت ملی شانس با پروکسی‌های داخلی بیشتر است.

**«مشکوک» یعنی چه؟** پروکسی جواب داده ولی تلگرام از داخلش جواب نداده، یا کند است. معمولاً در تلگرام کار نمی‌کند.

**اعلان نمی‌آید؟** در تنظیمات گوشی اجازهٔ اعلان TM Proxy را بده و گزینهٔ 🔔 را روشن نگه دار. اعلان فقط در «تست دوباره» یا «اسکن خودکار» بررسی می‌شود و برنامه باید باز باشد.

**آیفون؟** این برنامه فقط اندروید است.

### اعتبارها

داده‌های کشور: GeoLite2 از MaxMind (CC BY-SA 4.0) از طریق فهرست geoip پروژهٔ v2fly · QR Code for JavaScript از Kazuhiko Arase (MIT).

</div>

---

<div id="english">

## English

**TM Proxy** collects the latest Telegram proxies from about 100 sources (GitHub, websites, Telegram channels, Bale and Eitaa), tests every one, and marks as **healthy** only those that really reach Telegram. Connecting is one tap, with a quick re-check right before connecting.

### Confirmed by Telegram itself

A proxy counts as healthy only when the app sends a real Telegram request (`req_pq_multi`) through it and the **Telegram server** answers correctly (`resPQ` with the same nonce).

| Type | Test |
|---|---|
| **FakeTLS** (`ee` secret) | Full TLS handshake and secret check, then a Telegram reply |
| **dd** | obfuscated2 layer with the secret, then a Telegram reply |
| **Classic** | obfuscated2 layer with the secret, then a Telegram reply |
| **SOCKS5** | CONNECT to a Telegram server, then a Telegram reply |
| **WEB Proxy** | Only checks the HTTPS site is up; only Telegram can verify its secret, so it's never shown as healthy |

**Statuses:** 🟢 **Healthy** — Telegram replied and ping is under your limit · 🟡 **Suspicious** — the proxy answers but Telegram doesn't, ping is too high, or it's a web proxy · 🔴 **Down** — no answer, wrong secret, or rejected.

### Features

- **Real tests** for FakeTLS, dd, classic, SOCKS5 and WEB proxies
- **FakeTLS first:** FakeTLS-only by default (most filter-resistant in Iran); FakeTLS is always tested first and its cover domain is shown
- **Country flags:** "🇩🇪 (R.S) 1"; ☁️ for CDN proxies (bundled database, works on the national internet)
- **Naming:** working proxies are named (R.S) 1, (R.S) 2, … by quality
- **Retest working proxies** with one tap
- **Down alert:** if the proxy you connected to goes down, you get a notification with the best replacement
- **Stability and favorites:** per-operator stability, a "stable" badge, starred favorites
- **Manual proxies:** paste or load a TXT file, with "Test only these"
- **Domestic sources** (Bale, Eitaa, Rubika) for the national internet; add your own
- **Group share:** QR per proxy, ready message with names and flags, HTML page
- **Auto-scan** every 10 minutes to 12 hours, and auto-connect to the best proxy
- Network status: IP, operator, location, ISP, ping and speed
- TXT / CSV export, QR for the best proxy, copy all
- In-app updates · Persian and English · dark, light (pale blue) or automatic theme

### Getting started

1. Download [TM-Proxy.apk](../../releases/latest/download/TM-Proxy.apk), allow unknown sources and install (Android 8+).
2. Wait for the network status; leave the mode on Auto or choose one.
3. Tap **Start scan**.
4. Tap **Connect** on a healthy proxy (or "⚡ Connect directly to the best proxy"), then "Connect" in Telegram.

### How scanning works

1. Your last connected proxy, favorites, manual proxies and saved results are added first.
2. Sources are chosen by mode: national = domestic only; weak = light sources first.
3. Optionally, domains are resolved to IPs with secure DNS.
4. Proxies are ordered: connected proxy, favorites, FakeTLS, stability, freshness, resistance.
5. At least 100 proxies, and until the target count is reached, are tested in parallel.
6. Working and suspicious proxies are cached for shutdowns, and each proxy's history (per operator) is updated.

### Settings

| Setting | Options | Default |
|---|---|---|
| Internet mode | Auto · National · Weak · Good | Auto |
| Proxy type | MTProto · WEB · SOCKS5 · All | MTProto |
| FakeTLS only | recommended for Iran | on |
| Server address | domain · IP · both | both |
| Secure-DNS resolve | against tampered DNS | on |
| Proxies to find | 100 · 500 · 1000 · 2000 | 100 |
| Max ping | under 300 · 600 · 1000 · 2000 ms | under 2000 |
| Concurrent tests | 5 · 10 · 50 · 100 | 50 |
| Connect / test time | 6 · 10 · 15 · 20 s | 10 s |
| Auto-scan | off · 10 min · 30 min · 1 h · 12 h | off |
| Auto-connect to best | after scan | off |
| 🔔 Down alert | when your connected proxy goes down | on |
| Operator | auto or manual (separate history) | auto |

### List, filters and badges

Tabs: Working, Suspicious, Down, All, ★ Favorites. Search by IP or domain; filter by type (FakeTLS, dd, Classic, WEB, SOCKS5), port 443 only, Iran only, resistant only, fresh only. Sort by best (stability + ping), lowest ping, most stable, most resistant. Badges: **resistant** (score ≥ 5 of 7), **fresh** (< 24 h), **stable** (≥ 3 tests, ≥ 80% working), **IR**. Tap a proxy for its QR, country, type, cover domain, resistance score and per-operator history.

### Smart connect and down alerts

Before connecting, the proxy is quickly re-checked; if it fails, the next best one is tried (up to 4). The app remembers the proxy you connected to and tests it first on every scan. If it's down on **retest** or **auto-scan**, you get a notification with the best replacement (at most once every 30 minutes). Android asks for notification permission the first time. "➕ Add top 5 proxies" adds five proxies to Telegram one after another.

### Manual proxies and national internet

Paste `tg://proxy`, `t.me/proxy` or `tg://socks` links, or load a TXT file; "🧪 Test only these" tests just them. Domestic sources take one per line: `eitaa:channel`, `bale:channel`, `rubika:channel` or a full URL, plus an optional relay address for your own server. On the national internet only domestic sources, the cache and Iranian servers are used; scan once on free internet to fill the Iran IP ranges and cache.

### Export and group share

TXT (working), TXT (working + suspicious), full CSV, TXT (favorites) saved to Download; QR for the best proxy; copy working links; share (with the app download link). **📤 Group share:** a QR per proxy with Prev/Next, a ready message (all links with names, flags and ping) to copy or send, and an HTML page your friend can tap to connect.

### Build from source

GitHub Actions builds the APK (`.github/workflows/build.yml`): upload `rs-apk-src.zip` (if the zip is absent, the `source/` folder is built instead — same code, unpacked so it can be read on GitHub); it builds with Java 17 and Gradle 8.9 and publishes `TM-Proxy.apk` to Releases as version `1.{run number}`. Locally: Android SDK 34, JDK 17, `gradle assembleDebug`.

Security note: the signing key (`rs-key.jks`) and its password are in the source so updates install over the previous version. Because the repository is public, anyone can sign an APK with it; keep it in GitHub Secrets if only you should publish official builds.

### Project structure

`MainActivity.java` (WebView, `window.RSNative` bridge, notifications, theme, updates) · `ProxyTester.java` (FakeTLS / dd / classic / SOCKS5 / WEB tests) · `TgProbe.java` (`req_pq_multi` to a Telegram server) · `assets/index.html` (entire UI and scan logic) · `assets/geo4.bin` (IP → country). Bridge methods: `check`, `socks`, `web`, `fetch`, `geo`, `dns`, `notifyUser`, `askNotify`, `setTheme`, `sysDark`, `startUpdate`, `installUpdate`, `copy`, `share`, `save`, `open`.

### Permissions and privacy

`INTERNET` for sources and tests; `REQUEST_INSTALL_PACKAGES` only for in-app updates; `POST_NOTIFICATIONS` only for down alerts. Nothing is sent to the developer; settings, results, history and favorites stay on the phone. Proxies are run by third parties; be careful with sensitive data.

### FAQ

- **Full shutdown?** No proxy works in a full shutdown; on the national internet domestic proxies have the best chance.
- **"Suspicious"?** The proxy answered but Telegram didn't through it, or it's slow; it usually won't work in Telegram.
- **No alert?** Allow TM Proxy notifications in Android settings and keep 🔔 on. Alerts are checked on retest or auto-scan, with the app open.
- **iPhone?** Android only.

### Credits

Country data: GeoLite2 by MaxMind (CC BY-SA 4.0) via the v2fly geoip list · QR Code for JavaScript by Kazuhiko Arase (MIT).

</div>

---

<div align="center">

**Made by (R.S)**

</div>
