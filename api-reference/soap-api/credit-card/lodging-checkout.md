---
description: Methods related to lodging checkout
---

# Lodging Checkout

## Lodging Checkout Full - By TxID

<mark style="color:green;">`POST`</mark> /ICardProcess/LodgingCheckoutFullByTxID

Process a lodging checkout. Additional details such as the checkout date and additional charges accrued by the customer can be included.

{% tabs %}
{% tab title="Request body" %}
{% include "../../../.gitbook/includes/param-sess-key.md" %}

***

{% include "../../../.gitbook/includes/param-txid.md" %}

***

{% include "../../../.gitbook/includes/param-extra-charge-code.md" %}

***

`DepartureDate` datetime

Departure date of the checkout.

***

`FinalAmount` decimal

The final $ amount of stay. Cannot be higher than 15% of authorization of checkin.
{% endtab %}

{% tab title="Response body" %}
{% include "../../../.gitbook/includes/param-ok-msg-errs.md" %}

***

{% include "../../../.gitbook/includes/param-tx-approved.md" %}

***

{% include "../../../.gitbook/includes/param-txid.md" %}
{% endtab %}
{% endtabs %}





## Lodging Checkout - By TxID

<mark style="color:green;">`POST`</mark> /ICardProcess/LodgingCheckoutByTxID

Process a lodging checkout by transaction ID.

{% tabs %}
{% tab title="Request body" %}
{% include "../../../.gitbook/includes/param-sess-key.md" %}

***

{% include "../../../.gitbook/includes/param-txid.md" %}

***

`FinalAmount` decimal

The final $ amount of stay. Cannot be higher than 15% of authorization of checkin.
{% endtab %}

{% tab title="Response body" %}
{% include "../../../.gitbook/includes/param-ok-msg-errs.md" %}

***

{% include "../../../.gitbook/includes/param-tx-approved.md" %}

***

{% include "../../../.gitbook/includes/param-txid.md" %}
{% endtab %}
{% endtabs %}





## Lodging Checkout - By StayID

<mark style="color:green;">`POST`</mark> /ICardProcess/LodgingCheckoutByStayID

Process a lodging checkout by StayID.

{% tabs %}
{% tab title="Request body" %}
{% include "../../../.gitbook/includes/param-sess-key.md" %}

***

`StayID` int

The ID number that is returned after a checkin.

***

`FinalAmount` decimal

The final $ amount of stay. Cannot be higher than 15% of authorization of checkin.
{% endtab %}

{% tab title="Response body" %}
{% include "../../../.gitbook/includes/param-ok-msg-errs.md" %}

***

{% include "../../../.gitbook/includes/param-tx-approved.md" %}

***

{% include "../../../.gitbook/includes/param-txid.md" %}
{% endtab %}
{% endtabs %}



