# Services and supported features (WIP)

### REST/SOAP API

**Characteristics:** \
Enables integration of payment systems with external applications, allowing for full automation.

**Use Cases:**\
Perfect for companies developing custom applications with embedded payment functionality that are adaptable to various programming environments.\


**Supported features:**

| Feature                            | Description                                                                                                                                                                                                                               |
| ---------------------------------- | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Online payments                    | Enables businesses to accept payments through their web applications or platforms.                                                                                                                                                        |
| Surcharge payments                 | Allows businesses to add a surcharge or extra fee to the transaction amount.                                                                                                                                                              |
| Store card on file                 | Facilitates storing customer's card details securely for future transactions.                                                                                                                                                             |
| Recurring payments (payment plans) | Supports setting up automatic, recurring transactions, ideal for subscriptions or installment plans.                                                                                                                                      |
| Authorizing payments               | Authorizes transactions and verifies funds with the card issuer.                                                                                                                                                                          |
| Voiding                            | Cancels authorized transactions pre-settlement, stopping fund transfers.                                                                                                                                                                  |
| Crediting (refunds)                | <p>The process of returning funds to a customer's account after a transaction has been settled. </p><p></p><p>This typically occurs when a customer returns a product or disputes a charge, and the merchant agrees to reimbursement.</p> |
| Settlements                        | Finalizing a transaction by transferring funds from the buyer to the seller.                                                                                                                                                              |
| Reporting                          | Involves generating summaries and analyses of transaction data to help merchants track financial activities, manage cash flow, and ensure compliance.                                                                                     |

{% content-ref url="../documentation/getting-started/integration-options-v1/rest-api-v1.md" %}
[rest-api-v1.md](../documentation/getting-started/integration-options-v1/rest-api-v1.md)
{% endcontent-ref %}

{% content-ref url="../documentation/getting-started/integration-options-v1/soap-api-v1.md" %}
[soap-api-v1.md](../documentation/getting-started/integration-options-v1/soap-api-v1.md)
{% endcontent-ref %}



***



### iOS/Android Mobile SDK

**Characteristics:** \
Provides tools and libraries for integrating payment processing into mobile apps, with pre-built UI components and security features for iOS and Android.

**Use Cases:**\
Ideal for developers aiming to offer seamless in-app payments, especially in e-commerce and subscription-based mobile applications.\


**Supported features:**

| Feature                                               | Description                                                                                                                    |
| ----------------------------------------------------- | ------------------------------------------------------------------------------------------------------------------------------ |
| Online payments                                       | Processes payments without needing a physical point-of-sale system, using a mobile interface. (Card not present transactions)  |
| Surcharge payments                                    | Allows businesses to add a surcharge or extra fee to the transaction amount.                                                   |
| Store card on file (after collecting cardholder data) | Allows merchants to securely store and reuse cardholder information for future transactions if the user saves their card data. |

{% content-ref url="../documentation/getting-started/integration-options-v1/ios-sdk-v1.md" %}
[ios-sdk-v1.md](../documentation/getting-started/integration-options-v1/ios-sdk-v1.md)
{% endcontent-ref %}

{% content-ref url="../documentation/getting-started/integration-options-v1/android-sdk-v2.md" %}
[android-sdk-v2.md](../documentation/getting-started/integration-options-v1/android-sdk-v2.md)
{% endcontent-ref %}



***



### PayForm

**Characteristics:** \
A plug-and-play payment form that can be easily embedded on websites without advanced technical setup. Requires simple API integration to initiate the form.

**Use Cases:**\
Ideal for businesses seeking a quick, simple way to accept online payments without extensive integration. (Can be rendered in an iFrame, top-level page, or mobile browser).\


**Supported features:**

| Feature                                               | Description                                                                                                                                  |
| ----------------------------------------------------- | -------------------------------------------------------------------------------------------------------------------------------------------- |
| Online payments                                       | Provides a quick and simple way to accept payments directly through an embedded, highly configurable form which can be used on your website. |
| Store card on file (after collecting cardholder data) | Allows merchants to securely store and reuse cardholder information for future transactions.                                                 |
| Surcharge payments                                    | Allows businesses to add a surcharge or extra fee to the transaction amount.                                                                 |

{% content-ref url="../documentation/getting-started/integration-options-v1/payform-wip.md" %}
[payform-wip.md](../documentation/getting-started/integration-options-v1/payform-wip.md)
{% endcontent-ref %}



***



### Virtual Terminal

**Characteristics:** \
Web application that provides comprehensive credit card processing functionality, including authorizations, credits, voids, and reporting, while supporting card swipers and chip readers for secure transactions.

**Use Cases:**\
Ideal for in-person/card-present transactions, allowing merchants to efficiently process payments directly at the point of sale with the Win service installed.&#x20;



