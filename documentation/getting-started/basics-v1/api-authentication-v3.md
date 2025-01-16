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

# API Authentication (v3)

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
When passing cardholder data through our APIs, only the credit card number needs to be encrypted using RSA, the expiration date and CVV can be left as is.
{% endhint %}

{% hint style="info" %}
When encrypting sensitive cardholder data, use RSA encryption padding of OaepSHA1. \
Encrypted card numbers will always have 512 bytes.
{% endhint %}

<table data-card-size="large" data-view="cards" data-full-width="false"><thead><tr><th align="center"></th><th data-hidden></th><th data-hidden></th><th data-hidden data-card-target data-type="content-ref"></th></tr></thead><tbody><tr><td align="center">mobile.easypay5.com.cer</td><td></td><td></td><td><a href="https://easypaysoftware.com/mobile.easypay5.com.cer">https://easypaysoftware.com/mobile.easypay5.com.cer</a></td></tr><tr><td align="center">mobile.easypay5.com_base64encoded.cer</td><td></td><td></td><td><a href="https://easypaysoftware.com/mobile.easypay5.com_base64encoded.cer">https://easypaysoftware.com/mobile.easypay5.com_base64encoded.cer</a></td></tr><tr><td align="center">mobile.easypay5.com.p7b</td><td></td><td></td><td><a href="https://easypaysoftware.com/mobile.easypay5.com.p7b">https://easypaysoftware.com/mobile.easypay5.com.p7b</a></td></tr><tr><td align="center">mobile.easypay5.com.pem</td><td></td><td></td><td><a href="https://easypaysoftware.com/mobile.easypay5.com.pem">https://easypaysoftware.com/mobile.easypay5.com.pem</a></td></tr></tbody></table>



Examples of RSA encrypotion:

{% tabs %}
{% tab title="C#" %}
<pre class="language-csharp" data-overflow="wrap" data-line-numbers><code class="lang-csharp">using System.Security.Cryptography;
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
<strong>byte[] encryptedBytes = rsaPublicKey.Encrypt(plainBytes,
</strong><strong>  RSAEncryptionPadding.OaepSHA1);
</strong>
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

</code></pre>
{% endtab %}

{% tab title="Java" %}
<pre class="language-java" data-overflow="wrap" data-line-numbers><code class="lang-java">package NumberEncrypt;

import java.io.FileInputStream;
import java.io.FileNotFoundException;
import java.io.IOException;
import java.nio.charset.StandardCharsets;
import java.security.InvalidKeyException;
import java.security.KeyStore;
import java.security.KeyStoreException;
import java.security.NoSuchAlgorithmException;
import java.security.cert.Certificate;
import java.security.cert.CertificateException;
import java.security.cert.X509Certificate;
import java.util.Base64;
import java.util.Enumeration;
import javax.crypto.BadPaddingException;
import javax.crypto.Cipher;
import javax.crypto.IllegalBlockSizeException;
import javax.crypto.NoSuchPaddingException;

public class EncryptCard {

  public static void main(String[] args) {

    CertificateDetails certDetails = getCertificateDetails(
      "C:\\Users\\BobSmith\\Downloads\\mobile_easypay5_com.cer", "");
    String myCardNumber = "4111111111111111";
    byte[] plainbytes = myCardNumber.getBytes(StandardCharsets.UTF_8);
    try {
      Cipher cipher = Cipher.getInstance(
        "RSA/ECB/OAEPWithSHA-1AndMGF1Padding");
      cipher.init(Cipher.ENCRYPT_MODE,
        certDetails.getX509Certificate().getPublicKey());
      byte[] encryptedBytes = cipher.doFinal(plainbytes);
      String eBytesString = Base64.getEncoder()
        .encodeToString(encryptedBytes);
      System.out.println(eBytesString);

    }
    catch (NoSuchAlgorithmException e) {
      e.printStackTrace();
    }
    catch (NoSuchPaddingException e) {
      e.printStackTrace();
    }
    catch (InvalidKeyException e) {
      e.printStackTrace();
    }
    catch (IllegalBlockSizeException e) {
      e.printStackTrace();
    }
    catch (BadPaddingException e) {
      e.printStackTrace();
    }
  }

<strong>  public static CertificateDetails getCertificateDetails(
</strong><strong>    String jksPath, String jksPassword) {
</strong>
    CertificateDetails certDetails = null;
    try {
      // Provide location of Java Keystore and password for access
      KeyStore keyStore = KeyStore.getInstance("Windows-MY");
      keyStore.load(
        new FileInputStream(jksPath), jksPassword.toCharArray());

      // Iterate over all aliases
      Enumeration&#x3C;String> aliasEnum = keyStore.aliases();
      String alias = "";
      while (aliasEnum.hasMoreElements()) {
        alias = (String)aliasEnum.nextElement();
        if (alias.contains("mobile.easypay5.com")) {
          break;
        }
      }
      Certificate[] certChain = keyStore.getCertificateChain(alias);
      certDetails = new CertificateDetails();
      certDetails.setX509Certificate((X509Certificate)certChain[0]);
    }
    catch (KeyStoreException e) {
      e.printStackTrace();
    }
    catch (NoSuchAlgorithmException e) {
      e.printStackTrace();
    }
    catch (CertificateException e) {
      e.printStackTrace();
    }
    catch (FileNotFoundException e) {
      e.printStackTrace();
    }
    catch (IOException e) {
      e.printStackTrace();
    }

    return certDetails;
  }
}

package NumberEncrypt;

import java.security.PrivateKey;
import java.security.cert.X509Certificate;

public class CertificateDetails {

  private PrivateKey privateKey;
  private X509Certificate x509Certificate;
  public PrivateKey getPrivateKey() {
    return privateKey;
  }
  public void setPrivateKey(PrivateKey privateKey) {
    this.privateKey = privateKey;
  }
  public X509Certificate getX509Certificate() {
    return x509Certificate;
  }
  public void setX509Certificate(X509Certificate x509Certificate) {
    this.x509Certificate = x509Certificate;
  }
}
</code></pre>
{% endtab %}

{% tab title="JavaScript (Node.js)" %}
{% code overflow="wrap" lineNumbers="true" %}
```javascript
const crypto = require("crypto");
const fs = require("fs");
​
var myCardNumber = "4761530001111118";
​
try {
  const publicKey = Buffer.from(
    fs.readFileSync("mobile.easypay5.com.pem", { encoding: "utf-8" })
  );
​
  const encryptedData = crypto.publicEncrypt({
      key: publicKey,
      padding: crypto.constants.RSA_PKCS1_OAEP_PADDING,
      oaepHash: 'sha1',
    },
    Buffer.from(myCardNumber) // Convert the string to a buffer
  );
​
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





