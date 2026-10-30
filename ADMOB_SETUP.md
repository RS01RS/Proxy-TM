# فعال کردن تبلیغات (AdMob)

برنامه بدون تبلیغ هم کامل کار می‌کند. وقتی حساب AdMob داشتی، این مراحل را انجام بده. (AdMob به کتابخانهٔ AndroidX و یک حساب نیاز دارد؛ برای حساب ایرانی معمولاً باید روش پرداخت خارج از ایران داشته باشی.)

## ۱. حساب و شناسه‌ها
- در https://admob.google.com یک برنامه و دو «واحد تبلیغ» بساز: یکی **Banner**، یکی **Interstitial**.
- سه شناسه می‌گیری: App ID، Banner unit ID، Interstitial unit ID.
- برای تست بدون حساب، شناسه‌های تستی رسمی گوگل:
  - App ID: `ca-app-pub-3940256099942544~3347511713`
  - Banner: `ca-app-pub-3940256099942544/6300978111`
  - Interstitial: `ca-app-pub-3940256099942544/1033173712`

## ۲. گرِیدل
در `app/build.gradle`، داخل `dependencies { ... }` این را اضافه کن:
```gradle
    implementation 'com.google.android.gms:play-services-ads:23.6.0'
```
و در فایل `gradle.properties` ریشه این دو خط را بگذار (AdMob به AndroidX نیاز دارد):
```
android.useAndroidX=true
android.enableJetifier=true
```

## ۳. مانیفست
در `app/src/main/AndroidManifest.xml`، داخل `<application>` این را اضافه کن (App ID خودت):
```xml
        <meta-data
            android:name="com.google.android.gms.ads.APPLICATION_ID"
            android:value="ca-app-pub-xxxxxxxxxxxxxxxx~yyyyyyyyyy" />
```

## ۴. فایل AdHook.java
فایل `app/src/main/java/.../AdHook.java` را با نسخهٔ زیر جایگزین کن (Banner و Interstitial خودت را بگذار). پل برنامه از قبل این سه متد را صدا می‌زند: `AdHook.banner`، `AdHook.interstitial`، `AdHook.AVAILABLE`.

```java
package com.rs.proxy;

import android.app.Activity;
import android.view.Gravity;
import android.view.ViewGroup;
import android.widget.FrameLayout;
import com.google.android.gms.ads.*;
import com.google.android.gms.ads.interstitial.*;

final class AdHook {
    static final boolean AVAILABLE = true;
    private static final String BANNER = "ca-app-pub-3940256099942544/6300978111";       // ← بنر خودت
    private static final String INTER  = "ca-app-pub-3940256099942544/1033173712";        // ← تمام‌صفحهٔ خودت
    private static boolean inited;
    private static AdView bannerView;
    private static InterstitialAd interstitial;
    private AdHook() { }

    private static void init(Activity a) {
        if (inited) return; inited = true;
        MobileAds.initialize(a, s -> { });
        loadInter(a);
    }
    static void banner(Activity a, boolean on) {
        a.runOnUiThread(() -> {
            init(a);
            if (!on) { if (bannerView != null) bannerView.setVisibility(android.view.View.GONE); return; }
            if (bannerView == null) {
                bannerView = new AdView(a);
                bannerView.setAdUnitId(BANNER);
                bannerView.setAdSize(AdSize.BANNER);
                FrameLayout.LayoutParams lp = new FrameLayout.LayoutParams(
                        ViewGroup.LayoutParams.MATCH_PARENT, ViewGroup.LayoutParams.WRAP_CONTENT, Gravity.BOTTOM);
                a.addContentView(bannerView, lp);
                bannerView.loadAd(new AdRequest.Builder().build());
            }
            bannerView.setVisibility(android.view.View.VISIBLE);
        });
    }
    private static void loadInter(Activity a) {
        InterstitialAd.load(a, INTER, new AdRequest.Builder().build(), new InterstitialAdLoadCallback() {
            public void onAdLoaded(InterstitialAd ad) { interstitial = ad; }
            public void onAdFailedToLoad(LoadAdError e) { interstitial = null; }
        });
    }
    static void interstitial(Activity a) {
        a.runOnUiThread(() -> {
            init(a);
            if (interstitial != null) { interstitial.show(a); interstitial = null; loadInter(a); }
        });
    }
}
```

همین. برنامه خودش بنر را پایین صفحه نشان می‌دهد و بعد از هر اسکن (با فاصلهٔ حداقل ۳ دقیقه) یک تبلیغ تمام‌صفحهٔ قابل‌بستن نشان می‌دهد. در نت ملی (بدون اینترنت بین‌الملل) تبلیغ خودکار مخفی می‌شود.

> نکتهٔ گوگل پلی: تبلیغ تمام‌صفحه نباید سر بزنگاه (وسط کار کاربر) بیاید و باید قابل بستن باشد. کد بالا فقط بعد از پایان اسکن نشان می‌دهد، که مجاز است.
