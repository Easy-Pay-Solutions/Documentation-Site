# FAQ

### Integration Options

<details>

<summary>What are the different options available for integrating Number with Verifone card readers?</summary>

Number offers four options: Standalone Desktop Application, Number Verifone SDK, Browser-based Interface, and Virtual Terminal support.

</details>

<details>

<summary>How do I implement the Number Verifone SDK in my application?</summary>

To implement the Number Verifone SDK, download the DLL, include it in your project, and follow the integration guidelines provided in the documentation to set up payment processing.

</details>

<details>

<summary>Can I use Number (Verifone) with a web application?</summary>

Yes, Number provides a browser-based interface that allows integration with web applications using Cross-Origin Resource Sharing (CORS) to communicate with Verifone devices.

</details>

<details>

<summary>What is the process for creating Card-on-File payment plans using Number?</summary>

You can create Card-on-File payment plans using (a variety of channels such as the Virtual Terminal, API, Payform, widgets, and WIN SDK ) which allows you to manage recurring payments and consent agreements.

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

To pass cardholder data through the Number API, you need a Session Key, HMAC secret, and RSA Certificate to encrypt the credit card number before transmission. However, it is important to note that HMAC enforcement is primarily applied when using the Mobile SDK, as the networks involved can present higher risks

</details>

<details>

<summary>How can I manage token renewal for Number?</summary>

You can manage token renewal through the Number Client Admin Portal, where you can create new tokens and view existing ones. Tokens expire every six months.

</details>

### Session Management

<details>

<summary>How do I manage session keys when using the Number API?</summary>

Obtain a session key using your Account Code and Token, which is valid for 25 hours. If you receive error codes 5030 or 5050, re-authenticate to obtain a new session key.

</details>

<details>

<summary>What should I do if my session key expires?</summary>

If your session key expires, you will need to authenticate again to obtain a new session key. Monitor for expiration codes to ensure continuous access.

</details>

<details>

<summary>What happens if I exceed the number of unsuccessful authentication attempts?</summary>

If you exceed six unsuccessful authentication attempts, your IP address will be locked out, requiring manual intervention from Number support to unlock it.

</details>

<details>

<summary>How can I check if my authentication was successful?</summary>

After authentication, check the FunctionOK and AuthSuccess flags. If both are true, you will receive a session key; otherwise, read the error messages and abort the process.

</details>

### Payment Processing

<details>

<summary>What types of transactions can I process using Number?</summary>

Number allows you to process various types of transactions, including authorizations, credits, voids, settlements, and recurring payments through Card-on-File plans

</details>

<details>

<summary>How do I handle refunds using the Number system?</summary>

To process refunds, you can use the Number API to initiate a credit transaction against the original payment. Ensure you have the original transaction ID to reference during the refund process .

</details>

<details>

<summary>What is the process for creating a Card-on-File payment plan?</summary>

To create a Card-on-File payment plan, you can use the Number API to collect cardholder data and then set up the payment plan by specifying the consent type (Annual or Fixed Recurring)

</details>

<details>

<summary>How can I ensure that my transactions are secure?</summary>

Number employs end-to-end encryption (P2PE) for all transactions, ensuring that cardholder data is encrypted during transmission between the Verifone device and the Number cloud servers

</details>

### Reconciliation

<details>

<summary>How can I ensure that My database contains accurate transaction data</summary>

We recomend that your system periodically query our database to ensure you have accurate data . Webhooks are provided for realtime notifications but you can augment this with Transaction Queries

</details>
