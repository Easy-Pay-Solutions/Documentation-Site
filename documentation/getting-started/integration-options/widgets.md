---
description: Getting started with widgets for Number
hidden: true
---

# Widgets

Widgets are our legacy option to collecting cardholder data and payments. If you are just getting started with Number, we recommend using the [payform.md](payform.md "mention") instead.

A Number widget is a pre-made web form which can be used to collect cardholder data. They can be used to make instant payments and collect consent.

After the widget has been submitted, we will pass relevant data to you as a webhook.



***



## Designing your widget

You can control the design of the form, the size, and the way data is populated and consumed. If you wish, you can also use the widget with standard options to make it as simple as possible.



### Considerations and options

* Is the widget going to be public-facing or practice-facing?
* Do you need to collect cardholder information, make instant sales, or both?
* What fields do you need to show to the user? (cardholder info...?)
* What information do you want to pass in the background as a hidden field? (`ReferenceID`, ...?)
* What fields should be pre-populated? (`Firstname`, `Lastname`, ...?)
* What fields can be altered by the user, and what should be read-only? (`Address`, `Amount`, ...?)
* How do you wish to POST the real-time values from the widget?
  * Redirect to the integrator site with encrypted values attached?
  * Have the widget contained in an iFrame and have it do a POST message to the parent page?
  * POST values to the integrator site without redirection, in the background?
* Do you need to redirect to Number receipt page, or consent agreement page?
* What should the widget be styled like? You can modify the size, colors, frame, etc.

You'll also need to know how you plan to use the widget in your workflow:

1. Embed the widget directly within your desktop or web application;
2. Direct your users to a dedicated top-level payment page;
3. Send the generated payment link directly to cardholders.



***



## Using an IFrame vs full page

### IFrame

An IFrame is a web container which can contain content from any domain. This has been an ideal method for our integrators to include a payment widget since it has become an integral part of their website. It creates an environment where the payment window becomes a part of the client site.

{% hint style="success" %}
Loading an IFrame with Number's widget or PayForm gives you 100% isolation from Cardholder data. **This provides excellent security and eliminates more costly PCI compliance programs.**
{% endhint %}

Do note that **our widget requires a session cookie**. Extra steps are required to utilize the IFrame approach. For example, Safari will block cookies from an IFrame if the parent page does not share the same domain. To resolve this, a subdomain can be created and served on our web farm.

{% hint style="info" %}
[PayForms](payform.md) do not utilize session cookies, there are no issues loading them as IFrames. This makes them preferable to using the widget.
{% endhint %}



### Full page

If you do not want to use an IFrame to host our payment widget, we can also develop a full-page payment display for you. You will open this page exactly the same as any widget (you may pre-populate some values as the page is opened).&#x20;

Once the user submits the payment, we can POST real-time data to your site in a number of ways. Usually, we will simply redirect back to your site with some ECHO values which allow your application to pick up where it left off prior to payment.

We encourage integrators to design their own payment page if they so desire. You can supply HTML / CSS / JavaScript / jQuery for us to include and modify in our secure PCI Level One environment.



***



## Creating your widget

To open your widget, first you need to create a string manifest that will eventually become an encrypted URL. There are two ways to create this manifest:&#x20;

1. Using our widget builder tool.
2. Creating it yourself using your programming language of choice.

{% hint style="warning" %}
If you want to use advanced options such as dynamically pre-populating form data, you will need to program the widget manifest without the tool!
{% endhint %}



### Widget builder tool

<figure><img src="../../../.gitbook/assets/PayForm builder.png" alt=""><figcaption></figcaption></figure>

Use our widget builder tool to select various settings, options, and styles. The widget manifest and encrypted URL will be generated for you.

{% include "../../../.gitbook/includes/link-widget-builder.md" %}

