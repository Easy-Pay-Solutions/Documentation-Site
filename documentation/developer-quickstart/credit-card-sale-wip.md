---
description: Learn to make credit card sales with Number
---

# Credit Card Sale (WIP)

<figure><img src="../../.gitbook/assets/Credit card sale 2 (2).png" alt=""><figcaption></figcaption></figure>

## Card present sales

To make credit card present sales using Number, you have several options:

{% stepper %}
{% step %}
**Integration with a Verifone card reader**

You can use Verifone card readers, which are secure devices that connect to your computer via USB. They encrypt cardholder data during transmission to ensure security.
{% endstep %}

{% step %}
#### Any USB card reader through the Virtual Terminal or our custom desktop app

When you have a USB card reader connected to your machine, you can log into the Virtual Terminal to make card present sales.&#x20;

We also have a custom desktop application which can be convenient in an office setting to collect card present payments. It offers much of the same functionality as the Virtual Terminal.
{% endstep %}

{% step %}
#### A custom integration with our REST API or SOAP API

Both our REST API and SOAP API offer methods for handling card present transactions.

If you have your own PCI level one compliance program, you may use our APIs and write your own custom code calling our APIs to collect card present payments. You can read more about PCI compliance in the short [#pci-compliance](../getting-started/integration-options/#pci-compliance "mention") section of our integration guide.
{% endstep %}
{% endstepper %}



### Verifone integration

There are a few approaches to integration, but we recommend the browser-based interface option.&#x20;

Before you start, you'll need to download the [Verifone Windows service](https://easypay1.com/deploy/MiddleWare/EPVerifoneSetup_E2E_1041.zip) to your machine, connect your card reader device to a free USB port, allow it to initialize, extract the archive with the service and run the EXE as an administrator. After the installation is complete, reboot the system.

Now, you'll be able to issue commands to the Win service by calling `https://localhost:8031` from your website. Here's an simplified example of how you can invoke the service:

{% tabs %}
{% tab title="JavaScript" %}
{% code overflow="wrap" lineNumbers="true" %}
```javascript
// Initiates CHIP transaction
function initiateEMVTransaction() {
    // You must either supply a session key for authentication or modify your eptools profile to point to a particular account
    // You may modify your stored profile at c:\ProgramData\EasyPay\Eptools\eptools\profiles
    const sessKey = getSessKey();
    
    // Each account can have multiple merchant records. Normally this can be '1' for default if you only have one merchant on account.
    const merchID = getMerchId();
    
    // Note: any 'address' field should be an object consisting of:
    // 'Address1', 'Address2', 'City', 'State', 'ZIP', and 'Country'
    
    // The account holder and end customer JSONs should consist of:
    // 'Firstname', 'Lastname', 'address' (see above), 'Email', and 'Phone'
    const acctHolderJson = getAcctHolderJson();
    const endCustJson = getEndCustJson();
    
    // Purchase details should consist of the following fields:
    // 'REFID' and 'RPGUID' (your custom defined values), and 'ServiceDesc'
    const purchDetailsJson = getPurchDetailsJson();

    // The amount needs to be stripped from '$' and ',' symbols
    let amount = getAmount();
    amount = amount.replace('$', "").replace(',', ""); 

    const url = `https://localhost:8031/VerifoneSVC/service/GetEmvJson?SessKey=${sessKey}&AcctHolderJson=${acctHolderJson}&EndCustJson=${endCustJson}&PurchDetailsJson=${purchDetailsJson}&MerchID=${merchID}&Amount=${amount}`;

    // Make the call to the service and do basic error/success handling
    $.ajax({
        type: "GET",
        url: url,
        success: function (data) {
            // Hex to byte array, then UTF text, and alert the XML object
            alert(stringFromUTF8Array(hexToBytes(data)));
        },
        error: function (xhr, status, error) {
            console.error("Verifone Middleware Error", {
                statusCode: xhr.status,
                statusText: xhr.statusText,
                error: error
            });
            alert(`Verifone Middleware Error: ${error}`);
        }
    });
}
```
{% endcode %}
{% endtab %}
{% endtabs %}

{% hint style="info" %}
For an in-depth tutorial on how to integrate and use your Verifone card reader with Number, see our [verifone.md](../getting-started/integration-options/verifone.md "mention") integration guide.
{% endhint %}



### Virtual Terminal

When you want to use your USB card reader with the Virtual Terminal, you have to first install the very same [Windows service](https://easypay1.com/deploy/MiddleWare/EPVerifoneSetup_E2E_1041.zip) that is used when doing a Verifone browser-based integration. After installation, [contact the Number support team](../../help/customer-support/) to get the card reader features activated.

When you visit the Virtual Terminal, log in and expand _Credit Cards_ in the navigation on the left. You'll see options for a sale, an EMV sale, authorization, forced auth, and adjustments. As long as your USB card reader is connected to your machine, it will seamlessly integrate with the Virtual Terminal.

<figure><img src="../../.gitbook/assets/image.png" alt=""><figcaption></figcaption></figure>

{% hint style="info" %}
To learn more about using the Virtual Terminal, see the [virtual-terminal.md](../getting-started/integration-options/virtual-terminal.md "mention") user guide.
{% endhint %}



### Custom desktop application

{% hint style="info" %}
Read more about using our custom desktop application for sales in the [integration-options](../getting-started/integration-options/ "mention") guide or [contact Number](../../help/customer-support/) to get access.
{% endhint %}





### REST / SOAP API integration

If you wish to have more control over the integration and you are PCI Level 1 compliant, you can try using our APIs. They provide methods for all payment types available using our other services, including card present payments.

{% include "../../.gitbook/includes/warning-pci-compliant-only.md" %}

You can use the following API operations:

* For the REST API, use [#apicardprocrest-v1.0.0-cardsale-cardpresent](../../api-reference/rest-api/card-operations/process-a-card-sale.md#apicardprocrest-v1.0.0-cardsale-cardpresent "mention")
* For the SOAP API, use [#credit-card-sale-card-present](../../api-reference/soap-api/credit-card/credit-card-sale.md#credit-card-sale-card-present "mention").

After authenticating, when you scan the credit card and collect the track data alongside the other payment details, prepare the HMAC secured header like shown in [authentication.md](authentication.md "mention") quickstart guide, and encrypt the card number using our RSA certificate. Follow the instructions in the API reference to prepare and handle the request.

{% hint style="info" %}
To learn more about our APIs, see the [rest-api.md](../getting-started/integration-options/rest-api.md "mention") and [soap-api.md](../getting-started/integration-options/soap-api.md "mention") integration guides.
{% endhint %}



***



## Manual card sales

To make manual credit card sales using Number, you have the following options:

{% stepper %}
{% step %}
#### Use a PayForm widget

You can configure and customize our PayForm widget and redirect your users to a separate page with the form or embed it as an iFrame in your existing web application.
{% endstep %}

{% step %}
#### Virtual Terminal or our custom desktop application

The Virtual Terminal website allows you to handle manual card sales by default. This approach requires no coding and is perfect for a physical point-of-sale.

We also have a custom desktop application which can be convenient way to collect manual card payments. It offers much of the same functionality as the Virtual Terminal.
{% endstep %}

{% step %}
#### Android or iOS SDK integration

If you have a mobile application that needs to handle payments, our SDKs implement secure forms which can collect payments from your users.
{% endstep %}

{% step %}
#### REST API or SOAP API integration

If you need more configuration, you can always call our APIs to collect manual card sales.

If you have your own PCI level one compliance program, you may use our APIs and write your own custom code calling our APIs to collect manual card payments. You can read more about PCI compliance in the short [#pci-compliance](../getting-started/integration-options/#pci-compliance "mention") section of our integration guide.
{% endstep %}
{% endstepper %}



### PayForm

The PayForm is designed to be a highly flexible and secure payment form for your users. To start collecting payments with the PayForm, you'll want to use our builder tool for configuration, then our REST API to generate a payment URL.&#x20;

{% include "../../.gitbook/includes/info-payform-builder.md" %}

You can read about configuration specifics in the [payform.md](../getting-started/integration-options/payform.md "mention") guide. For the purpose of this tutorial, you can follow the example below, we'll briefly explain each configuration step.&#x20;

#### Example

In the example below, the PayForm has been setup for **an instant card payment**.&#x20;

<figure><img src="../../.gitbook/assets/payform builder example 3.png" alt=""><figcaption></figcaption></figure>

{% stepper %}
{% step %}
#### Visible and read-only fields

The user (cardholder) will need to provide their first and last names, full address, email, and click a checkbox to agree to pay and give their permissions to receive an email.

Additionally, they'll see the amount field, bu tit'll be read-only.
{% endstep %}

{% step %}
#### Submission options

The PayForm will redirect the user to an external URL. An encrypted query string containing the POST data will also be appended to the URL&#x20;
{% endstep %}

{% step %}
#### Styling and colors

The styling and colors were mostly left on default, only switching out the button background and border to shades of green.
{% endstep %}

{% step %}
#### Pre-filled values

The amount will be pre-filled as $25, the Redirect URL is using an example URL to your website, and the EIndex is using the sandbox value for encryption key. EndPoint should be left as default.
{% endstep %}
{% endstepper %}

\
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
      "eColors": "#ffffff,#7aca44,#73ff00,#212121,#ffffff,#212121,#ffffff"
    }
  }
}
```
{% endcode %}

