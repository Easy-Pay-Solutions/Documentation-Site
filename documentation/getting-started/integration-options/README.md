---
description: Learn about how you can integrate with Number
---

# Integration Options

Before you start using our services, you'll want to decide which type of integration is most suited to your business case. We provide a plethora of ways to start using our services:

* REST and SOAP APIs
* Mobile SDKs for Android and iOS
* PayForm and legacy widgets
* The Virtual Terminal web application
* Desktop applications
* Dynamic Link Libraries (DLLs)

**You don't have to limit yourself to one type of integration.** Many integrators use our PayForm to collect the cardholder data, and then use our API for the rest. The Virtual Terminal can also be used for various functions such as processing payments, creating card-on-file plans (consents), and generating reports. You can find more details about each integration in the next few sections.

Before you read about the specific integration options, we recommend having a look at the PCI Compliance section below to help you clarify which options are relevant to your unique case.



***



## PCI Compliance

### What is PCI DSS?

PCI compliance refers to adherence to the Payment Card Industry Data Security Standard (PCI DSS), which is a set of security standards related to processing, storing, and transmitting credit card information. The PCI DSS was developed by the Payment Card Industry Security Standards Council (PCI SSC), which was founded by major credit card companies like Visa, MasterCard, American Express, Discover, and JCB.



{% hint style="info" %}
Some key aspects of PCI compliance include:

1. **Maintaining Secure Networks and Systems**: Installing and maintaining a firewall configuration to protect cardholder data and not using vendor-supplied defaults for system passwords and other security parameters.
2. **Protecting Cardholder Data**: Companies must protect stored cardholder data and encrypt transmission of cardholder data across open, public networks.
3. **A Vulnerability Management Program**: Using and regularly updating antivirus software.
4. **Strong Access Control Measures**: Access to cardholder data should be restricted by business need-to-know, with a unique ID assigned to each person with computer access, and restricted physical access to cardholder data.
5. **Regular Monitoring and Network Tests**: Tracking and monitoring all access to network resources and cardholder data, regularly testing security systems and processes.
6. **An Information Security Policy**: Companies must maintain a policy that addresses information security for all personnel.
{% endhint %}



PCI compliance helps protect cardholder data from theft and fraud, ensuring consumer trust and avoiding fines and penalties associated with non-compliance. Businesses of all sizes that handle credit card information are **required** to comply with PCI DSS.



### Integration choice based on compliance

**If you are not already handling cardholder data by yourself, Number can do that for you.**

Depending on whether or not you are handling the card holder data under your own documented PCI level one compliance program, you'll want to use different types of integrations.&#x20;

1. If you have your own PCI level one compliance program umbrella, you may use our APIs for all types of payment activities, including authorization of cards, issuing credits, reversal, reports, etc.
2. Otherwise, you can use our PayForm web widget and other applications served under our PCI Level One platform to collect cardholder data, and use our API for any and all other payment-related activities.



***



## REST & SOAP APIs

Both APIs will allow you to enable integration of Number payments with external applications, allowing for full automation and a high degree of customization.&#x20;

They allow a variety of functions:&#x20;

* Processing payments / voids / credits / settlements,&#x20;
* Runing queries and reports,&#x20;
* Returning receipts and documents for signature,&#x20;
* Creating / modifying / processing payment plans.

You don't need to use both of the APIs, they share similar functionality. **We recommend starting with the REST API as our modern option.** We continue to have both of the APIs supported.

It's important to note that some API functionality will require you to collect cardholder data, such as [Processing a card sale with card present](../../../api-reference/rest-api/card-operations/process-a-card-sale.md#apicardprocrest-v1.0.0-cardsale-cardpresent), and that requires you to be PCI Level 1 compliant. You can overcome this by using our PayForm to collect all cardholder data securely.

You can read more about implementation in the [rest-api.md](rest-api.md "mention") and [soap-api.md](soap-api.md "mention") integration guides.



***



## Android and iOS SDKs

The mobile SDKs will allow you to integrate Number payments services into any Android and iOS application using the prebuilt payment UI components. Similar to PayForm, those components will allow you to collect cardholder data and process payments in a secure and PCI compliant way.

If you need to integrate Number payments with a mobile application, we recommend using this approach.

You can read more about implementation in the [android-sdk.md](android-sdk.md "mention") and [ios-sdk.md](ios-sdk.md "mention") integration guides.



***



## PayForm and legacy widgets

A PayForm is the most convenient means of collecting cardholder data. By using our builder tool or our API, you'll be able to set the design and behavioral aspects of the form and we'lll return a URL which loads it into the view. The form will then use webhooks to POST the realtime data to the site of your choice.

Once the cardholder data is collected, you can use other integrations, such as our APIs or the Virtual Terminal, to process consents, credit, void, and query transactions.

We also have a widget as a legacy option to the PayForm. With this widget, users will enter their cardholder data directly into the Number platform, and your system can be updated in realtime. **If you're just starting, we suggest using the PayForm as our modern option.**

We recommend using the PayForm to collect all cardholder data when integrating with web applications as it's secure, easy to get started, and offers a lot of customization.&#x20;

You can read more about implementation in the [payform.md](payform.md "mention") and [widgets.md](widgets.md "mention") integration guides.



***



## Virtual Terminal

The Virtual Terminal (VT) is a web application which you can access through your browser. It provides all types of credit card processing functionality:

* Authorizations,
* Voids / credits / settlements,
* Reporting,
* Payment plans (recurring / subscription consent),
* Card-on-file (Annual consent).

The VT is the fastest way to start trying out our payment services. Otherwise, it's ideal for businesses processing payments over the phone or at sales points lacking a physical terminal.

You can read more about the Virtual Terminal in the [virtual-terminal.md](virtual-terminal.md "mention") user guide.



***



## Our custom desktop application

We also have a custom desktop application which can be convenient in an office setting to collect card present payments. This application offers much of the same functionality as the Virtual Terminal. As opposed to the Virtual Terminal, the desktop app only requires you to authenticate once a day to keep your session.

The application interfaces with VeriFone card readers. These devices accept EMV chip and contactless cards in addition to the usual card swipe and manual entry.&#x20;

{% hint style="info" %}
[Contact us](../../../help/customer-support/) to learn more about custom desktop applications.
{% endhint %}



***



## Win service and DLLs for the Verifone

If you wish, you can take advantage of our end-to-end encryption model used with the Verifone card reader and build around it by referencing our Dynamic Link Library. The DLL will channel its requests through our API and responses can be consumed at the client software product. This way, you can develop your own workflow and displays.

You can read more about integrating with Verifone in the [verifone.md](verifone.md "mention") integration guide.



