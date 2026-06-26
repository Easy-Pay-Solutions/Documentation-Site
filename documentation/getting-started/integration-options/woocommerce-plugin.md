---
description: Classic WooCommerce Payment Plugin for PayForm
icon: wordpress-simple
---

# WooCommerce Plugin

The Number WooCommerce Gateway plugin enables merchants to securely accept credit and debit card payments using Number’s hosted [PayForm](payform.md). No additional programming is required, as the plugin automatically generates the PayForm URL and processes transaction results.

#### Features

* Secure hosted card collection powered by PayForm
* PCI-compliant tokenized payment processing
* Native WooCommerce checkout integration
* Securely save payment methods for faster repeat purchases
* Full and partial refund capabilities
* Surcharging support
* Express checkout with Apple Pay and Google Pay
* Customizable form styling

#### Software Requirements

* Minimum WordPress Version: 7.0
* WooCommerce Version: 10.3.1
* WooCommerce checkout pages must be set to _Classic Shortcode (_[_see WooCommerce Docs_](https://woocommerce.com/document/woocommerce-store-editing/customizing-cart-and-checkout/#incompatible-extensions)_)_

#### Install the Plugin

1. Upload the plugin zip via WordPress Admin&#x20;
2. Activate the plugin
3. Navigate to WooCommerce → Settings → Payments and enable Number Gateway
4. Enable open\_ssl in the php.ini file by uncommenting `extension=openssl`.
5. Add the encryption key that corresponds to your eIndex. While you are using test credentials you will use our sandbox test key.

```
Add the environment variable Number_ENCRYPTION_KEY and set it's value.

Modify the wp-config.php file to access the key as shown below:

/* Add any custom values between this line and the "stop editing" line. */
define('Number_ENCRYPTION_KEY', getenv('Number_ENCRYPTION_KEY') ?: ($_SERVER['Number_ENCRYPTION_KEY'] ?? null));
/* That's all, stop editing! Happy publishing. */
```

{% file src="../../../.gitbook/assets/numberpayments-plugin (1).zip" %}

#### Configuration and Settings

**General Settings**

<table><thead><tr><th width="186">Setting</th><th>Description</th><th>Default</th></tr></thead><tbody><tr><td>Enable/Disable</td><td>Enables or disables the Number payment gateway. When enabled, customers will be able to select this payment method during checkout.</td><td>no</td></tr><tr><td>Title</td><td>Defines the payment method title displayed to customers during checkout.</td><td>Credit Card Payment</td></tr><tr><td>Description</td><td>Controls the description shown to customers beneath the payment method title.</td><td>Pay securely using NumberPayments.</td></tr></tbody></table>

**API Settings**

<table><thead><tr><th width="189.4000244140625">Setting</th><th>Description</th><th>Default</th></tr></thead><tbody><tr><td>Account Code</td><td>The account code provided by Number.</td><td>—</td></tr><tr><td>Token</td><td>Secure API token used for authentication. Store securely and do not share publicly.</td><td>—</td></tr><tr><td>Merchant ID</td><td>The merchant ID from your Number account.</td><td>—</td></tr><tr><td>API URL</td><td>Endpoint URL used to submit payment transactions. </td><td><a href="https://easypay5.com/ApicardProcRest/v1.0.0">https://easypay5.com/ApicardProcRest/v1.0.0</a></td></tr><tr><td>eIndex</td><td>Encryption key index used by the hosted payment form.</td><td>300</td></tr></tbody></table>

**Payment Form Fields and Styling**

These settings control the appearance and behavior of the hosted payment form. There are a number of fields you can have added to your form. For some of the fields, you can choose to provide a default value, and to mark them as read-only.

{% hint style="info" %}
The PayForm Builder tool can be used to help configure these settings. It is available at [https://easypay8.com/byopayform](https://easypay8.com/byopayform).
{% endhint %}

| Setting     | Description                                                                                                                                              | Default                                                 |
| ----------- | -------------------------------------------------------------------------------------------------------------------------------------------------------- | ------------------------------------------------------- |
| Widget Type | Determines which transaction type the widget collects. Available options: `payment` (Standard payment form), `combination` (Combo widget configuration). | payment                                                 |
| Visible     | Controls which payment form fields are visible to the customer. Example configuration values are determined by the PayForm Builder tool.                 | 0600                                                    |
| ReadOnly    | Determines whether specific payment fields are read-only.                                                                                                | 0000                                                    |
| Styles      | Controls predefined style configuration options for the payment form.                                                                                    | 0001                                                    |
| Colors      | Defines the color palette used by the payment form.                                                                                                      | #ffffff,#428bca,#007bff,#212121,#ffffff,#212121,#ffffff |

#### PayForm Configuration and Features

Additional payment form functionality and validation settings.

| Setting           | Description                                                                                                                   | Default |
| ----------------- | ----------------------------------------------------------------------------------------------------------------------------- | ------- |
| Enable Wallets    | Enables supported digital wallets during checkout. Supported wallets: Apple Pay and Google Pay.                               | no      |
| Apple Pay Domain  | The domain registered with Apple for Apple Pay verification.                                                                  |         |
| AVS Partial Match | Requires only the ZIP/postal code to match the card issuer records.                                                           | no      |
| CVV Match         | Requires the card security code (CVV) to match the issuer records. If the CVV does not match, the transaction will be voided. | no      |

#### FAQ



<details>

<summary><strong>Are card details stored on my website?</strong></summary>

**No**. Card details are collected securely using PayForm and tokenized by the payment provider. Sensitive card data is not stored on your WooCommerce site.

</details>

<details>

<summary><strong>Does the plugin support saved payment methods?</strong></summary>

**Yes**. Logged-in customers can securely save their payment methods for faster future purchases.

</details>

<details>

<summary><strong>Does it work with WooCommerce Blocks?</strong></summary>

**No**, not at this time. The current plugin supports WooCommerce classic checkout.

</details>