**This JSON can be used to make a REST API request to generate the actual payment form.**&#x20;

You may re-use this JSON to generate the same type of form for multiple different users. You may also want to dynamically configure values like the amounts from your code.

{% hint style="success" %}
To generate a PayForm, make a request to [#payform-initialize](../../api-reference/rest-api/payform.md#payform-initialize "mention").&#x20;
{% endhint %}

If you include a valid session key, the PayForm will be accessible under the `PaymentUrl` included in the response. You can embed it into your site or redirect the user to the page.

Once the user fills out and submits the form, we'll handle the payment.

If you want to handle the query string when redirecting back to your website to store the transaction ID in your database, read the [#redirect-with-query-string](../getting-started/integration-options/payform.md#redirect-with-query-string "mention") section of our full PayForm guide.

{% hint style="info" %}
Learn more about how to configure and use the PayForm in the [payform.md](../getting-started/integration-options/payform.md "mention") guide.
{% endhint %}



### <mark style="background-color:orange;">Virtual Terminal</mark>

The Virtual Terminal is a web application that allows you to manually enter credit card details and process transactions through your browser. This option is suitable for businesses that need to process payments without a physical terminal 4 5 .



### Custom desktop application

{% hint style="info" %}
Read more about using our custom desktop application for sales in the [integration-options](../getting-started/integration-options/ "mention") guide or [contact Number](../../help/customer-support/) to get access.
{% endhint %}



### <mark style="background-color:orange;">Android / iOS SDK integration</mark>

* If you are developing an Android application, you can utilize the Number Android SDK to charge credit cards manually. The method`ChargeCreditCard().chargeCreditCard(params: ChargeCreditCardBodyParams)`allows you to process credit card transactions by entering the card details manually 3 .
* **Request Parameters**:
  * `encryptedCardNumber`: Securely handle the card number.
  * `creditCardInfo`: Include details like expiration date and CVV.
  * `accountHolder`: Information about the cardholder 3 .



### <mark style="background-color:orange;">REST / SOAP API integration</mark>

* You can process a manual card sale using the`/ICardProcess/CreditCardSale_Manual`API endpoint. This requires sending a POST request with the necessary credit card information, including the account number, expiration date, CVV, and account holder details 1 .
* **Request Parameters**:
  * `SessKey`: A unique session key for authentication.
  * `ccCardInfo`: Contains the credit card details (AccountNumber, ExpMonth, ExpYear, CSV).
  * `AcctHolder`: Information about the account holder 2 1 .



