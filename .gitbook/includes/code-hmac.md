---
title: code - hmac
---

{% tabs %}
{% tab title="C#" %}
{% code overflow="wrap" %}
```csharp
var sessKey = "9B9175EF556E4DDA93303132323141303035383339";
var hmacSecret = "7D55DBB3D691C9E0FDF341E4AB38C3C9";
var userId = 123;

var hash = string.Empty;
var epoch = (int)(DateTime.UtcNow - new DateTime(1970, 1, 1)).TotalSeconds;
using (var hmac = new HMACSHA256(Encoding.ASCII.GetBytes(hmacSecret)))
{
  string hashable = string.Format("{0}_{1}_{2}", sessKey, epoch, userId);
  var bytes = hmac.ComputeHash(Encoding.ASCII.GetBytes(hashable));
  hash = BitConverter.ToString(bytes).Replace("-", "");
}

var signature = string.Format("{0}_{1}_{2}_{3}", 
  sessKey, epoch, userId, hash);
```
{% endcode %}
{% endtab %}

{% tab title="Java" %}
{% code overflow="wrap" %}
```java
String sessKey = "9B9175EF556E4DDA93303132323141303035383339";
String hmacSecret = "7D55DBB3D691C9E0FDF341E4AB38C3C9"; 
String userId = "123"; 

String hash;
String epoch = Long.toString(new Date().getTime() / 1000L); 
Try {
  Mac sha256HMAC = Mac.getInstance("HmacSHA256");
  SecretKeySpec secretKey = new SecretKeySpec(
    hmacSecret.getBytes(), "HmacSHA256");
  sha256HMAC.init(secretKey);
  String hashable = sessKey + "_" + epoch + "_" + userId;
  hash = Hex.encodeHexString(sha256HMAC.doFinal(hashable.getBytes()));
} catch (NoSuchAlgorithmException | InvalidKeyException e) {
  // handle signing exceptions
}
String signature = String.join("_", sessKey, epoch, userId, hash);
```
{% endcode %}
{% endtab %}

{% tab title="JavaScript (Postman)" %}
<pre class="language-javascript" data-overflow="wrap"><code class="lang-javascript"><strong>// In the Pre-Request Script Tab in Postman:
</strong>var sessKey = '9B9175EF556E4DDA93303132323141303035383339';
var hmacSecret = '7D55DBB3D691C9E0FDF341E4AB38C3C9';
var userId = '123';

// hash sessKey, epoch, and userId with hmacSecret
var epoch = Math.floor(Date.now() / 1000);
var hash = CryptoJS.HmacSHA256(`${sessKey}_${epoch}_${userId}`, hmacSecret);
const signature = `${sessKey}_${epoch}_${userId}_${hash}`;

pm.collectionVariables.set("token", signature.toUpperCase());

// In the headers tab, create a new header with 
// the name SessKey and set the value to {{token}}
</code></pre>
{% endtab %}
{% endtabs %}
