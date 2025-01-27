---
description: Methods related to credit card authorization
---

# Credit Card Auth (v1)

## &#x20;Credit Card Auth - Manual

<mark style="color:green;">`POST`</mark> /ICardProcess/CreditCardAuthOnly\_Manual

Authorizes a credit card transaction when the credit card details are entered manually. Details include the card number, expiration date, CVV, card holder name and address.

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

***

## Credit Card Auth - Card Present

<mark style="color:green;">`POST`</mark> /ICardProcess/CreditCardAuthOnly\_CardPresent

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

***

## Credit Card Voice Auth

<mark style="color:green;">`POST`</mark> /ICardProcess/CreditCardVoiceAuth

This method is used to receive approval for credit card transactions that require voice authorization before they are completed.

{% tabs %}
{% tab title="Request body" %}
{% include "../../../.gitbook/includes/param-sess-key.md" %}

***

{% include "../../../.gitbook/includes/param-approval-code.md" %}

***

{% include "../../../.gitbook/includes/param-txid.md" %}
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

***

## Credit Card Voice Auth - Full

<mark style="color:green;">`POST`</mark> /ICardProcess/CreditCardVoiceAuthSA

This method is used to receive approval for credit card transactions that require voice auth. Returns additional details such as the credit card data used in the transaction, settlement amounts, and transaction dates.

{% tabs %}
{% tab title="Request body" %}
{% include "../../../.gitbook/includes/param-sess-key.md" %}

***

{% include "../../../.gitbook/includes/param-approval-code.md" %}

***

{% include "../../../.gitbook/includes/param-txid.md" %}
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

`CardType` string

***

`SequenceNumber` string

***

`CardNumMask` string

***

{% include "../../../.gitbook/includes/param-avsr.md" %}

***

{% include "../../../.gitbook/includes/param-cvvr.md" %}

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
