---
description: Methods related to creating and modifying subscription consent
---

# Consent Subscription (v1)

## Create Subscription Consent - Card Present

<mark style="color:green;">`POST`</mark> /ICardProcess/ConsentAnnual\_Create\_CP

Create a subscription payment plan with a specific $ amount paid per time period. The credit card data is supplied by reading the magnetic stripe via a card reader device.

{% include "../../../.gitbook/includes/info-process-scheduled-payments.md" %}

{% tabs %}
{% tab title="Request body" %}
{% include "../../../.gitbook/includes/param-sess-key.md" %}

***

{% include "../../../.gitbook/includes/param-track.md" %}

***

{% include "../../../.gitbook/includes/param-consent-sub-creator.md" %}

***

{% include "../../../.gitbook/includes/param-account-holder.md" %}

***

{% include "../../../.gitbook/includes/param-end-customer.md" %}
{% endtab %}

{% tab title="Response body" %}
{% include "../../../.gitbook/includes/param-ok-msg-errs.md" %}

***

{% include "../../../.gitbook/includes/params-consent-creation-results.md" %}

***

{% include "../../../.gitbook/includes/param-consent-id.md" %}
{% endtab %}
{% endtabs %}

***

## Create Subscription Consent - Manual

<mark style="color:green;">`POST`</mark> /ICardProcess/ConsentAnnual\_Create\_MAN

Create a subscription payment plan with specified $ amount paid per time period.The credit card data is supplied by manually.

{% include "../../../.gitbook/includes/info-process-scheduled-payments.md" %}

{% tabs %}
{% tab title="Request body" %}
{% include "../../../.gitbook/includes/param-sess-key.md" %}

***

{% include "../../../.gitbook/includes/param-credit-card-info.md" %}

***

{% include "../../../.gitbook/includes/param-consent-sub-creator.md" %}

***

{% include "../../../.gitbook/includes/param-account-holder.md" %}

***

{% include "../../../.gitbook/includes/param-end-customer.md" %}
{% endtab %}

{% tab title="Response body" %}
{% include "../../../.gitbook/includes/param-ok-msg-errs.md" %}

***

{% include "../../../.gitbook/includes/params-consent-creation-results.md" %}

***

{% include "../../../.gitbook/includes/param-consent-id.md" %}
{% endtab %}
{% endtabs %}

***

## Modify Subscription Consent&#x20;

<mark style="color:green;">`POST`</mark> /ICardProcess/ConsentAnnual\_Modify

Update the subscription payment and expiration date information. Does not alter the credit card associated with the consent.

{% tabs %}
{% tab title="Request body" %}
{% include "../../../.gitbook/includes/param-sess-key.md" %}

***

{% include "../../../.gitbook/includes/param-consent-id.md" %}

***

`ConsentMods` api\_ConsentSubscriptionEditor (object)

Fields: ExpMonth, ExpYear, Email, Zip, RPGUID, CustomerRefID, ServiceDescrip, PaymentAmt, PaymentAdjustDate, OnHold.
{% endtab %}

{% tab title="Response body" %}
{% include "../../../.gitbook/includes/param-ok-msg-errs.md" %}

***

{% include "../../../.gitbook/includes/params-consent-modify-response.md" %}
{% endtab %}
{% endtabs %}

***

## Cancel Subscription Consent&#x20;

<mark style="color:green;">`POST`</mark> /ICardProcess/ConsentAnnual\_Cancel

Cancel the subscription plan and removes the credit card information.

{% tabs %}
{% tab title="Request body" %}
{% include "../../../.gitbook/includes/param-sess-key.md" %}

***

{% include "../../../.gitbook/includes/param-consent-id.md" %}
{% endtab %}

{% tab title="Response body" %}
{% include "../../../.gitbook/includes/param-ok-msg-errs.md" %}

***

{% include "../../../.gitbook/includes/params-consent-cancel-response.md" %}
{% endtab %}
{% endtabs %}



