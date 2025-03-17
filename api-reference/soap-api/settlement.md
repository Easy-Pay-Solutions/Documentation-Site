---
description: Methods related to settlements
---

# Settlement

## Settle Merchant Transactions - All Open

<mark style="color:green;">`POST`</mark> /ICardProcess/Settlement\_ExecuteBatch\_All

Settle all open transactions (credit card charges) for the specified merchant.

{% tabs %}
{% tab title="Request body" %}
***
{% endtab %}

{% tab title="Response body" %}
***
{% endtab %}
{% endtabs %}





## Settle Merchant Transactions - Selective

<mark style="color:green;">`POST`</mark> /ICardProcess/Settlement\_ExecuteBatch\_Selective

Settle open transactions (credit card charges) for the specified merchant by transaction IDs.

{% tabs %}
{% tab title="Request body" %}
***

TxIDs array\<int>

A list of transactions to settle by ID.

***
{% endtab %}

{% tab title="Response body" %}
***
{% endtab %}
{% endtabs %}



