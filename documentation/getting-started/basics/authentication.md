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

# Authentication

<figure><img src="../../../.gitbook/assets/Authentication Flow.png" alt=""><figcaption></figcaption></figure>



Both the REST and SOAP APIs provide their own methods for authenticating with Number. You will need to use them to receive a `SessKey`. To authenticate, you need to provide your `AccountCode` and `Token`.

***

{% include "../../../.gitbook/includes/param-account-code.md" %}

***

{% include "../../../.gitbook/includes/param-token.md" %}

***

As a result of authentication, you will obtain a session key. This key is required to prove your identity when using any of the other methods provided by our backend.

***

{% include "../../../.gitbook/includes/param-sess-key.md" %}

***

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

{% include "../../../.gitbook/includes/warning-hmac.md" %}

### HMAC header

When required to secure the request, the `SessKey` header will need to include additional data.

***

{% include "../../../.gitbook/includes/param-sesskey-pci-secure.md" %}

***

This altered key should be passed instead of the plain session key using a header with the same name, `SessKey`. Here are some examples of creating the header signature:

{% include "../../../.gitbook/includes/code-hmac.md" %}

### RSA encryption

When the REST API traffic originates from unknown networks or mobile devices, we also mandate that any credit card numbers be encrypted prior to building your request. You can download our RSA 2048 certificate and use the public key to encrypt the cardholder information.&#x20;

{% hint style="info" %}
When passing cardholder data through our REST API, only the credit card number needs to be encrypted using RSA, the expiration date and CVV can be left as is.
{% endhint %}

{% hint style="warning" %}
When encrypting sensitive cardholder data, use RSA encryption padding of OaepSHA1. \
Encrypted card numbers will always have 512 bytes.
{% endhint %}

{% include "../../../.gitbook/includes/link-rsa-certificate.md" %}

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

Each token has a lifespan of 6 months since it was generated and will need to be replaced afterwards. This can only be done by physically logging into The Client Admin Portal. To make the process faster, The Client Admin Portal provides a way to POST new tokens to your web server to help automate a part of the renewal process.

To learn how to use the Client Admin Portal to renew tokens, see the [client-admin-portal.md](../client-admin-portal.md "mention") guide.

<figure><img src="../../../.gitbook/assets/Token Renewal.png" alt=""><figcaption></figcaption></figure>





