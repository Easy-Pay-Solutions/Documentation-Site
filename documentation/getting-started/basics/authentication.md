---
description: How to authenticate with the Number backend
coverY: 0
---

# Authentication

<figure><img src="../../../.gitbook/assets/Authentication Flow.png" alt=""><figcaption></figcaption></figure>



The REST API provides their own methods for authenticating with Number. You will need to use them to receive a `SessKey`. To authenticate, you need to provide your `AccountCode` and `Token`.

***

***

***

As a result of authentication, you will obtain a session key. This key is required to prove your identity when using any of the other methods provided by our backend.

***

***

It is required that you manage a session key throughout any 24-hour period:&#x20;

You will need to reauthenticate when one of the following two errors occurs:&#x20;

{% hint style="danger" %}
**Error 5030: Expired session - session key has expired after 25 hours**
{% endhint %}

{% hint style="danger" %}
**Error 5050: Unauthorized - your IP has changed since you last authenticated**
{% endhint %}

The system will lock your IP out if you send 6 unsuccessful authentication attempts in a row. **Always abort unsuccessful authentication attempts instead of retrying and notify the user.** Only the Number support team can remove the lock from a merchant.

We recommend that you obtain and use the same key until you receive one of above errors.



***



## HMAC and RSA

{% hint style="info" %}
The HMAC and RSA section only applies to using the REST API.
{% endhint %}

If you are not passing cardholder data through the REST API, you only need the session key to authenticate and connect to your account. Otherwise, you need to use a signature secured by an HMAC secret and and encrypt the cardholder data using our RSA certificate.

### HMAC header

When required to secure the request, the `SessKey` header will need to include additional data.

***

***

This altered key should be passed instead of the plain session key using a header with the same name, `SessKey`. Here are some examples of creating the header signature:

### RSA encryption

When the REST API traffic originates from unknown networks or mobile devices, we also mandate that any credit card numbers be encrypted prior to building your request. You can download our RSA 2048 certificate and use the public key to encrypt the cardholder information.&#x20;

{% hint style="info" %}
When passing cardholder data through our REST API, only the credit card number needs to be encrypted using RSA, the expiration date and CVV can be left as is.
{% endhint %}

{% hint style="warning" %}
When encrypting sensitive cardholder data, use RSA encryption padding of OaepSHA1. \
Encrypted card numbers will always have 512 bytes.
{% endhint %}

Examples of RSA encryption:

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



#### Encrypted test cards <a href="#test-cards" id="test-cards"></a>

Here are some test cards with encrypted card numbers for [first-data-testing.md](../../testing/first-data-testing.md "mention"). Before you implement encryption, you can use them for testing in the Sandbox environment.

You can read more about testing in the [testing](../../testing/ "mention") section.

{% tabs %}
{% tab title="Visa" %}
Card number: **4761 5300 0111 1118**

{% code title="Encrypted string" %}
```
K8ELXxBJGpgO02O9Rw3XYe32D4msyv2lBO/SaQyx2vkPjFdy8hBjOxKQ9Q9NMQro9HotSzdev0Legr+iwevfvMnZINZMAy7ufNA4CniT3YcNdOYbzATBD1iTTiLcf+/we9QHsuo70R7Mij9oONFdh5UX948v89ZQMc95RyXtXpU1sUXkf/GG+gm9XFG0y09pb7KCIwa8vxhbMej0I7k7xhR3t6651XWec7H4NVE6jqMOSK7S3/cuqU9eHhqOD24f3X8xnzrGQUTGEvfk63bsH4UgXq/lEo27yMSi0FpsBLyw7fE/1FsFQG58HgMoXmwdjGtHPSH4/xUXJHtihkKHi8Ge9Zch7k9v7ZiAAe48qUPmFs2bOH3XV3jtvPo3fX64vz3Ode37oehe06+MmQR7ho+cR/r/IDAA74zQWRgYfDL79UhaLEMCQ7mcoxGlRgz5gfOy1inD1mL14lPlH8FcTDcnlDBtwakzlSP8NrmtFGvz3gV9T3d9nAP2yBvP4qXF875rGhiXgQ8HQHAit0SyxMuqdNtnScUbTu4iUHqQr4xtsiOQ/MoJIFgygtPs4ndEpNAeImvr7+DgFQvhkZyDWJBQ8qqpv4vlO3pDAJ6/7UzSmSD5D9vjdFj9tAAf72cXLtu1STcB7XKzzrG696kBdYAWhoF/z72n1n4AtZGWMf0=
```
{% endcode %}
{% endtab %}

{% tab title="Mastercard" %}
Card number: **5137 2211 1111 6668**

