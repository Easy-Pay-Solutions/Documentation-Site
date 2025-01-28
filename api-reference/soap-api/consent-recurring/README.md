---
description: Methods related to creating and modifying recurring consent
---

# Consent Recurring

## Create Recurring Consent

<mark style="color:green;">`POST`</mark> /ICardProcess/ConsentRecurring\_Create

Creates a recurring consent. Depending upon user account settings, this also authorize the card for $0.

{% include "../../../.gitbook/includes/info-process-scheduled-payments.md" %}

{% tabs %}
{% tab title="Request body" %}
{% include "../../../.gitbook/includes/param-sess-key.md" %}

***

`ccCardInfo` api\_CardInfo2 (object)

Fields: AccountNumber, ExpMonth, ExpYear, CSV, Track

***

`ConsentCreator` api\_ConsentRecurringCreator (object)

Fields: MerchID, CustomerRefID, ServiceDescrip, RPGUID, StartDate, NumPayments, TotalAmount, Period

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

***

`MySched` List\<api\_SchedLine> (array\<object>)

Fields: SchedID, paymentNo, paymentAmt, paymentDate, Remaining
{% endtab %}
{% endtabs %}

***

## Modify Recurring Consent

<mark style="color:green;">`POST`</mark> /ICardProcess/ConsentRecurring\_Modify

Update the payment amounts, expiration, and customer reference information for a recurring consent. Does not alter the credit card saved with the consent.

{% tabs %}
{% tab title="Request body" %}
{% include "../../../.gitbook/includes/param-sess-key.md" %}

***

{% include "../../../.gitbook/includes/param-consent-id.md" %}

***

`ConsentMods` api\_ConsentRecurringEditor (object)

Fields: ExpMonth, ExpYear, Email, Zip, CustomerRefID, ServiceDescrip, RPGUID
{% endtab %}

{% tab title="Response body" %}
{% include "../../../.gitbook/includes/param-ok-msg-errs.md" %}

***

{% include "../../../.gitbook/includes/params-consent-modify-response.md" %}
{% endtab %}
{% endtabs %}

***

## Cancel Recurring Consent

<mark style="color:green;">`POST`</mark> /ICardProcess/ConsentRecurring\_Cancel

Cancel a recurring consent and remove credit card data from the system.

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