**Supported features:**

| Feature                             | Description                                                                                                                                                                                                                                 |
| ----------------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Online payments                     | Processes payments without needing a physical point-of-sale system, using a web interface.                                                                                                                                                  |
| Card present (via manual entry)     | Accepts payments by manually entering card details.                                                                                                                                                                                         |
| Surcharge payments                  | Allows businesses to add a surcharge or extra fee to the transaction amount.                                                                                                                                                                |
| Store card on file (annual consent) | Allows storing customer card information with their consent for recurring use.                                                                                                                                                              |
| Recurring payments (payment plans)  | Facilitates the automated scheduling of regular payments over time.                                                                                                                                                                         |
| Authorizing payments                | Verifies cardholder information and checks funds to approve transactions securely.                                                                                                                                                          |
| Voiding                             | Cancels authorized transactions pre-settlement, stopping fund transfers.                                                                                                                                                                    |
| Crediting (refunds)                 | <p>The process of returning funds to a customer's account after a transaction has been completed. </p><p></p><p>This typically occurs when a customer returns a product or disputes a charge, and the merchant agrees to reimbursement.</p> |
| Settlements                         | Finalizing a transaction by transferring funds from the buyer to the seller.                                                                                                                                                                |
| Reporting                           | Involves generating summaries and analyses of transaction data to help merchants track financial activities, manage cash flow, and ensure compliance.                                                                                       |

{% content-ref url="../documentation/getting-started/integration-options-v1/virtual-terminal.md" %}
[virtual-terminal.md](../documentation/getting-started/integration-options-v1/virtual-terminal.md)
{% endcontent-ref %}



***



### Desktop Applications

**Characteristics:** \
Installed on a user's computer for online payment processing.

**Use Cases:**\
Beneficial for businesses who would rather not log into a browser application.



**Supported features:**

| Feature                             | Description                                                                                                                                                                                                                        |
| ----------------------------------- | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Online payments                     | Processes payments without needing a physical point-of-sale system, using a user interface.                                                                                                                                        |
| Card Present (via manual entry)     | Accepts payments by manually entering card details.                                                                                                                                                                                |
| Surcharge payments                  | Allows businesses to add a surcharge or extra fee to the transaction amount.                                                                                                                                                       |
| Store card on file (Annual Consent) | Allows storing customer card information with their consent for recurring use                                                                                                                                                      |
| Recurring payments (Payment Plans)  | Facilitates the automated scheduling of regular payments over time.                                                                                                                                                                |
| Authorizing Payments                | Verifies cardholder information and checks funds to approve transactions securely.                                                                                                                                                 |
| Voiding                             | Cancels authorized transactions pre-settlement, stopping fund transfers.                                                                                                                                                           |
| Crediting (Refunds)                 | The process of returning funds to a customer's account after a transaction has been completed. This typically occurs when a customer returns a product or disputes a charge, and the merchant agrees to reimburse the amount paid. |
| Settlerments                        | Finalizing a transaction by transferring funds from the buyer to the seller.                                                                                                                                                       |
| Reporting                           | Involves generating summaries and analyses of transaction data to help merchants track financial activities, manage cash flow, and ensure compliance.                                                                              |

{% content-ref url="../documentation/getting-started/integration-options-v1/custom-desktop-application.md" %}
[custom-desktop-application.md](../documentation/getting-started/integration-options-v1/custom-desktop-application.md)
{% endcontent-ref %}



***



### Dynamic Link Libraries

**Characteristics:** \
Used by desktop applications to integrate payment functions.

**Use Cases:**\
For developers integrating payment functionalities into desktop software.\


**Supported features:**

| Functionality                                 | Description                                                                                            |
| --------------------------------------------- | ------------------------------------------------------------------------------------------------------ |
| Online payments                               | Integrates payment capabilities directly into desktop applications for processing transactions online. |
| Store card on file (via integration with API) | Allows secure storage of card details through API integration for future transactions.                 |
| Manually keyed transactions                   | Supports Chip/Tap/Swipe and Keyed card data.                                                           |
| Card present payments (Verifone)              | Accepts payments via Chip/Tap/Swipe and Keyed card data through Verifone device.                       |
| Authorizing Payments                          | Verifies cardholder information and checks funds to approve transactions securely.                     |
| Recurring payments (automated payment plans)  | Automates payment plans                                                                                |
| Surcharge payments                            | Allows businesses to add a surcharge or extra fee to the transaction amount.                           |

{% content-ref url="../documentation/getting-started/integration-options-v1/dynamic-link-libraries.md" %}
[dynamic-link-libraries.md](../documentation/getting-started/integration-options-v1/dynamic-link-libraries.md)
{% endcontent-ref %}



