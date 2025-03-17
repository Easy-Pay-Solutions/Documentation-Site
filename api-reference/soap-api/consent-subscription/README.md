---
description: Methods related to creating and modifying subscription consent
---

# Consent Subscription

## Create Subscription Consent - Card Present

<mark style="color:green;">`POST`</mark> /ICardProcess/ConsentAnnual\_Create\_CP

Create a subscription payment plan with a specific $ amount paid per time period. The credit card data is supplied by reading the magnetic stripe via a card reader device.

{% tabs %}
{% tab title="Request body" %}
***

***

***

***
{% endtab %}

{% tab title="Response body" %}
***

***
{% endtab %}
{% endtabs %}





## Create Subscription Consent - Manual

<mark style="color:green;">`POST`</mark> /ICardProcess/ConsentAnnual\_Create\_MAN

Create a subscription payment plan with specified $ amount paid per time period.The credit card data is supplied by manually.

{% tabs %}
{% tab title="Request body" %}
***

***

***

***
{% endtab %}

{% tab title="Response body" %}
***

***
{% endtab %}
{% endtabs %}





## Modify Subscription Consent&#x20;

<mark style="color:green;">`POST`</mark> /ICardProcess/ConsentAnnual\_Modify

Update the subscription payment and expiration date information. Does not alter the credit card associated with the consent.

{% tabs %}
{% tab title="Request body" %}
***

***

`ConsentMods` api\_ConsentSubscriptionEditor (object)

Fields: ExpMonth, ExpYear, Email, Zip, RPGUID, CustomerRefID, ServiceDescrip, PaymentAmt, PaymentAdjustDate, OnHold.
{% endtab %}

{% tab title="Response body" %}
***
{% endtab %}
{% endtabs %}





## Cancel Subscription Consent&#x20;

<mark style="color:green;">`POST`</mark> /ICardProcess/ConsentAnnual\_Cancel

Cancel the subscription plan and removes the credit card information.

{% tabs %}
{% tab title="Request body" %}
***
{% endtab %}

{% tab title="Response body" %}
***
{% endtab %}
{% endtabs %}



