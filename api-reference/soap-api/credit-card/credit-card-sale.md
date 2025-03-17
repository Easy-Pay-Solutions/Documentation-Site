---
description: Methods related to credit card sale
layout:
  title:
    visible: true
  description:
    visible: true
  tableOfContents:
    visible: true
  outline:
    visible: true
  pagination:
    visible: true
---

# Credit Card Sale

## Credit Card Sale - Composite

<mark style="color:green;">`POST`</mark> /ICardProcess/CreditCardSale\_Composite

This is for internal use only.

{% tabs %}
{% tab title="Request body" %}
***

`Purchase` [api\_Purchase](../soap-object-dictionary.md#api_purchase) (object)

Fields: PurchType, Track, EmvTags, CardInfo, EMVRecTags, IsAuthOnly

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





## Credit Card Sale - Card Present

<mark style="color:green;">`POST`</mark> /ICardProcess/CreditCardSale\_CardPresent

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





## Credit Card Sale - Manual

<mark style="color:green;">`POST`</mark> /ICardProcess/CreditCardSale\_Manual

Processes a credit card cardsale when the credit card details are entered manually. Details include the card number, expiration date, CVV, card holder name and address.

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





## Credit Card Sale - EMV

<mark style="color:green;">`POST`</mark> /ICardProcess/CreditCardSale\_EMV

Processes a credit card sale using a card reader device. The card information is read directly from the device without the need for manual entry.

{% tabs %}
{% tab title="Request body" %}
***

***

`EmvTags` string

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



