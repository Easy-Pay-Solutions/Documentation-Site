---
description: How to authenticate with the Number backend
coverY: 0
layout:
  cover:
    visible: false
    size: hero
  title:
    visible: true
  description:
    visible: true
  tableOfContents:
    visible: true
  outline:
    visible: true
  pagination:
    visible: true
---

# API Authentication (v2)

<figure><img src="../../../.gitbook/assets/Authentication Flow.png" alt=""><figcaption></figcaption></figure>

### Authentication

Both the REST and SOAP APIs provide their own methods for authenticating with Number. You will need to use them to receive the `Session Key`. To authenticate, you need to provide your `Account Code` and `Token`.



***



{% include "../../../.gitbook/includes/param-account-code.md" %}

***



{% include "../../../.gitbook/includes/param-token.md" %}

***



As a result of authentication, you will obtain a `Session Key`. This key is required to prove your identity when using any of the other methods provided by our backend.

**You will need to reauthenticate when one of the following two errors occurs:**&#x20;

{% hint style="danger" %}
**5030:** Expired Session Key (session key has expired after 25 hours)&#x20;
{% endhint %}

{% hint style="danger" %}
**5050:** Unauthorized Session Key (your IP has changed since you last authenticated)
{% endhint %}

The system will lock your IP out if you send 6 unsuccessful authentication attempts in a row. Always abort unsuccessful authentication attempts instead of retrying and notify the user. Only the Number support team can remove the lock from a merchant.

We recommend that you obtain and use the same `Session Key` until you receive one of those errors.



***



{% include "../../../.gitbook/includes/param-sess-key.md" %}



***



### HMAC

If you are not passing cardholder data through the API, you only need the session key to authenticate and connect to your account.&#x20;

If you have your own PCI compliant program and want to handle cardholder data using our API, you'll need to supplement the authentication header with the HMAC secret and RSA certificate.

***

{% include "../../../.gitbook/includes/param-sesskey-pci-secure.md" %}

***

This key should be passed using the same header, `SessKey`.

Examples of creating the header signature:

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



***



### Lockouts

When you authenticate, you will receive `FunctionOK` and `AuthSuccess` flags in the response. You should handle the response as follows:

1. Check the FunctionOK flag.
   1. If false, read the `ErrMsg` and `ErrCode`, and abort.
   2. If true, read the `AuthSuccess` flag.
      1. If `AuthSuccess` is false, read `RspMsg` and abort.
      2. If `AuthSuccess` is true, save the `SessKey` value.

Once again, it's important to abort unsuccessful authentication attempts and notify the user that new credentials need to be applied to the product.&#x20;

The system will lock your IP after 6 unsuccessful attempts in a row. When a lockout occurs, our support department will need to manually audit it to determine if it's safe to remove the lock.&#x20;



***



### Token Renewal

The Client Admin Portal will allow you to create and manage all of your tokens.  There is no limit to the number of tokens you can create. We recommend creating a separate token for each individual processing location (IP address).

Each token has a lifespan of 6 months since it was generated and will need to be replaced afterwards. This can only be done by physically logging into The Client Admin Portal. To make the process faster, The Client Admin Portal provides a way to POST new tokens to your web server to help automate a part of the renewal process.