{% code title="Encrypted string" %}
```
WkPwbAzt1xZxECR4tdWOZDi219AiFmKq8qn6/MwwMPSeqkcRInqFMp3DxmM33G7pPrsvkIZA5zwk/tPLjjKkPDE1czVdVHA8yxYra6ggiGnjlASrxKdDGz6vaujGOnnex3cjXxV4mGC2gEhERTaFyXVlJDpM2jh/fdbXpg11n0BwmFBzgReTAV5BsS87vOqLfHjg9evm4lTIlYoqKR6DcGLn27Wd2ExwQu6V8nc8rkR6hwqEXsz3BFsbDtUhLeeWZdsEtZfKbAMzVAjwhUIbtsm4NOLLyQ5aSVc3P48FuW5GU9OZJD1MeicdsD+DFYmQk77UkEWEcKm9hogzf66sgrLAhY+TXg4iO4X0BJb8AJQRV0m9Am3VaemOIX/zw851AacwWxVNgYwrxbzcik9ODZR5GR8pHwXsPfeED2XISzGyfBdpv/5gqs5wTAlpZc0yW0nDShx9j+nmUJGVrd3RMHJddOe5+8HIWHFqAh3cQ6DBPe4FgBrTTtM44FlG+PuCRcVW6eQrnUr/llnWJdrUT5wKvGodewJCZv5JAdY9JZk9uj/qyITnDXVDC7uxxdHQgdq8yqjLZ/6iUoSu/dFFIflXmc/QFF13kRX74+XzYkMdEhUWQQ73R2KUKuTtO0jPMW5f+52UVJmUjEKYcggB8PcapFXAToKY0WaQhoSwOi0=
```
{% endcode %}
{% endtab %}

{% tab title="Discover" %}
Card number: **6011 2087 0111 7775**

{% code title="Encrypted string" %}
```
FFcT8XK/lbjN6oBxp7qY4DND1QYeejnjcaYxCfVVaRQ4tqgE6SrOSGqvpfkOXWbacOHDd26SF+lNGx2Uj7UxMRglY/6AjsMfWfffG15kyfKNLJIPwiLklpNwKgOH3J9z8CHYXF1G7gQR/q4Z42z851iFB7DNGfPJ7iZk+ZPh4YEer+R+ZH2nlLx0GVcbI6YOXtCgNLC8LJd8brzrmqKyA/0ZrJJaD+PmiK6rZxcHdPqIdx1Bc+x7y54GTd6LpigGVtnS65PKPzjIjfXYpTgyBQhbqIpy6qu5r6G3CwWupYjdXV4xX3GzTsQDX3byoSssRdQEmDeUa78iIlk3QbHHJn81SdorHaUI34uU1c0D5eqWzVSh4aAhrnTjDlx0ecS1Wn0cPpMvDxVZI3pEq3TrnuUQZgvcHJDMsZ3Dn1pviQnah272d3bh8uL8u/Drb7FLREgK7o8ZlV/rcPGgf++8N7CMEyZgIfVWuXc8EVRHA2KWuSTKgFfNyWX7GAF41f1EYEYn7dMd8EZcv6atpXNuLhsIAyKUeVoYO8nhBLHmtNBvKm2Ly5CSW344MiKUjmpR8+FpuBgLyJrVHkAaZmKLKcmaKqVEcVzqq+uiN0RhXWnkiUyODKdaP+LQjsNzmdbieW0ZaXJJPOkmMrgbuOfeDv6B9MUEW3UOoUEFAY48+Kg=
```
{% endcode %}
{% endtab %}

{% tab title="AMEX" %}
Card number: **3710 3008 9111 338**

{% code title="Encrypted string" %}
```
hWp5QKogAb7jkP85oHB7q+yYLw75IXVBzhGdQ0oZUUNk+z1uVLWK3ZyFwoi1Op8f5naINaHZ9T0ke2OW7Ydh7aYo3nTmhXVkM8LdYB3OUcvscj92HB5CHiWo1jBG0Jv4+vicBfOFT404r4MLwIqpdJVrr0URS0sSbSSPo34vk31GS9mihi+8UBzRXip8WKgnS5003grbvYf7tqGGK4YwrxCIgZRGqGIIrjqhrILBwn3zUmCjFuMItiNJ+VhnrThBeIXk9Lb8+FqzzZw63sIW41m4xOuVa4ZMB/4EpuG84BsA2V1WukRWzQRCo2CFYn55T96/GRdUrz3tGWEVs3NfXs4116IcK5fwYNBt/n0gVhmji4TU4JjUl64XS9gjfnPHGm3YsuOIuHL4Kapklp6UpDh/bVt795zMisGvlYEWazjflsO6MkDE+lgwt5XNs0kGVdWql9OHYSxAcmEmgZ4/ERf4dmgp/3TN5cMh4KZWGnEeWapcUtWWRISnHCCnkOpvz3wDsjH/96zb9DsYsXJ+92u76tCo3PNOMcD/cyEwMpqpjqjg/Z0a1YcS/anEXdGGwoXy65VCEALLy8mAct7whyQeValIPXeNq7sEbU2Y+LO8pevIfepDjChC5lVm4r/vUJOWq0ZvOCfUgHpRKqLS+zq0AYC0xP1Y8Xe1L+yT1zY=
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

Once again, it's important to **abort unsuccessful authentication attempts** and notify the user that new credentials need to be applied to the product.&#x20;

The system will lock your IP after 6 unsuccessful attempts in a row. When a lockout occurs, our support department will need to manually audit it to determine if it's safe to remove the lock.&#x20;



***



## Token Renewal

The Client Admin Portal will allow you to create and manage all of your tokens.  There is no limit to the number of tokens you can create. We recommend creating a separate token for each individual processing location (IP address).

Each token has a lifespan of 2 years since it was generated and will need to be replaced afterwards. This can only be done by physically logging into The Client Admin Portal. To make the process faster, The Client Admin Portal provides a way to POST new tokens to your web server to help automate a part of the renewal process.

To learn how to use the Client Admin Portal to renew tokens, see the [client-admin-portal.md](../client-admin-portal.md "mention") guide.

<figure><img src="../../../.gitbook/assets/Token Renewal.png" alt=""><figcaption></figcaption></figure>





