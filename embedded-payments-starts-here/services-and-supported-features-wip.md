# Services and supported features (WIP)

### REST/SOAP API

**Characteristics:** \
Enables integration of payment systems with external applications, allowing for full automation.

**Use Cases:**\
Perfect for companies developing custom applications with embedded payment functionality that are adaptable to various programming environments.\


{% hint style="info" %}
Learn more about [REST API](../documentation/getting-started/integration-options-v1/rest-api-v1.md) and [SOAP API](../documentation/getting-started/integration-options-v1/soap-api-v1.md) integrations.
{% endhint %}

**Supported features:**

| Feature                            | Description                                                                                                                                                                                                                      |
| ---------------------------------- | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Online payments                    | Enables businesses to accept payments through their web applications or platforms.                                                                                                                                               |
| Surcharge payments                 | Allows businesses to add a surcharge or extra fee to the transaction amount.                                                                                                                                                     |
| Store card on file                 | Facilitates storing a customer's card details securely for future transactions.                                                                                                                                                  |
| Recurring payments (Payment Plans) | Supports setting up automatic, recurring transactions, ideal for subscriptions or installment plans.                                                                                                                             |
| Authorizing Payments               | Authorizes transactions and verifies funds with the card issuer.                                                                                                                                                                 |
| Voiding                            | Cancels authorized transactions pre-settlement, stopping fund transfers.                                                                                                                                                         |
| Crediting (Refunds)                | The process of returning funds to a customer's account after a transaction has been settled. This typically occurs when a customer returns a product or disputes a charge, and the merchant agrees to reimburse the amount paid. |
| Settlerments                       | Finalizing a transaction by transferring funds from the buyer to the seller.                                                                                                                                                     |
| Reporting                          | Involves generating summaries and analyses of transaction data to help merchants track financial activities, manage cash flow, and ensure compliance.                                                                            |

***

### iOS/Android Mobile SDK

**Characteristics:** \
Provides tools and libraries for integrating payment processing into mobile apps, with pre-built UI components and security features for iOS and Android.

**Use Cases:**\
Ideal for developers aiming to offer seamless in-app payments, especially in e-commerce and subscription-based mobile applications.\


{% hint style="info" %}
Learn more about [iOS SDK](../documentation/getting-started/integration-options-v1/ios-sdk-v1.md) and [Android SDK](../documentation/getting-started/integration-options-v1/android-sdk-v2.md) integrations.
{% endhint %}

**Supported features:**

| Feature                                               | Description                                                                                                                    |
| ----------------------------------------------------- | ------------------------------------------------------------------------------------------------------------------------------ |
| Online payments                                       | Processes payments without needing a physical point-of-sale system, using a mobile interface. (Card not present transactions)  |
| Surcharge payments                                    | Allows businesses to add a surcharge or extra fee to the transaction amount.                                                   |
| Store card on file (after collecting cardholder data) | Allows merchants to securely store and reuse cardholder information for future transactions - if the user saves his card data. |

***

### PayForm

**Characteristics:** \
A plug-and-play payment form that can be easily embedded on websites without advanced technical setup. Requires simple API integration to Initiate the Form.

**Use Cases:**\
Ideal for businesses seeking a quick, simple way to accept online payments without extensive integration. (Can be rendered in IFRAME or top-level page or Mobile Browser)\


{% hint style="info" %}
Learn more about [PayForm](../documentation/getting-started/integration-options-v1/payform-v1.md) integration.
{% endhint %}

**Supported features:**

| Feature                                               | Description                                                                                                                                                       |
| ----------------------------------------------------- | ----------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Online payments                                       | Provides a quick and simple way to accept payments directly through an embedded highly configurable form which can be used on your web site and/or mobile browser |
| Store card on file (after collecting cardholder data) | Allows merchants to securely store and reuse cardholder information for future transactions.                                                                      |
| Surcharge payments                                    | Allows businesses to add a surcharge or extra fee to the transaction amount.                                                                                      |

***

### Virtual Terminal:

**Characteristics:** \
Web application that provides comprehensive credit card processing functionality, including authorizations, credits, voids, and reporting, while supporting card swipers and chip readers for secure transactions

**Use Cases:**\
It is ideal for in-person/card-present transactions, allowing merchants to efficiently process payments directly at the point of sale with the WIN service installed.&#x20;

{% hint style="info" %}
Learn more about [Virtual Terminal](../documentation/getting-started/integration-options-v1/virtual-terminal.md) integration.
{% endhint %}

**Supported features:**

| Feature                             | Description                                                                                                                                                                                                                        |
| ----------------------------------- | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Online payments                     | Processes payments without needing a physical point-of-sale system, using a web interface.                                                                                                                                         |
| Card Present (via manual entry)     | Accepts payments by manually entering card details.                                                                                                                                                                                |
| Surcharge payments                  | Allows businesses to add a surcharge or extra fee to the transaction amount.                                                                                                                                                       |
| Store card on file (Annual Consent) | Allows storing customer card information with their consent for recurring use                                                                                                                                                      |
| Recurring payments (Payment Plans)  | Facilitates the automated scheduling of regular payments over time.                                                                                                                                                                |
| Authorizing Payments                | Verifies cardholder information and checks funds to approve transactions securely.                                                                                                                                                 |
| Voiding                             | Cancels authorized transactions pre-settlement, stopping fund transfers.                                                                                                                                                           |
| Crediting (Refunds)                 | The process of returning funds to a customer's account after a transaction has been completed. This typically occurs when a customer returns a product or disputes a charge, and the merchant agrees to reimburse the amount paid. |
| Settlerments                        | Finalizing a transaction by transferring funds from the buyer to the seller.                                                                                                                                                       |
| Reporting                           | Involves generating summaries and analyses of transaction data to help merchants track financial activities, manage cash flow, and ensure compliance.                                                                              |

