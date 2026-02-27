---
description: How to Download and  Install, by Browser type
---

# Certificate Installation

#### **Download the Certificate**

To download an SSL certificate from the Ingenico device, go to https://`[your-terminal-ip]`:8090 in your browser. Look for the padlock icon in the browser's address bar, and download the certificate.

#### **Method by Browser**

**Windows (Chrome/Edge)**

Click the lock icon - Certificate is Valid - Details - Copy to File - Select format (Base-64 encoded .CER) - Save

***

**macOS (Safari/Chrome)**

Click the lock icon - View Certificate - Drag the certificate icon to the desktop.

***

**Firefox**

Click the lock icon - More Information - View Certificate - Export (save as .crt or .pem).

The certificate is also available on our website at "somewhere soon".

***

#### **Installation Steps for Major Browsers**

**Windows (Chrome/Edge)**

1. Open Chrome Settings, search for "certificates", and click _Manage device certificates_.
2. Go to the _Trusted Root Certification Authorities_ tab.
3. Click _Import_ and follow the wizard to select your certificate file (PFX or CRT).
4. Ensure it is placed in the "Trusted Root Certification Authorities" store.

***

**macOS (Safari/Chrome)**

1. Open _Keychain Access_ and select the "System" keychain.
2. Drag and drop the certificate file into the list.
3. Double-click the certificate, expand "Trust," and set "When using this certificate" to _Always Trust_.

***

**Firefox**

1. Go to Settings > Privacy & Security > Certificates.
2. Click _View Certificates_, then the _Authorities_ tab.
3. Click _Import_ and select the certificate file, ensuring you check "Trust this CA to identify websites".
