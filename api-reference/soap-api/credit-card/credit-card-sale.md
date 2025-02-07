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
{% include "../../../.gitbook/includes/param-sess-key.md" %}

***

`Purchase` [api\_Purchase](../soap-object-dictionary.md#api_purchase) (object)

Fields: PurchType, Track, EmvTags, CardInfo, EMVRecTags, IsAuthOnly

***

{% include "../../../.gitbook/includes/param-account-holder.md" %}

***

{% include "../../../.gitbook/includes/param-end-customer.md" %}

***

{% include "../../../.gitbook/includes/param-amounts.md" %}

***

{% include "../../../.gitbook/includes/param-purchitems.md" %}

***

{% include "../../../.gitbook/includes/param-merchid.md" %}
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





## Credit Card Sale - Card Present

<mark style="color:green;">`POST`</mark> /ICardProcess/CreditCardSale\_CardPresent

Authorizes a card when the card is present at the place of the sale and can be swiped/inserted through a card reader.

{% tabs %}
{% tab title="Request body" %}
{% include "../../../.gitbook/includes/param-sess-key.md" %}

***

{% include "../../../.gitbook/includes/param-track.md" %}

***

{% include "../../../.gitbook/includes/param-account-holder.md" %}

***

{% include "../../../.gitbook/includes/param-end-customer.md" %}

***

{% include "../../../.gitbook/includes/param-amounts.md" %}

***

{% include "../../../.gitbook/includes/param-purchitems.md" %}

***

{% include "../../../.gitbook/includes/param-merchid.md" %}
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





## Credit Card Sale - Manual

<mark style="color:green;">`POST`</mark> /ICardProcess/CreditCardSale\_Manual

Processes a credit card cardsale when the credit card details are entered manually. Details include the card number, expiration date, CVV, card holder name and address.

{% tabs %}
{% tab title="Request body" %}
{% include "../../../.gitbook/includes/param-sess-key.md" %}

***

{% include "../../../.gitbook/includes/param-credit-card-info.md" %}

***

{% include "../../../.gitbook/includes/param-account-holder.md" %}

***

{% include "../../../.gitbook/includes/param-end-customer.md" %}

***

{% include "../../../.gitbook/includes/param-amounts.md" %}

***

{% include "../../../.gitbook/includes/param-purchitems.md" %}

***

{% include "../../../.gitbook/includes/param-merchid.md" %}
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





## Credit Card Sale - EMV

<mark style="color:green;">`POST`</mark> /ICardProcess/CreditCardSale\_EMV

Processes a credit card sale using a card reader device. The card information is read directly from the device without the need for manual entry.

{% tabs %}
{% tab title="Request body" %}
{% include "../../../.gitbook/includes/param-sess-key.md" %}

***

{% include "../../../.gitbook/includes/param-track.md" %}

***

`EmvTags` string

***

{% include "../../../.gitbook/includes/param-rectags.md" %}

***

{% include "../../../.gitbook/includes/param-account-holder.md" %}

***

{% include "../../../.gitbook/includes/param-end-customer.md" %}
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