Most of the options should be easy to understand or described in the footer of the tool. If you have any questions, please refer to the [#payform-builder](payform.md#payform-builder "mention") guide or [contact Number](../../../help/customer-support/).



### Programming the widget

If you need to open the widget with dynamic content, you will have to do some programming. This is also true if you need to consume real-time data after the widget is submitted.&#x20;

{% hint style="info" %}
If you only need a widget for users to submit payments and need no dynamic content or real-time postings, we can provide you with an encrypted URL to place in your product.
{% endhint %}

In order to open a widget for collecting credit card information, first you must create a widget manifest. This is a string which is has two components: `Key` and `Inputs`.

#### Key parameter

For `Key`, you need to enter your Number credentials. You can either use your account code and token or a session key. You can read more about those parameters in [authentication.md](../basics/authentication.md "mention").

Examples:

{% code title="AccountCode and Token" overflow="wrap" %}
```url
?Key=EP2944916|0EDED2AE63D748079FBCFEB552A93A16
```
{% endcode %}

{% code title="Session Key (preferred)" overflow="wrap" %}
```url
?Key=AABAF6C95552447D8B303031353341303032303634
```
{% endcode %}

#### Inputs parameter

For `Inputs`, you add parameters which can configure the widget, pre-populating the widget with values, directing us where to post the results, etc. **Each parameter should be separated from its value and the following arguments by a pipe "|" symbol.**&#x20;

Example:

{% code overflow="wrap" %}
```url
&inputs=MERCHID|2|WTYPE|P|REFID|1234|RPGUID|5678|FIRSTNAME|John|LASTNAME|Doe|ADDRESS1|123 Fake St|ADDRESS2|Apt 2|CITY|Scarborough|STATE|ME|ZIP|04074|AMOUNT|16.75|REDIRECT|https://easypay7.com/PostingApp
```
{% endcode %}

Here is a list of arguments you can use for `Inputs`:

* `MERCHID`: An integer which represents one of your merchant records. You will get this information when you board new accounts.
* `REFID`: Any custom unique identifier to describe this particular cardholder or transaction. You can then query our database at a later time to find records based on this reference ID.
* `FIRSTNAME`: (optional)
* `LASTNAME`: (optional)
* `ADDRESS1`: (optional)
* `ADDRESS2`: (optional)
* `CITY`: (optional)
* `STATE`: (optional)
* `ZIP`: (optional)
* `AMOUNT`: For a one-time payment widget, the $ amount for the transaction.
* `WTYPE`: The type of widget to use. Use "_P_" for testing and [contact Number](../../../help/customer-support/) for more details.
* `REDIRECT`: URL where we can POST the results of the widget submission.&#x20;

{% hint style="info" %}
When we POST the results of the widget to the redirect URL of your choice, if you are storing a card-on-file, we will provide information such as a `ConsentID` which will allow you to charge this card at a later time, and if you are collecting a payment, we will provide the `TransactionID` so that you may do operations such as voiding, etc.
{% endhint %}

#### Manifest encryption

Once you have developed your string manifest, you will now need to encrypt it using AES 256. **You will be issued a unique encryption key when you begin to process live transactions.** Until then, you are encouraged to use the Number development sandbox key.

{% code title="Sandbox encryption key" overflow="wrap" %}
```
A142278ED69B3FE6C5E8F63CB8205F519F3A82BEA9CB2719938DB88D5C35EC60
```
{% endcode %}

Whenever you use this key, you will append the following to your encrypted URL, so that we know which encryption key you are using:

{% code title="Sandbox EINDEX value" overflow="wrap" %}
```url
EINDEX=300
```
{% endcode %}

{% hint style="danger" %}
**Make sure to swap the sandbox encryption key and EINDEX value when you switch to running a production environment!**&#x20;
{% endhint %}

In all cases, encrypt the above manifest and create two components:&#x20;

* an initialization vector (`I`)
* an encrypted message (`M`)

Gather the widget manifest and encrypt it. The final step is to create the URL using the template.

{% code title="Widget URL template" overflow="wrap" %}
```url
https://{assigned URL}/?m={encrypted msg}&i={init vector}&Eindex={your EIndex}
```
{% endcode %}



See examples below:

{% code title="Example parameters" overflow="wrap" %}
```url
?Key=EP2944916|0EDED2AE63D748079FBCFEB552A93A16&inputs=MERCHID|2|WTYPE|PN|REFID|1234|RPGUID|5678|FIRSTNAME|John|LASTNAME|Doe|ADDRESS1|123 Fake St|ADDRESS2|Apt 2|CITY|Scarborough|STATE|ME|ZIP|04074|AMOUNT|16.75|REDIRECT|https://easypay7.com/PostingApp
```
{% endcode %}

{% code title="Example encrypted URL" overflow="wrap" %}
```url
https://easypay5.com/stdwidget/?m=wphl1A6AdqOSqIdKFOSn88QavjhU9YwpCGrJlcoleDGtWrXeoDUcFXK2tlYD8sfhr0pXZbcBBQaS0fmZXNSG9MbxcveD4WqauFKL3d/ev7SlmfxDshPQhLhkGN9aHYQKby+7iWaSu4UfNmGd/53Ot275LsJ1AA/MaB+u5h7xRbY2+Oa5o0Dq3C7PDcH+pnpYQxgDKOiDERCBCdVHXdi9tfk9AqbhbAnXXr0PIAVfjIWA/Q7kDBLK2MooQNPyNw6h+QVQFJFNrfb4hbRp8VYJVOOLFO3hB/Fj1+jrSSeteORJw1LuUK2ekJUB15enIC6CyDtsU9NkAex9FT7O6GhDxN77PDdYhxpkwMI9KiiLUCffVtS2KQdHO9g7Uo56+z3lAFRzn6gX7mcvjAmnGiNa+kydZkWx9KKSWRHORGKl1IydupV0B7wJRFRbikDoxINbhCg2GCD5W8+pOc8KxctCjw==&i=Uw/DOxrBSY4X1alDyxpB0A==&Eindex=300
```
{% endcode %}

{% hint style="success" %}
If you want to quickly test your encryption, you can use our [encryption utility](https://easypayconfig.com/DocumentationPublish/Encryption.aspx).
{% endhint %}



***



## Getting real-time data

There are a few methods you can use to POST data to your product when the widget is submitted:

1. Provide a redirect URL in the string manifest to receive an encrypted message;
2. Provide a URL where we can POST values;
3. If you display the widget using an IFrame, you can choose a POST message to the parent page.

If you provided a redirect URL, we will POST data to your site as follows:&#x20;

```
https://yoursite.com/yourpage.aspx?m=xxxxx&i=xxxxxx
```

You will read the `m` and `i` values and decrypt using the same encryption scheme, and the same key you used to open the widget.&#x20;

{% hint style="danger" %}
**Replace any space ' ' characters with plus '+' characters prior to decrypting the base64 string. These can be altered during URL encoding.**
{% endhint %}

Here is some typical decrypted data:

```
CONSENTID|1664|CARDNO|5439|CARDTYPE|Visa|FIRSTNAME|Bob|LASTNAME|smith|REFID|324889
```

```
TRANSACTIONID|174|CARDNO|5339|CARDTYPE|Amex|FIRSTNAME|Bob|LASTNAME|smith|REFID|7899
```



***



## Additional processing with APIs

Having integrated the widget into your application, now that the cardholder data is in our system, you can use our APIs for additional processing. This includes charging consents, crediting payments, voiding transactions, and running reports.

To learn more, see our [rest-api.md](rest-api.md "mention") guide.



