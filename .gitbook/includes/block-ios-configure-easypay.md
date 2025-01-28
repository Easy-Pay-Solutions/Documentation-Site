---
title: block - ios configure easypay
---

Configure `EasyPay` class. You can do that in your Payment Module or in `AppDelegate` (`didFinishLaunchingWithOptions`). Set `isProduction = true` to enable jailbroken device detection.

<pre class="language-swift"><code class="lang-swift">EasyPay.shared.configureSecrets(apiKey: "YOURAPIKEY",
<strong>                                hmacSecret: "YOURHMACSECRET",
</strong>                                sentryKey: "YOURSENTRYKEY", 
                                isProduction: Bool)
</code></pre>
