---
description: Learn to make credit card sales and collect consent with Number
---

# Card Sales and Consent

<figure><img src="../../.gitbook/assets/Credit card sale 3.png" alt=""><figcaption></figcaption></figure>

## Card present sales and consent

To make sales or collect consent when a card is present using Number, you have several options:

{% stepper %}
{% step %}
#### **Integration with a Verifone card reader**

You can use Verifone card readers. They are secure devices that connect to your computer via USB. They encrypt cardholder data during transmission to ensure security.
{% endstep %}

{% step %}
#### USB card reader through the Virtual Terminal or our desktop app

When you have a USB card reader connected to your machine, you can log into the Virtual Terminal to make card present sales and to collect consent.&#x20;

We also have a custom desktop application which can be convenient in an office setting to collect card present payments. It offers similar functionality to the Virtual Terminal.
{% endstep %}

{% step %}
#### Custom integration with our REST API

Our REST API offers methods for handling card present transactions.

If you have your own PCI level one compliance program, you may write your own custom code calling our APIs to collect card present payments and consent. You can read more about PCI compliance in the short [#pci-compliance](../getting-started/integration-options/#pci-compliance "mention") section of our [integration-options](../getting-started/integration-options/ "mention") guide.
{% endstep %}
{% endstepper %}



### Verifone integration

There are a few approaches to integration, You can either use the browser-based interface option or the Desktop integration with SDK .

{% hint style="info" %}
For an in-depth tutorial on how to integrate and use your Verifone card reader with Number, see our [verifone.md](../getting-started/integration-options/verifone.md "mention") integration guide.
{% endhint %}

Before you start, you'll need to download the Verifone Windows service to your machine, connect your card reader device to a free USB port, allow it to initialize, extract the archive with the service and run the EXE as an administrator. After the installation is complete, reboot the system.

You can issue commands to the service by calling `https://localhost:8031` from your website.&#x20;

#### Verifone card present sales

Here's an simplified example of how you can invoke the service for a card present sale:

#### Verifone card present annual consent

Here's an simplified example of how you can invoke the service to collect annual consent:



### Virtual Terminal or desktop application

When you want to use your Verifone with the Virtual Terminal, you have to first install the very same Windows service that is used when doing a Verifone browser-based integration. After installation, [contact the Number support team](../../help/customer-support/) to get the card reader features activated.

{% hint style="info" %}
To learn more about using the Virtual Terminal, see the [virtual-terminal.md](../getting-started/integration-options/virtual-terminal.md "mention") user guide.
{% endhint %}

{% hint style="info" %}
Read more about using our custom desktop application for sales in the [integration-options](../getting-started/integration-options/ "mention") guide or [contact Number](../../help/customer-support/) to get access.
{% endhint %}

#### Virtual Terminal card present sales

When you visit the Virtual Terminal, log in and expand _Credit Cards_ in the navigation on the left. You'll see options for a sale, an EMV sale, authorization, forced auth, and adjustments.&#x20;

<figure><img src="../../.gitbook/assets/Virtual Terminal card present sales.png" alt=""><figcaption></figcaption></figure>

As long as your USB card reader is connected to your machine, it will seamlessly integrate with the Virtual Terminal for card present transactions.

#### Virtual Terminal card present consent

When you visit the Virtual Terminal, log in and expand _Consents_ in the navigation on the left. You'll see options for annual consent, EMV annual consent, and one-time consent. You can also expand the _Recurring_ tab to find options to create recurring consent, EMV recurring consent, and subscription consent.

<figure><img src="../../.gitbook/assets/Virtual Terminal manual consent.png" alt=""><figcaption></figcaption></figure>

<figure><img src="../../.gitbook/assets/Virtual Terminal card present consent 2.png" alt=""><figcaption></figcaption></figure>

As long as your USB card reader is connected to your machine, it will seamlessly integrate with the Virtual Terminal for card present transactions.



### REST API integration

Our APIs are useful for any Integration as you can apply a credit, void, query, charge a stored card etc. For integrators who are PCI Level one compliant you may also pass cardholder data directly through the API. Most integrations will use our PayForms to collect Cardholder data while the API will be used for all remaining activity.

{% hint style="info" %}
To learn more about our APIs, see the [rest-api.md](../getting-started/integration-options/rest-api.md "mention") integration guide.
{% endhint %}

When you scan the credit card and collect the track data alongside the other payment details, if using the REST API, prepare the HMAC secured header like shown in [authentication.md](authentication.md "mention") quickstart guide, and encrypt the card number using our RSA certificate.&#x20;

Follow the instructions in the API reference to prepare and handle the request.

#### API card present sales

You can use the following API operations:

* For the REST API, use [#apicardprocrest-v1.0.0-cardsale-cardpresent](../../api-reference/rest-api/card-operations-1/process-a-card-sale.md#apicardprocrest-v1.0.0-cardsale-cardpresent "mention")

#### API card present consent

You can use the following API operations:

* For the REST API, you can use [#apicardprocrest-v1.0.0-consentannual-create\_cp](../../api-reference/rest-api/consent-annual-1/create-annual-consent.md#apicardprocrest-v1.0.0-consentannual-create_cp "mention") and [#apicardprocrest-v1.0.0-consentrecurring-create](../../api-reference/rest-api/consent-recurring-1/create-recurring-consent.md#apicardprocrest-v1.0.0-consentrecurring-create "mention").



***



## Manual card sales and consent

To make credit card sales and collect consent using Number when you want to enter the card details manually, you have the following options:

{% stepper %}
{% step %}
#### PayForm widget

You can configure and customize our PayForm widget and redirect your users to a separate page with the form or embed it as an IFrame in your existing web application.
{% endstep %}

{% step %}
#### Virtual Terminal or our desktop application

The Virtual Terminal website allows you to handle manual card sales and consent collection by default. This approach requires no coding and is perfect for a physical point-of-sale.

We also have a custom desktop application which can be convenient way to collect manual card payments and consent. It offers much of the same functionality as the Virtual Terminal.
{% endstep %}

{% step %}
#### Android or iOS SDK integration

If you have a mobile application that needs to handle payments and consent, our SDKs implement secure forms which can collect cardholder information from your users.
{% endstep %}

{% step %}
#### REST API integration

For more customization, you can call our API for sales and consent.

If you have your own PCI level one compliance program, you may write your own custom code calling our API to collect manual card payments and consent. You can read more about PCI compliance in the short [#pci-compliance](../getting-started/integration-options/#pci-compliance "mention") section of our integration guide.
{% endstep %}
{% endstepper %}



### PayForm widget

The PayForm is designed to be a highly flexible and secure payment form for your users. To start collecting payments and consent with the PayForm, you'll want to use our builder tool for configuration, then our REST API to generate a payment URL.&#x20;

{% hint style="info" %}
Learn more about how to configure and use the PayForm in the [payform.md](../getting-started/integration-options/payform.md "mention") guide.
{% endhint %}

You can read about configuration specifics in the [#payform-builder](../getting-started/integration-options/payform.md#payform-builder "mention") section of our full PayForm guide. For the purpose of this tutorial, you can follow the example below; we'll briefly explain each configuration step.&#x20;

#### PayForm manual card sale

In the example below, the PayForm has been setup for **an instant card payment**.&#x20;

<figure><img src="../../.gitbook/assets/PayForm manual card sale 1.png" alt=""><figcaption></figcaption></figure>

<figure><img src="../../.gitbook/assets/PayForm manual card sale 2.png" alt=""><figcaption></figcaption></figure>

<figure><img src="../../.gitbook/assets/PayForm manual card sale 3.png" alt=""><figcaption></figcaption></figure>

<figure><img src="../../.gitbook/assets/PayForm manual card sale 4.png" alt=""><figcaption></figcaption></figure>

<figure><img src="../../.gitbook/assets/PayForm manual card sale 5.png" alt=""><figcaption></figcaption></figure>

{% stepper %}
{% step %}
#### Visible and read-only fields

The cardholder will need to provide their first and last names, full address, email, and click a checkbox to agree to pay and give their permissions to receive an email.

Additionally, they'll see the amount field, but it'll be read-only.
{% endstep %}

{% step %}
#### Submission options

The PayForm will redirect the user to an external URL. An encrypted query string containing the POST data will also be appended to the URL&#x20;
{% endstep %}

{% step %}
#### Styling and colors

The styling and colors were left as default, only switching out the button background and border to different shades of green.
{% endstep %}

{% step %}
#### Pre-filled values

The amount will be pre-filled as $25, the redirect URL is using an example URL to your website, and the EIndex is using the sandbox value for encryption key. Endpoint value should always be left as default.
{% endstep %}
{% endstepper %}

The JSON will look like the following:

{% code title="PayForm JSON example" %}
```json
{
  "InitParams": {
    "MerchID": 1,
    "WTYPE": "PF",
    "PostURL": "",
    "RedirectURL": "https://yourwebsite.com/success",
    "REF_ID": "",
    "RPGUID": "",
    "EndPoint": "PayForm/PF.aspx",
    "EINDEX": "300",
    "Amounts": {
      "Amount": 25,
      "Surcharge": 0,
      "TotalAmt": 25
    },
    "Payer": {
      "Firstname": "",
      "Lastname": "",
      "BillingAddress": {
        "StreetAddress": "",
        "City": "",
        "State": "",
        "ZIP": "",
        "Country": ""
      },
      "Email": "",
      "Phone": ""
    },
    "WidOptions": {
      "eVisible": "6E7F",
      "eReadOnly": "0040",
      "eStyles": "0001",
      "eSubmission": "0201",
      "eColors": "#ffffff,#6cca44,#59ff00,#212121,#ffffff,#212121,#ffffff"
    }
  }
}
```
{% endcode %}

**This JSON can be used to make a REST API request to generate the actual payment form.**&#x20;

You may re-use this JSON to generate the same type of form for multiple different users. You may also want to dynamically configure values like the amounts from your code.

{% hint style="success" %}
To generate a PayForm, make a request to [#payform-initialize](../../api-reference/rest-api/payform-1.md#payform-initialize "mention").&#x20;
{% endhint %}

If you include a valid session key, the PayForm will be accessible under the `PaymentUrl` included in the response. You can embed it into your site or redirect the user to the page.

Once the user fills out and submits the form, we'll handle the payment.

If you want to handle the query string when redirecting back to your website to store the transaction ID in your database, read the [#redirect-with-query-string](../getting-started/integration-options/payform.md#redirect-with-query-string "mention") section of our full PayForm guide.

#### PayForm manual consent

To use the PayForm to save a card on file, follow the steps in [#payform-manual-card-sale](card-sales-and-consent.md#payform-manual-card-sale "mention"), change the transaction type to collecting cardholder data, and skip the amount field.

You may also collect an instant payment and consent at the same time by choosing the combo widget as your transaction type.



### Virtual Terminal or desktop application

The Virtual Terminal is a web application that allows you to manually enter credit card details and process transactions through your browser.&#x20;

{% hint style="info" %}
To learn more about using the Virtual Terminal, see the [virtual-terminal.md](../getting-started/integration-options/virtual-terminal.md "mention") user guide.
{% endhint %}

{% hint style="info" %}
Read more about using our custom desktop application for sales in the [integration-options](../getting-started/integration-options/ "mention") guide or [contact Number](../../help/customer-support/) to get access.
{% endhint %}

#### Virtual Terminal manual card sale

When you visit the Virtual Terminal, log in and expand _Credit Cards_ in the navigation on the left. You'll see options for a sale, an EMV sale, authorization, forced auth, and adjustments. Follow the instructions and manually enter the cardholder details to make a sale.

<figure><img src="../../.gitbook/assets/Virtual Terminal card present sales (1).png" alt=""><figcaption></figcaption></figure>

#### Virtual Terminal manual consent

Using the Virtual Terminal, you can create annual, one-time, recurring, and subscription consents. Log in and expand _Consents_ and _Recurring_ tabs on the left side of the screen. Choose the type of consent you're interested in and follow the instructions to manually enter the cardholder details and store a card on file.

<figure><img src="../../.gitbook/assets/Virtual Terminal manual consent (1).png" alt=""><figcaption></figcaption></figure>



### Android / iOS SDK integration

If you are developing an Android or iOS application, you can utilize our SDKs to charge credit cards and collect consent manually by having users enter their own details.&#x20;

{% hint style="info" %}
We recommend following the [android-sdk.md](../getting-started/integration-options/android-sdk.md "mention") and [ios-sdk.md](../getting-started/integration-options/ios-sdk.md "mention") guides to learn how to integrate Number with your mobile applications.
{% endhint %}

#### Mobile manual card sale

The relevant methods are described in [#id-1.-charge-credit-card](../getting-started/integration-options/android-sdk.md#id-1.-charge-credit-card "mention") section of the [android-sdk.md](../getting-started/integration-options/android-sdk.md "mention") guide and [#id-1.-charge-credit-card](../getting-started/integration-options/ios-sdk.md#id-1.-charge-credit-card "mention") section of the [ios-sdk.md](../getting-started/integration-options/ios-sdk.md "mention") guide.&#x20;

#### Mobile manual consent annual

The relevant methods are described in [#id-3.-create-annual-consent](../getting-started/integration-options/android-sdk.md#id-3.-create-annual-consent "mention") section of the [android-sdk.md](../getting-started/integration-options/android-sdk.md "mention") guide and [#id-3.-create-annual-consent](../getting-started/integration-options/ios-sdk.md#id-3.-create-annual-consent "mention") section of the [ios-sdk.md](../getting-started/integration-options/ios-sdk.md "mention") guide.&#x20;



### REST API integration

If you wish to have more control over the integration and you are PCI Level 1 compliant, you can try using our APIs. They provide methods for all payment types available using our other services, including manual card sales and collecting different types of consent.

{% hint style="info" %}
To learn more about our APIs, see the [rest-api.md](../getting-started/integration-options/rest-api.md "mention") integration guide.
{% endhint %}

After authenticating, when you collect cardholder data alongside the other payment details, if using the REST API, prepare the HMAC secured header like shown in [authentication.md](authentication.md "mention") quickstart guide, and encrypt the card number using our RSA certificate. Follow the instructions in the API reference to prepare and handle the request.

#### Manual card sale

You can use the following API operations:

* For the REST API, use [#apicardprocrest-v1.0.0-cardsale-manual](../../api-reference/rest-api/card-operations-1/process-a-card-sale.md#apicardprocrest-v1.0.0-cardsale-manual "mention").

#### Manual consent

You can use the following API operations:

* For the REST API, use [#apicardprocrest-v1.0.0-consentannual-create\_man](../../api-reference/rest-api/consent-annual-1/create-annual-consent.md#apicardprocrest-v1.0.0-consentannual-create_man "mention") for annual consent and [#apicardprocrest-v1.0.0-consentrecurring-create](../../api-reference/rest-api/consent-recurring-1/create-recurring-consent.md#apicardprocrest-v1.0.0-consentrecurring-create "mention") for recurring consent.

