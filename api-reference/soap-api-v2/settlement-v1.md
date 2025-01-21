---
description: Methods related to settlements
---

# Settlement (v1)

## Settle Merchant Transactions - All Open

<mark style="color:green;">`POST`</mark> /ICardProcess/Settlement\_ExecuteBatch\_All

Settle all open transactions (credit card charges) for the specified merchant.

{% tabs %}
{% tab title="Request body" %}
{% include "../../.gitbook/includes/param-sess-key.md" %}

***

{% include "../../.gitbook/includes/param-merchid.md" %}
{% endtab %}

{% tab title="Response body" %}
{% include "../../.gitbook/includes/param-ok-msg-errs.md" %}

***

{% include "../../.gitbook/includes/param-batch-result.md" %}
{% endtab %}
{% endtabs %}

***

## Settle Merchant Transactions - Selective

<mark style="color:green;">`POST`</mark> /ICardProcess/Settlement\_ExecuteBatch\_Selective

Settle open transactions (credit card charges) for the specified merchant by transaction IDs.

{% tabs %}
{% tab title="Request body" %}
{% include "../../.gitbook/includes/param-sess-key.md" %}

***

TxIDs array\<int>

A list of transactions to settle by ID.

***

{% include "../../.gitbook/includes/param-merchid.md" %}
{% endtab %}

{% tab title="Response body" %}
{% include "../../.gitbook/includes/param-ok-msg-errs.md" %}

***

{% include "../../.gitbook/includes/param-batch-result.md" %}
{% endtab %}
{% endtabs %}

