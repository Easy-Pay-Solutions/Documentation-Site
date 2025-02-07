---
description: Methods related to processing annual consent
---

# Process Annual Consent

## Process Annual Consent

<mark style="color:green;">`POST`</mark> /ICardProcess/ConsentAnnual\_ProcPayment

Use the credit card stored on file to process a payment for an existing consent.

{% tabs %}
{% tab title="Request body" %}
{% include "../../../.gitbook/includes/param-sess-key.md" %}

***

{% include "../../../.gitbook/includes/param-consent-id.md" %}

***

{% include "../../../.gitbook/includes/param-process-amount.md" %}
{% endtab %}

{% tab title="Response body" %}
{% include "../../../.gitbook/includes/param-ok-msg-errs.md" %}

***

{% include "../../../.gitbook/includes/param-tx-approved.md" %}

***

{% include "../../../.gitbook/includes/param-txid.md" %}

***

{% include "../../../.gitbook/includes/param-txncode.md" %}

***

{% include "../../../.gitbook/includes/param-avsr.md" %}

***

{% include "../../../.gitbook/includes/param-cvvr.md" %}

***

{% include "../../../.gitbook/includes/params-acquirer-opts-voice-opts-auth-balance.md" %}
{% endtab %}
{% endtabs %}





## Process Annual Consent - Alternative

<mark style="color:green;">`POST`</mark> /ICardProcess/ConsentAnnual\_ProcPayment\_Alt

Processes a credit card payment for an existing consent, but the payment is transferred to a different merchant than the original one.&#x20;

The alternate merchant must be previously assigned to the account holders' account.

{% include "../../../.gitbook/includes/info-alt-merchant.md" %}

{% tabs %}
{% tab title="Request body" %}
{% include "../../../.gitbook/includes/param-sess-key.md" %}

***

{% include "../../../.gitbook/includes/param-consent-id.md" %}

***

{% include "../../../.gitbook/includes/param-process-amount.md" %}

***

{% include "../../../.gitbook/includes/param-alternate-merchid.md" %}
{% endtab %}

{% tab title="Response body" %}
{% include "../../../.gitbook/includes/param-ok-msg-errs.md" %}

***

{% include "../../../.gitbook/includes/param-tx-approved.md" %}

***

{% include "../../../.gitbook/includes/param-txid.md" %}

***

{% include "../../../.gitbook/includes/param-txncode.md" %}

***

{% include "../../../.gitbook/includes/param-avsr.md" %}

***

{% include "../../../.gitbook/includes/param-cvvr.md" %}

***

{% include "../../../.gitbook/includes/params-acquirer-opts-voice-opts-auth-balance.md" %}
{% endtab %}
{% endtabs %}



