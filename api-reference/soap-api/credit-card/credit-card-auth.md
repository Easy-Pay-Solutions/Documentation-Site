---
description: Methods related to credit card authorization
---

# Credit Card Auth

## &#x20;Credit Card Auth - Manual

<mark style="color:green;">`POST`</mark> /ICardProcess/CreditCardAuthOnly\_Manual

Authorizes a credit card transaction when the credit card details are entered manually. Details include the card number, expiration date, CVV, card holder name and address.

{% tabs %}
{% tab title="Request body" %}
***

***

***

***

***

***
{% endtab %}

{% tab title="Response body" %}
***

***

***

***

***

***
{% endtab %}
{% endtabs %}





## Credit Card Auth - Card Present

<mark style="color:green;">`POST`</mark> /ICardProcess/CreditCardAuthOnly\_CardPresent

Authorizes a card when the card is present at the place of the sale and can be swiped/inserted through a card reader.

{% tabs %}
{% tab title="Request body" %}
***

***

***

***

***

***
{% endtab %}

{% tab title="Response body" %}
***

***

***

***

***

***
{% endtab %}
{% endtabs %}





## Credit Card Voice Auth

<mark style="color:green;">`POST`</mark> /ICardProcess/CreditCardVoiceAuth

This method is used to receive approval for credit card transactions that require voice authorization before they are completed.

{% tabs %}
{% tab title="Request body" %}
***

***
{% endtab %}

{% tab title="Response body" %}
***

***

***

***

***

***
{% endtab %}
{% endtabs %}





## Credit Card Voice Auth - Full

<mark style="color:green;">`POST`</mark> /ICardProcess/CreditCardVoiceAuthSA

This method is used to receive approval for credit card transactions that require voice auth. Returns additional details such as the credit card data used in the transaction, settlement amounts, and transaction dates.

{% tabs %}
{% tab title="Request body" %}
***

***
{% endtab %}

{% tab title="Response body" %}
***

***

***

***

`CardType` string

The type of card used.

Example: VI

***

`SequenceNumber` string

***

`CardNumMask` string

***

***

***

`DetailAgg` string

***

`IsPartialApproved` boolean

***

`POSRetrieval` string

***

`AuthorizedAmount` decimal

***

`RequiresVoiceAuth` boolean

***

`TransactionDate` string

***

`TransactionTime` string

***

`ArrivalDate` string

***

`DepartureDate` string

***

`Duration` string

***

`CardExpMonth` string

***

`CardExpYear` string

***

`ChargeDescriptor` string

***

`SaleCode` string

***

`SettledAmount` decimal
{% endtab %}
{% endtabs %}



