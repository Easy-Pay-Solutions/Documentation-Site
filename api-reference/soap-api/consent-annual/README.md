---
description: Methods related to creating and modifying annual consent
---

# Consent Annual

## Create Annual Consent - Card Present

<mark style="color:green;">`POST`</mark> /ICardProcess/ConsentAnnual\_Create\_CP

Create an annual consent by sending the credit card details to the processor via a card reader device. Use when the card is present and you can scan the magnetic stripe.

{% tabs %}
{% tab title="Request body" %}
{% include "../../../.gitbook/includes/param-sess-key.md" %}

***

{% include "../../../.gitbook/includes/param-track.md" %}

***

{% include "../../../.gitbook/includes/param-consent-annual-creator.md" %}

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





## Create Annual Consent - Manual

<mark style="color:green;">`POST`</mark> /ICardProcess/ConsentAnnual\_Create\_MAN

Create an annual consent by sending the credit card details, which include: card number, expiration date, CVV, and card holder contact data. Not created by swiping the card through a reader device.

{% tabs %}
{% tab title="Request body" %}
{% include "../../../.gitbook/includes/param-sess-key.md" %}

***

{% include "../../../.gitbook/includes/param-credit-card-info.md" %}

***

{% include "../../../.gitbook/includes/param-consent-annual-creator.md" %}

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





## Modify Annual Consent

<mark style="color:green;">`POST`</mark> /ICardProcess/ConsentAnnual\_Modify

Update the payment amounts, expiration, and customer reference information for an annual consent. Does not alter the credit card saved with the consent.

{% tabs %}
{% tab title="Request body" %}
{% include "../../../.gitbook/includes/param-sess-key.md" %}

***

{% include "../../../.gitbook/includes/param-consent-id.md" %}

***

`ConsentMods` api\_ConsentAnnualEditor (object)

Fields: ExpMonth, ExpYear, Email, Zip, CustomerRefID, ServiceDescrip, RPGUID, NumDays, LimitPerCharge, LimitLifeTime
{% endtab %}

{% tab title="Response body" %}
{% include "../../../.gitbook/includes/param-ok-msg-errs.md" %}

***

{% include "../../../.gitbook/includes/params-consent-modify-response.md" %}
{% endtab %}
{% endtabs %}





## Cancel Annual Consent

<mark style="color:green;">`POST`</mark> /ICardProcess/ConsentAnnual\_Modify

Cancel an annual consent and remove credit card data from the system.

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



