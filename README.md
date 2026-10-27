# VPN Scan

**[فارسی](#فارسی) · [English](#english)**

---

## فارسی

**VPN Scan** کانفیگ‌های رایگان V2Ray را از بیش از ۱۰۰ منبع جمع می‌کند. بعد آن‌ها را با **هستهٔ واقعی** همان برنامه‌ای که استفاده می‌کنی تست می‌کند. سرورهای سالم را با یک دکمه به **v2rayNG**، **V2Box**، **Hiddify** یا **NPV Tunnel** می‌فرستد.

### 📥 دانلود
آخرین نسخه را از بخش [Releases](../../releases/latest) دانلود کن (فایل `VPN-Scan.apk`).
اندروید ۸ به بالا لازم است. هسته‌های Xray 25 و sing-box فقط روی گوشی‌های ۶۴ بیتی کار می‌کنند، یعنی تقریباً همهٔ گوشی‌های امروزی.

### ✨ امکانات

**🧪 تست با سه هسته**

| هسته | نسخه | برای برنامهٔ |
|---|---|---|
| Xray | 26.10.21 | v2rayNG · V2Box |
| Xray | 25.10.15 | NPV Tunnel |
| sing-box | 1.14.4 | Hiddify |

- یکی، چندتا یا هر سه هسته را می‌شود انتخاب کرد (گزینهٔ «همه»).
- زیر هر سرور معلوم است با کدام برنامه سالم بوده: ✓ سالم، خط‌خورده یعنی وصل نشد، «—» یعنی آن هسته این نوع کانفیگ را پشتیبانی نمی‌کند.
- تست واقعی است: دو درخواست واقعی از داخل خود کانفیگ فرستاده می‌شود، نه فقط پینگ.

**➕ افزودن به برنامه‌ها**
- چهار دکمه: v2rayNG، V2Box، Hiddify و NPV Tunnel.
- هر دکمه فقط سرورهایی را می‌فرستد که با هستهٔ همان برنامه سالم بوده‌اند. تعدادشان روی دکمه نوشته شده.
- v2rayNG کانفیگ‌ها را مستقیم می‌گیرد. برای بقیه، لینک‌ها کپی می‌شوند و برنامه باز می‌شود؛ آنجا «افزودن از کلیپ‌بورد» را بزن.
- نام سرورهای سالم به شکل R.S 1، R.S 2 و … شماره‌گذاری می‌شود و پرچم کشور سرور کنارش می‌آید (🇩🇪 R.S 1). سرورهای پشت CDN علامت ☁️ می‌گیرند.

**📦 خروجی ساب**
- همهٔ سرورهای سالم هر برنامه یک‌جا: کپی ساب (Base64)، کپی لینک‌ها یا ذخیرهٔ فایل ساب.
- لینک ساب داخلی (`http://127.0.0.1:…`) که یک بار در v2rayNG، Hiddify، V2Box یا NPV اضافه می‌شود و با «به‌روزرسانی ساب» تازه می‌شود. این لینک فقط وقتی VPN Scan باز است کار می‌کند.

**✂️ فرگمنت TLS**
- کانفیگ‌هایی که در دست‌دادن TLS قطع می‌شوند، یک بار هم با فرگمنت تست می‌شوند.
- اگر با فرگمنت سالم شدند، علامت ✂ می‌گیرند. برای استفاده، فرگمنت را در برنامهٔ VPN روشن کن: `packets: tlshello · length: 10-20 · interval: 10-20`.

**🌍 تست باز شدن سایت‌ها**
- برای هر سرور سالم بررسی می‌شود که گوگل، یوتیوب، اینستاگرام و تلگرام باز می‌شوند یا نه.
- با فیلتر «فقط سرورهایی که باز می‌کنند» لیست، دکمه‌ها و ساب فقط همان سرورها را نشان می‌دهند.

**📝 کانفیگ‌های دستی**
- یک یا چند کانفیگ، لینک ساب یا کانال داخلی را بچسبان یا از فایل TXT بده.
- دکمهٔ «فقط همین‌ها را تست کن»، یا همراه اسکن معمولی.

**🌐 پروتکل‌ها**
VLESS (با REALITY و Vision) · VMess · Trojan · Shadowsocks · Hysteria2 · Hysteria · TUIC · AnyTLS · WireGuard · SOCKS

**📡 وضعیت اینترنت و حالت‌های اسکن**
- برنامه اپراتور، IP، موقعیت، پینگ و سرعت اینترنت را نشان می‌دهد.
- اسکن متناسب با وضعیت نت انجام می‌شود:
  - **خودکار**
  - **نت ملی:** فقط سرورهای داخل ایران.
  - **نت ضعیف**
  - **نت خوب**

**☁️ IP تمیز کلودفلر**
- اگر IP کانفیگی که پشت کلودفلر است فیلتر باشد، برنامه با IP تمیز دوباره تستش می‌کند و لینک را با همان IP می‌سازد.
- IP تمیز را خود برنامه پیدا می‌کند. فهرست IP خودت را هم می‌توانی بدهی، با چسباندن متن یا فایل TXT.

**⚙️ تنظیمات**
- تعداد سرور سالم: ۱۰، ۳۰، ۵۰ یا ۱۰۰.
- حداکثر تأخیر: زیر ۵۰۰ تا زیر ۵۰۰۰ میلی‌ثانیه.
- تعداد تست هم‌زمان.
- پینگ سریع TCP برای کنار گذاشتن سرورهای خاموش.
- منابع عمومی.
- دکمهٔ بازگشت به تنظیمات پیش‌فرض.

**🔁 و بیشتر**
- تست دوبارهٔ سالم‌ها و حذف سرورهای قطع‌شده.
- QR کد، کپی، اشتراک‌گذاری و ذخیرهٔ لیست.
- لاگ برنامه با دلیل رد شدن کانفیگ‌ها، جدا برای هر هسته.
- به‌روزرسانی از داخل برنامه با نوار پیشرفت.
- دو زبانهٔ فارسی و English.
- تم تیره، روشن (آبی کم‌رنگ) یا خودکار هم‌رنگ گوشی.

### 📖 روش استفاده
۱. برنامه را باز کن و صبر کن وضعیت اینترنت مشخص شود.
۲. هسته‌ها و پروتکل‌ها را انتخاب کن. برای سرعت بیشتر، فقط هستهٔ برنامه‌ای را که استفاده می‌کنی بزن.
۳. **شروع اسکن V2Ray** را بزن.
۴. در پایان، دکمهٔ برنامه‌ات را بزن، مثلاً «➕ Hiddify».

### ⚠️ نکته‌ها
- کانفیگ‌ها از منابع عمومی‌اند و هر لحظه ممکن است قطع شوند. هر چند وقت یک‌بار «تست دوباره» بزن.
- با «همه» هر کانفیگ با سه هسته تست می‌شود، پس اسکن کندتر است.
- VLESS و Trojan بدون TLS در هستهٔ جدید Xray (و v2rayNG جدید) کار نمی‌کنند. ولی با NPV Tunnel و Hiddify ممکن است کار کنند.

---

## English

**VPN Scan** collects free V2Ray configs from 100+ sources. It tests each one with the **real core** used by your VPN app. Working servers go to **v2rayNG**, **V2Box**, **Hiddify** or **NPV Tunnel** with one tap.

### 📥 Download
Get the latest `VPN-Scan.apk` from [Releases](../../releases/latest).
Requires Android 8+. The Xray 25 and sing-box cores run only on 64-bit phones, which covers almost every modern phone.

### ✨ Features

**🧪 Tests with three cores**

| Core | Version | Used by |
|---|---|---|
| Xray | 26.10.21 | v2rayNG · V2Box |
| Xray | 25.10.15 | NPV Tunnel |
| sing-box | 1.14.4 | Hiddify |

- Pick one core, several, or **All**.
- Each server shows which apps it works in: ✓ works, struck through = failed, "—" = that core doesn't support this config type.
- Each test sends two real requests through the config itself, not just a ping.

**➕ Add to your app**
- Four buttons: v2rayNG, V2Box, Hiddify and NPV Tunnel.
- Each button sends only the servers that passed that app's core, and shows how many there are.
- v2rayNG imports the configs directly. For the other apps, the links are copied and the app opens; tap "Add from clipboard" there.
- Working servers are numbered R.S 1, R.S 2, … with the server's country flag (🇩🇪 R.S 1). Servers behind a CDN get ☁️.

**📦 Subscription export**
- All working servers for each app in one place: copy as a Base64 subscription, copy the links, or save a subscription file.
- A local subscription link (`http://127.0.0.1:…`) you add once to v2rayNG, Hiddify, V2Box or NPV and refresh with "Update subscription". It only works while VPN Scan is open.

**✂️ TLS fragment**
- Configs that fail the TLS handshake are retested once with fragmentation.
- If they pass, they get a ✂ mark. To use them, turn on fragment in your VPN app: `packets: tlshello · length: 10-20 · interval: 10-20`.

**🌍 Site access test**
- Each working server is checked for Google, YouTube, Instagram and Telegram.
- The "Only servers that open" filter limits the list, the buttons and the subscription to those servers.

**📝 Manual configs**
- Paste one or more configs, subscription links or domestic channels, or load a TXT file.
- Use "Test only these", or include them in normal scans.

**🌐 Protocols**
VLESS (incl. REALITY & Vision) · VMess · Trojan · Shadowsocks · Hysteria2 · Hysteria · TUIC · AnyTLS · WireGuard · SOCKS

**📡 Network status & scan modes**
- The app shows your operator, IP, location, ping and speed.
- The scan adapts to your network:
  - **Auto**
  - **National network:** Iranian servers only.
  - **Weak**
  - **Good**

**☁️ Clean Cloudflare IPs**
- If a Cloudflare-fronted config's IP is filtered, the app retests it through a clean IP and rewrites the link to use that IP.
- The app finds clean IPs automatically. You can also give it your own list, by pasting it or loading a TXT file.

**⚙️ Settings**
- Number of working servers: 10, 30, 50 or 100.
- Maximum delay: under 500 to under 5000 ms.
- Number of concurrent tests.
- Fast TCP pre-check to skip dead servers.
- Public sources.
- One-tap reset to defaults.

**🔁 More**
- Retest working servers and drop the dead ones.
- QR code, copy, share and save the list.
- App log with the reasons configs were rejected, per core.
- In-app updates with a progress bar.
- Persian and English.
- Dark, light (pale blue) or automatic theme that follows the phone.

### 📖 How to use
1. Open the app and wait for the network status to load.
2. Choose cores and protocols. For a faster scan, select only your app's core.
3. Tap **Start V2Ray scan**.
4. When it finishes, tap your app's button, e.g. "➕ Hiddify".

### ⚠️ Notes
- Configs come from public sources and can stop working at any time. Use "Retest" now and then.
- Testing with **All** cores is slower, because each config is tested three times.
- VLESS/Trojan configs without TLS don't work in the new Xray core (or recent v2rayNG). They may still work in NPV Tunnel and Hiddify.

---

Country data: GeoLite2 by MaxMind (CC BY-SA 4.0), via the v2fly geoip list bundled with Xray.

Made by **R.S** · [RS01RS](https://github.com/RS01RS)
