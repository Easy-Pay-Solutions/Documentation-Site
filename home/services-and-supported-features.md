---
description: A short compilation of Number services and supported features
---

# Services and Supported Features

### REST API

**Characteristics:** \
Enables integration of payment systems with external applications, allowing for full automation.

**Use Cases:**\
Perfect for companies developing custom applications with embedded payment functionality that are adaptable to various programming environments.

{% hint style="info" %}
To learn how to use the API, see the [rest-api.md](../documentation/getting-started/integration-options/rest-api.md "mention") integration guide.
{% endhint %}



**Supported features:**

| Feature                            | Description                                                                                                                                                                                                            |
| ---------------------------------- | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Online payments                    | Enables businesses to accept payments through their web applications or platforms.                                                                                                                                     |
| Surcharge payments                 | Allows businesses to add a surcharge or an extra fee to the transaction amount.                                                                                                                                        |
| Store card on file                 | Facilitates storing a customer's card details securely for future transactions.                                                                                                                                        |
| Recurring payments (payment plans) | Supports setting up automatic, recurring transactions, ideal for subscriptions or installment plans.                                                                                                                   |
| Authorizing payments               | Authorizes transactions and verifies funds with the card issuer.                                                                                                                                                       |
| Voiding                            | Cancels authorized transactions pre-settlement, stopping fund transfers.                                                                                                                                               |
| Crediting (refunds)                | <p>Return funds to a customer's account after a transaction has been completed. </p><p></p><p>Occurs when a customer returns a product or disputes a charge, and the merchant agrees to reimburse the amount paid.</p> |
| Settlements                        | Finalizing a transaction by transferring funds from the buyer to the seller.                                                                                                                                           |
| Reporting                          | Involves generating summaries and analyses of transaction data to help merchants track financial activities, manage cash flow, and ensure compliance.                                                                  |



***



### Android/iOS Mobile SDK

**Characteristics:** \
Provides tools and libraries for integrating payment processing into mobile apps, with pre-built UI components and security features for Android and iOS.

**Use Cases:**\
Ideal for developers aiming to offer seamless in-app payments, especially in e-commerce and subscription-based mobile applications.

{% hint style="info" %}
To learn to use mobile SDKs, see the [android-sdk.md](../documentation/getting-started/integration-options/android-sdk.md "mention") and [ios-sdk.md](../documentation/getting-started/integration-options/ios-sdk.md "mention") integration guides.
{% endhint %}



**Supported features:**

| Feature                                               | Description                                                                                                                    |
| ----------------------------------------------------- | ------------------------------------------------------------------------------------------------------------------------------ |
| Online payments                                       | Processes payments without needing a physical point-of-sale system, using a mobile interface (card not present transactions).  |
| Surcharge payments                                    | Allows businesses to add a surcharge or an extra fee to the transaction amount.                                                |
| Store card on file (after collecting cardholder data) | Allows merchants to securely store and reuse cardholder information for future transactions if the user saves their card data. |



***



### PayForm

**Characteristics:** \
A plug-and-play payment form that can be easily embedded on websites without advanced technical setup. Requires simple API integration to initiate the form.

**Use Cases:**\
Ideal for businesses seeking a quick, simple way to accept online payments without extensive integration. Can be rendered in IFrame or as a top-level page.

{% hint style="info" %}
To learn to use the PayForm, see the [payform.md](../documentation/getting-started/integration-options/payform.md "mention") configuration guide.
{% endhint %}



**Supported features:**

| Feature                                               | Description                                                                                                                                |
| ----------------------------------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------ |
| Online payments                                       | Provides a quick and simple way to accept payments directly through a highly configurable embedded form which can be used on your website. |
| Store card on file (after collecting cardholder data) | Allows merchants to securely store and reuse cardholder information for future transactions.                                               |
| Surcharge payments                                    | Allows businesses to add a surcharge or an extra fee to the transaction amount.                                                            |
| Multiple payment types                                | PayForm supports a range of payment options, including credit cards, ACH, Apple Pay, and Google Pay.                                       |



***



### Virtual Terminal

**Characteristics:** \
Web application that provides comprehensive credit card processing functionality, including authorizations, credits, voids, and reporting, while supporting card swipers and chip readers for secure transactions.

**Use Cases:**\
It is ideal for in-person/card-present transactions, allowing merchants to efficiently process payments directly at the point of sale with the Windows service installed.&#x20;

{% hint style="info" %}
To learn to use the Virtual Terminal, see the [virtual-terminal.md](../documentation/getting-started/integration-options/virtual-terminal.md "mention") user guide.
{% endhint %}

{% hint style="success" %}
You can also use our **custom desktop application** as an alternative to the Virtual Terminal. The desktop application supports much of the same features. &#x20;

It can be installed on user's computer, and it's beneficial for businesses who would rather not log into a browser application.

To learn more about our custom desktop application, [contact the Number support team](../help/customer-support/).
{% endhint %}



**Supported features:**

| Feature                             | Description                                                                                                                                                                                                            |
| ----------------------------------- | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Online payments                     | Processes payments without needing a physical point-of-sale system, using a web interface.                                                                                                                             |
| Card present                        | Accepts card present payments using Verifone or a different USB card reader.                                                                                                                                           |
| Manual entry                        | Accepts payments by manually entering card details.                                                                                                                                                                    |
| Surcharge payments                  | Allows businesses to add a surcharge or an extra fee to the transaction amount.                                                                                                                                        |
| Store card on file (annual consent) | Allows storing customer card information with their consent for recurring use                                                                                                                                          |
| Recurring payments (payment plans)  | Facilitates the automated scheduling of regular payments over time.                                                                                                                                                    |
| Authorizing payments                | Verifies cardholder information and checks funds to approve transactions securely.                                                                                                                                     |
| Voiding                             | Cancels authorized transactions pre-settlement, stopping fund transfers.                                                                                                                                               |
| Crediting (refunds)                 | <p>Return funds to a customer's account after a transaction has been completed. </p><p></p><p>Occurs when a customer returns a product or disputes a charge, and the merchant agrees to reimburse the amount paid.</p> |
| Settlements                         | Finalizing a transaction by transferring funds from the buyer to the seller.                                                                                                                                           |
| Reporting                           | Involves generating summaries and analyses of transaction data to help merchants track financial activities, manage cash flow, and ensure compliance.                                                                  |



***



### Win Service and DLL

**Characteristics:** \
Used by your application and a Verifone card reader to integrate Number payment functions.

**Use Cases:**\
For developers integrating payment functionalities into card readers and custom applications.

{% hint style="info" %}
Learn more about integrating with Verifone in the [verifone.md](../documentation/getting-started/integration-options/verifone.md "mention") integration guide.
{% endhint %}



**Supported features:**

| Functionality                                 | Description                                                                                                              |
| --------------------------------------------- | ------------------------------------------------------------------------------------------------------------------------ |
| Card present (via Verifone device)            | Processes physical or keyed card transactions using Verifone devices with the Windows service running in the background. |
| Online payments (via browser-based interface) | Supports transaction processing through a web interface, utilizing the Windows service for continuous operation.         |
| Manually keyed transactions                   | Supports chip/tap/swipe and keyed card data.                                                                             |
| Surcharge payments                            | Allows businesses to add a surcharge or an extra fee to the transaction amount.                                          |
| Authorizing payments                          | Verifies cardholder information and checks funds to approve transactions securely.                                       |
| Store card on file                            | Allows secure storage of card details for future transactions.                                                           |
| Recurring payments (automated payment plans)  | Automate payment plans.                                                                                                  |