***

### Desktop Applications

**Characteristics:** \
Installed on a user's computer for online payment processing.

**Use Cases:**\
Beneficial for businesses who would rather not log into a browser application.

{% hint style="info" %}
Learn more about [Desktop Applications](../documentation/getting-started/integration-options-v1/custom-desktop-application.md) integration.
{% endhint %}

**Supported features:**

| Feature                             | Description                                                                                                                                                                                                                        |
| ----------------------------------- | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Online payments                     | Processes payments without needing a physical point-of-sale system, using a web interface.                                                                                                                                         |
| Card Present (via manual entry)     | Accepts payments by manually entering card details.                                                                                                                                                                                |
| Surcharge payments                  | Allows businesses to add a surcharge or extra fee to the transaction amount.                                                                                                                                                       |
| Store card on file (Annual Consent) | Allows storing customer card information with their consent for recurring use                                                                                                                                                      |
| Recurring payments (Payment Plans)  | Facilitates the automated scheduling of regular payments over time.                                                                                                                                                                |
| Authorizing Payments                | Verifies cardholder information and checks funds to approve transactions securely.                                                                                                                                                 |
| Voiding                             | Cancels authorized transactions pre-settlement, stopping fund transfers.                                                                                                                                                           |
| Crediting (Refunds)                 | The process of returning funds to a customer's account after a transaction has been completed. This typically occurs when a customer returns a product or disputes a charge, and the merchant agrees to reimburse the amount paid. |
| Settlerments                        | Finalizing a transaction by transferring funds from the buyer to the seller.                                                                                                                                                       |
| Reporting                           | Involves generating summaries and analyses of transaction data to help merchants track financial activities, manage cash flow, and ensure compliance.                                                                              |

***

### WIN SDK (Dynamic Link Libraries (DLL))

**Characteristics:** \
Used by desktop applications to integrate payment functions.

**Use Cases:**\
For developers integrating payment functionalities into desktop software.\


{% hint style="info" %}
Learn more about [WIN SDK DLL](../documentation/getting-started/integration-options-v1/dynamic-link-libraries.md) integration.
{% endhint %}

**Supported features:**

| Functionality                                 | Description                                                                                            |
| --------------------------------------------- | ------------------------------------------------------------------------------------------------------ |
| Online payments                               | Integrates payment capabilities directly into desktop applications for processing transactions online. |
| Store card on file (via integration with API) | Allows secure storage of card details through API integration for future transactions.                 |
| Manually keyed transactions                   | Supports Chip/Tap/Swipe and Keyed card data.                                                           |
| Card present payments (Verifone)              | Accepts payments via Chip/Tap/Swipe and Keyed card data through Verifone device.                       |
| Authorizing Payments                          | Verifies cardholder information and checks funds to approve transactions securely.                     |
| Recurring payments (Automated Payment Plans)  | Automates payment plans using Dynamic Link Libraries (DLL)                                             |
| Surcharge payments                            | Allows businesses to add a surcharge or extra fee to the transaction amount.                           |

***

### Win Services:

**Characteristics:** \
Installed in order to support a local Verifone card reader.

**Use Cases:**\
Ideal for continuous or automated payment processing within any browser application.

{% hint style="info" %}
Learn more about Win Services integration.
{% endhint %}

**Supported features:**

| Feature                                       | Description                                                                                                           |
| --------------------------------------------- | --------------------------------------------------------------------------------------------------------------------- |
| Card present via Verifone devices             | Processes physical or keyed card transactions using Verifone devices with Windows services running in the background. |
| Online payments (via browser-based interface) | Supports transaction processing through a web interface, utilizing Windows services for continuous operation.         |
| Manually keyed transactions                   | Supports Chip/Tap/Swipe and Keyed card data.                                                                          |
| Surcharge payments                            | Allows businesses to add a surcharge or extra fee to the transaction amount.                                          |
| Authorizing Payments                          | Verifies cardholder information and checks funds to approve transactions securely.                                    |
| Store card on file (via integration with API) | Allows secure storage of card details for future transactions.                                                        |
| Recurring payments (Automated Payment Plans)  | Automates payment plans using Dynamic Link Libraries (DLL)                                                            |

### Text2Pay

**Characteristics:** \
Allows merchants to send payment reminders and links via SMS or email.

**Use Cases:**\
Ideal for reminding customers about upcoming payments.\


**Supported features:**

| Feature                                       | Description                                                                        |
| --------------------------------------------- | ---------------------------------------------------------------------------------- |
| Authorizing Payments                          | Verifies cardholder information and checks funds to approve transactions securely. |
| Surcharge payments                            | Allows businesses to add a surcharge or extra fee to the transaction amount.       |
| Store card on file (via integration with API) | Allows secure storage of card details for future transactions.                     |
