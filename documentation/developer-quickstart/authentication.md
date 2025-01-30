---
description: A quickstart guide to authenticating with Number services
---

# Authentication

<figure><img src="../../.gitbook/assets/Authenticate.png" alt=""><figcaption></figcaption></figure>

## Basics

In general, to authenticate to our services, depending on your use case, you'll need:

{% stepper %}
{% step %}
#### An account code and token

Using the unique key representing the Number account and the token generated from the Client Admin Portal which expires every 6 months, you'll be able to authenticate to both the REST and SOAP API.&#x20;
{% endstep %}

{% step %}
#### API key

When initializing either of the mobile SDKs, you'll need an API key provided by Number.&#x20;
{% endstep %}

{% step %}
#### HMAC secret

If you are PCI Compliant and want to use our APIs to collect cardholder data, some endpoints will require you to append additional data to the session header. With this, you'll be required to use an HMAC secret provided by us to generate this header.

{% include "../../.gitbook/includes/warning-hmac.md" %}
{% endstep %}

{% step %}
#### Username and password

When logging into the Virtual Terminal or the Client Admin Portal, you'll need a username and password. Those may also require two-factor authentication using a text message to your mobile phone.
{% endstep %}
{% endstepper %}

If you want to read more about authentication, see the [authentication.md](../getting-started/basics/authentication.md "mention") guide.



***



## REST and SOAP API

Here's a basic step-by-step guide on how to authenticate with our APIs:

{% stepper %}
{% step %}
#### Find your account code

This will be provided by Number when you create an account with us.
{% endstep %}

{% step %}
#### Create a new token

Use the Client Admin Portal to create a token. If you don't have access to the Client Admin Portal, contact the [Number support team](https://number-development-portal.gitbook.io/number-development-portal/kmuHipzA8ZCcM2LLePFe/help/customer-support).
{% endstep %}

{% step %}
#### Send a request to authenticate and store the session key

You'll need to provide your account code (`AcctCode`) and token (`Token`).

REST API: [#apicardprocrest-v1.0.0-authenticate](../../api-reference/rest-api/authentication.md#apicardprocrest-v1.0.0-authenticate "mention")\
SOAP API: [#authenticate](../../api-reference/soap-api/authentication.md#authenticate "mention")

Review the response and store the value of the `SessKey`.
{% endstep %}

{% step %}
#### Include the session key in your requests

**If you don't encounter a PCI Level 1 compliance warning in API reference page:**

For REST API, include a `SessKey` header with the stored value.\
For SOAP API, include a `SessKey` parameter in the request body.

**In case you encounter the compliance warning in API reference page, as seen below:**

{% include "../../.gitbook/includes/warning-pci-compliant-only.md" %}

You'll need to prepare a secured header and use its value in place of the original `SessKey`.&#x20;

If the HMAC secret was not provided to you previously or you don't know how to find the value of `UserID` or `DeviceID`, [contact Number](../../help/customer-support/).&#x20;

The format for the key is as follows: [`SessKey`](#user-content-fn-1)[^1]\_[`Epoch`](#user-content-fn-2)[^2]\_[`DeviceID`](#user-content-fn-3)[^3]\_[`Hash`](#user-content-fn-4)[^4].

{% include "../../.gitbook/includes/code-hmac.md" %}

Include the signature in the same way as the `SessKey` in the previous case.
{% endstep %}
{% endstepper %}



***



## Android and iOS SDK

Authenticating with the mobile SDKs is very simple. [Contact Number](../../help/customer-support/) to get an API key, HMAC secret, and an optional Sentry DSN.&#x20;

After installing the SDK of your choice, you can configure and initialize the `EasyPay` class.

#### Android

{% include "../../.gitbook/includes/block-android-config-ep.md" %}

#### iOS

{% include "../../.gitbook/includes/block-ios-configure-easypay.md" %}



***



## Virtual Terminal

To log in and use the features of Virtual Terminal, you'll first need to create accounts for your users through the Client Admin Portal.&#x20;

To access the portal, [Contact Number](../../help/customer-support/). You will be asked to provide the full name, e-mail address, and cell phone number for every individual you wish to have access to the portal. Those individuals will then be able to enter the portal and create new Virtual Terminal users through the portal by entering _Manage Accounts_ > _Users_ through the navigation on the left.

Now, those users will be able to access the Virtual Terminal using the link below.

{% embed url="https://easypay5.com/VT" %}





[^1]: This key is generated upon successful authentication.

[^2]: Seconds since 1970 UTC

[^3]: UserID or DeviceID

[^4]: The HMAC hash created using the secret value which we will provide.
