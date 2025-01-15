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

## Authentication

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



## HMAC and RSA

If you are not passing cardholder data through the API, you only need the session key to authenticate and connect to your account.  Otherwise, you need to use a signature secured by an HMAC secret and and encrypt the cardholder data using our RSA certificate.

{% hint style="warning" %}
If you have your own PCI compliant program and want to handle cardholder data using our API, you'll need to supplement the authentication header with the HMAC secret and you'll need to use our RSA certificate to encrypt cardholder data.
{% endhint %}

### HMAC header

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

### RSA encryption

When the API traffic originates from unknown networks or mobile devices, we also mandate that any credit card numbers be encrypted prior to building your request. You can download our RSA 2048 certificate and use the public key to encrypt the cardholder information.&#x20;

{% hint style="info" %}
When passing cardholder data through our APIs, only the credit card number needs to be encrypted using RSA, the expiration date and CVV can be left as is.\\
{% endhint %}

Examples of RSA encrypotion:

{% tabs %}
{% tab title="C#" %}
{% code overflow="wrap" %}
```csharp
using System.Security.Cryptography;
using System.Security.Cryptography.X509Certificates;
using System.Text;

// Example card number to encrypt
string myCardNumber = "4111111111111111";

X509Store store = new X509Store(StoreName.My, StoreLocation.LocalMachine);
X509Certificate2? myCert = null;

store.Open(OpenFlags.ReadOnly);
bool certFound = false;

// Search for cert within store either by thumbprint or subject 
foreach (X509Certificate2 cert in store.Certificates)
{
  if (cert.Subject.Contains("mobile.easypay5.com"))
  {
    myCert = cert;
    certFound = true;
    break;
  }
}

if (!certFound || myCert == null)
{
  MessageBox.Show("Unable to find the certificate");
  return;
}

byte[] plainBytes = Encoding.UTF8.GetBytes(myCardNumber);
RSA? rsaPublicKey = myCert.GetRSAPublicKey();

if (rsaPublicKey == null)
{
  MessageBox.Show("Unable to get RSA public key from the certificate");
  return;
}

// Use the OaepSHA1 RSA encryption padding
byte[] encryptedBytes = rsaPublicKey.Encrypt(plainBytes, RSAEncryptionPadding.OaepSHA1);

// Convert to Base64 before sending to the API
string encryptedString = Convert.ToBase64String(encryptedBytes);

// Example payload for the API
string jsonPayload = $@"
{{
    ""ccCardInfo"": {{
        ""AccountNumber"": ""{encryptedString}"",
        ""ExpMonth"": 10,
        ""ExpYear"": 2028,
        ""CSV"": ""122""
    }}
}}";

```
{% endcode %}
{% endtab %}

{% tab title="JavaScript (Node.js)" %}
{% code overflow="wrap" %}
```javascript
const crypto = require("crypto");
const fs = require("fs");

var myCardNumber = "4761530001111118";

try {
  const publicKey = Buffer.from(
    fs.readFileSync("mobile.easypay5.com.pem", { encoding: "utf-8" })
  );

  const encryptedData = crypto.publicEncrypt({
      key: publicKey,
      padding: crypto.constants.RSA_PKCS1_OAEP_PADDING,
      oaepHash: 'sha1',
    },
    Buffer.from(myCardNumber) // Convert the string to a buffer
  );

  const encryptedString = encryptedData.toString("base64");
}
catch (error) {
  console.error("Error encrypting card data:", error);
}

```
{% endcode %}
{% endtab %}
{% endtabs %}





***



## Lockouts

When you authenticate, you will receive `FunctionOK` and `AuthSuccess` flags in the response. You should handle the response as follows:

1. Check the FunctionOK flag.
   1. If false, read the `ErrMsg` and `ErrCode`, and abort.
   2. If true, read the `AuthSuccess` flag.
      1. If `AuthSuccess` is false, read `RspMsg` and abort.
      2. If `AuthSuccess` is true, save the `SessKey` value.

Once again, it's important to abort unsuccessful authentication attempts and notify the user that new credentials need to be applied to the product.&#x20;

The system will lock your IP after 6 unsuccessful attempts in a row. When a lockout occurs, our support department will need to manually audit it to determine if it's safe to remove the lock.&#x20;



***



## Token Renewal

The Client Admin Portal will allow you to create and manage all of your tokens.  There is no limit to the number of tokens you can create. We recommend creating a separate token for each individual processing location (IP address).

Each token has a lifespan of 6 months since it was generated and will need to be replaced afterwards. This can only be done by physically logging into The Client Admin Portal. To make the process faster, The Client Admin Portal provides a way to POST new tokens to your web server to help automate a part of the renewal process.





