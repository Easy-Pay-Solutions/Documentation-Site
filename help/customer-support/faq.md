---
description: Answers to frequently asked questions
---

# FAQ

### Integration Options

<details>

<summary>What are the options available for integrating Number with Verifone card readers?</summary>

Number offers four options: [#easy-pay-verifone-sdk](../../documentation/getting-started/integration-options/verifone.md#easy-pay-verifone-sdk "mention"), [#easy-pay-verifone-sdk-1](../../documentation/getting-started/integration-options/verifone.md#easy-pay-verifone-sdk-1 "mention"), [#browser-based-installation](../../documentation/getting-started/integration-options/verifone.md#browser-based-installation "mention"), and [#virtual-terminal](../../documentation/getting-started/integration-options/verifone.md#virtual-terminal "mention") support.

</details>

<details>

<summary>How do I implement the Number Verifone SDK in my application?</summary>

To implement the Number Verifone SDK, download the DLL, include it in your project, and follow the integration guidelines provided in the [verifone.md](../../documentation/getting-started/integration-options/verifone.md "mention") integration guide to set up payment processing.

</details>

<details>

<summary>Can I use Number and Verifone with a web application?</summary>

Yes, Number provides a browser-based interface that allows integration with web applications using Cross-Origin Resource Sharing (CORS) to communicate with Verifone devices.&#x20;

You can find the full implementation details in the [verifone.md](../../documentation/getting-started/integration-options/verifone.md "mention") integration guide.

</details>

### Security and Compliance

<details>

<summary>How does Number ensure the security of cardholder data?</summary>

Number utilizes end-to-end encryption (P2PE) to secure cardholder data, ensuring it remains encrypted during transmission to the PCI Level One compliant processing platform.

</details>

<details>

<summary>What is HMAC, and why is it important in the Number API?</summary>

HMAC (Hash-based Message Authentication Code) is used to create a hash that verifies the authenticity of requests when passing cardholder data through the Number API.

</details>

<details>

<summary>What are the requirements for passing cardholder data through the Number API?</summary>

To pass cardholder data through the Number API, you need a session key, HMAC secret, and RSA Certificate to encrypt the credit card number before transmission.&#x20;

You can read more in [#hmac-and-rsa](../../documentation/getting-started/basics/authentication.md#hmac-and-rsa "mention") section of our [authentication.md](../../documentation/getting-started/basics/authentication.md "mention") guide.

</details>

<details>

<summary>How can I manage token renewal for Number?</summary>

You can manage token renewal through the Number Client Admin Portal, where you can create new tokens and view existing ones. Tokens expire every six months.

You can read more about token renewal in our [client-admin-portal.md](../../documentation/getting-started/client-admin-portal.md "mention") guide.

</details>

### Session Management

<details>

<summary>How do I manage session keys when using the Number API?</summary>

Call the authenticate method to obtain a session key using your account code and token. The session will be valid for 25 hours or until you change your IP. If you receive error codes 5030 or 5050, re-authenticate to obtain a new session key.

Read more in our [authentication.md](../../documentation/getting-started/basics/authentication.md "mention") guide.

</details>

<details>

<summary>What should I do if my session key expires?</summary>

If your session key expires, you will need to authenticate again to obtain a new session key. Monitor for expiration codes to ensure continuous access.

Read more in our [authentication.md](../../documentation/getting-started/basics/authentication.md "mention") guide.

</details>

<details>

<summary>What happens if I exceed the number of unsuccessful authentication attempts?</summary>

If you exceed six unsuccessful authentication attempts, your IP address will be locked out, requiring manual intervention from Number support to unlock it.

Read more in the [#lockouts](../../documentation/getting-started/basics/authentication.md#lockouts "mention") section of our [authentication.md](../../documentation/getting-started/basics/authentication.md "mention") guide.

</details>

<details>

<summary>How can I check if my authentication was successful?</summary>

After authentication, check the `FunctionOK` and `AuthSuccess` flags. If both are true, you will receive a session key; otherwise, read the error messages and abort the process.

</details>

### Payment Processing

<details>

<summary>What types of transactions can I process using Number?</summary>

Number allows you to process various types of transactions, including authorizations, credits, voids, settlements, and recurring payments through card-on-file plans

</details>

<details>

<summary>How do I handle refunds using the Number system?</summary>

To process refunds, you can use the Number API to initiate a credit transaction against the original payment. Ensure you have the original transaction ID to reference during the refund process.

</details>

<details>

<summary>What is the process for creating card-on-file payment plans using Number?</summary>

You can create card-on-file payment plans using a variety of channels such as the Virtual Terminal, our APIs, PayForm, widgets, and the Win service for Verifone. All of those options allow you to manage recurring payments and consent agreements.

To find out more, we recommend reading the [annual-consent.md](../../documentation/developer-quickstart/annual-consent.md "mention") quickstart guide.

</details>

<details>

<summary>How can I ensure that my transactions are secure?</summary>

Number employs end-to-end encryption (P2PE) for all transactions, ensuring that cardholder data is encrypted during transmission between the Verifone device and the Number cloud servers.

</details>

### Reconciliation

<details>

<summary>How can I ensure that my database contains accurate transaction data?</summary>

We recomend that your system periodically query our database to ensure you have accurate data. Webhooks are provided for real-time notifications, but you can augment this with transaction queries.

Read more about reconciliation in [#reconciliation](../../documentation/resources/querying.md#reconciliation "mention") section of the [querying.md](../../documentation/resources/querying.md "mention") reference.

</details>
