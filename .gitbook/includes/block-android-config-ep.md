---
title: block - android config ep
---

Configure the `EasyPay` class at the very beginning of the application lifecycle, e.g. in the main Application class (in the `onCreate()` method).

```kotlin
class MainApplication : Application() {
    override fun onCreate() {
        super.onCreate()
        EasyPay.init(applicationContext, "YOUR_API_KEY", "YOUR_HMAC_SECRET", "SENTRY_DSN")
    }
}
```
