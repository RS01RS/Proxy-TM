<div align="center">

# TM Proxy

**Made by (R.S)**

[فارسی](#فارسی) · [English](#english)

[![Download APK](https://img.shields.io/badge/Download-TM--Proxy.apk-1f5eff?style=for-the-badge)](../../releases/latest/download/TM-Proxy.apk)

</div>

---

<div dir="rtl" id="فارسی">

## فارسی

**TM Proxy** آخرین پروکسی‌های تلگرام رو از ده‌ها منبع جمع می‌کنه، همه رو تست می‌کنه و فقط اون‌هایی رو **سالم** نشون می‌ده که واقعاً به تلگرام وصل می‌شن.

### تأیید از خود تلگرام

پروکسی فقط وقتی سالم حساب می‌شه که اپ از داخل اون پروکسی یه درخواست واقعی تلگرام (`req_pq_multi`) بفرسته و **سرور تلگرام** جواب درست (`resPQ` با همون nonce) بده. پروکسی‌ای که فقط ادعای اتصال کنه سالم حساب نمی‌شه.

| نوع | تست |
|---|---|
| **FakeTLS** (secret با `ee`) | handshake کامل TLS و بررسی secret، بعد جواب تلگرام |
| **dd** | لایهٔ obfuscated2 با secret، بعد جواب تلگرام |
| **کلاسیک** | لایهٔ obfuscated2 با secret، بعد جواب تلگرام |
| **SOCKS5** | CONNECT به سرور تلگرام، بعد جواب تلگرام |
| **WEB Proxy** | فقط بالا بودن سایت HTTPS. secret این نوع رو فقط خود اپ تلگرام می‌سنجه، پس هیچ‌وقت «سالم» نشون داده نمی‌شه |

### وضعیت‌ها

- 🟢 **سالم**: تلگرام از داخل پروکسی جواب داده.
- 🟡 **مشکوک**: پروکسی جواب می‌ده ولی تلگرام از طریقش جواب نداده (یا وب پروکسی).
- 🔴 **قطع**: جواب نمی‌ده، secret اشتباهه یا رد می‌شه.

### امکانات

- بیش از ۷۰ منبع (گیت‌هاب، کانال‌های تلگرام، سایت‌ها) با آینه‌ها برای وقتی که گیت‌هاب فیلتره
- سه حالت اسکن: **نت ملی**، **اینترنت ضعیف**، **اینترنت خوب**
- تعداد اسکن ۵۰ / ۱۰۰ / ۳۰۰ / ۵۰۰ و تست هم‌زمان ۵ / ۱۰ / ۵۰ / ۱۰۰
- پیش‌فرض فقط FakeTLS (در ایران مقاوم‌ترین نوع در برابر فیلترینگ)
- اتصال مستقیم به تلگرام با یک دکمه، با تست دوباره قبل از اتصال
- نمایش IP، اپراتور، پینگ و سرعت
- علاقه‌مندی‌ها، QR کد، کپی همه، خروجی TXT / CSV / HTML در پوشهٔ Download

### نصب

1. فایل [TM-Proxy.apk](../../releases/latest/download/TM-Proxy.apk) رو دانلود کن.
2. نصب از منابع ناشناس رو اجازه بده و نصبش کن.
3. **اسکن** رو بزن، بعد روی یکی از پروکسی‌های سالم **اتصال** رو بزن.

### ساخت از سورس

APK به‌صورت خودکار با GitHub Actions ساخته می‌شه. کافیه `rs-apk-src.zip` رو آپلود کنی. بعد از تیک سبز، نسخهٔ جدید در بخش Releases قرار می‌گیره.

### نکته‌ها

- در قطعی کامل اینترنت هیچ پروکسی‌ای کار نمی‌کنه. در نت ملی شانس با پروکسی‌های داخلی بیشتره.
- پروکسی‌ها مال افراد دیگه‌ان. اطلاعات حساس رو با احتیاط بفرست.

</div>

---

<div id="english">

## English

**TM Proxy** collects the latest Telegram proxies from dozens of sources, tests every one, and marks as **healthy** only the ones that really reach Telegram.

### Confirmed by Telegram itself

A proxy counts as healthy only when the app sends a real Telegram request (`req_pq_multi`) through it and the **Telegram server** answers correctly (`resPQ` with the same nonce). A proxy that only claims to be connected is never counted as healthy.

| Type | Test |
|---|---|
| **FakeTLS** (`ee` secret) | Full TLS handshake and secret check, then a Telegram reply |
| **dd** | obfuscated2 layer with the secret, then a Telegram reply |
| **Classic** | obfuscated2 layer with the secret, then a Telegram reply |
| **SOCKS5** | CONNECT to a Telegram server, then a Telegram reply |
| **WEB Proxy** | Only checks that the HTTPS site is up. Only the Telegram app can check this type's secret, so it is never shown as healthy |

### Statuses

- 🟢 **Healthy**: Telegram replied through the proxy.
- 🟡 **Suspect**: the proxy answers but Telegram did not reply through it (or it is a web proxy).
- 🔴 **Dead**: no answer, wrong secret, or rejected.

### Features

- 70+ sources (GitHub, Telegram channels, websites) with mirrors for when GitHub is filtered
- Three scan modes: **national internet**, **weak internet**, **good internet**
- Scan 50 / 100 / 300 / 500 proxies, with 5 / 10 / 50 / 100 parallel tests
- FakeTLS only by default (the type most resistant to filtering in Iran)
- One-tap connect to Telegram, with a re-check right before connecting
- Shows IP, operator, ping and speed
- Favorites, QR codes, copy all, and TXT / CSV / HTML export to the Download folder

### Install

1. Download [TM-Proxy.apk](../../releases/latest/download/TM-Proxy.apk).
2. Allow installing from unknown sources and install it.
3. Tap **Scan**, then tap **Connect** on a healthy proxy.

### Build from source

GitHub Actions builds the APK automatically. Upload `rs-apk-src.zip`, and after the green check the new version appears under Releases.

### Notes

- In a full internet shutdown no proxy can work. On the national internet, domestic proxies have a better chance.
- Proxies are run by third parties. Be careful with sensitive data.

</div>

---

<div align="center">

**Made by (R.S)**

</div>
