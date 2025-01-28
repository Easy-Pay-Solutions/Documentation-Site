---
description: Methods related to transactions
---

# Transaction

## Apply Transaction Credit

<mark style="color:green;">`POST`</mark> /ICardProcess/Transaction\_ApplyCredit

Apply a full or partial credit against a settled credit card charge.&#x20;

{% include "../../.gitbook/includes/info-void-credit-transaction.md" %}

{% tabs %}
{% tab title="Request body" %}
{% include "../../.gitbook/includes/param-sess-key.md" %}

***

{% include "../../.gitbook/includes/param-txid.md" %}

***

`CreditAmount` decimal

The $ amount that you want to return to the card. \
This can be a partial amount of the full transaction.
{% endtab %}

{% tab title="Response body" %}
{% include "../../.gitbook/includes/param-ok-msg-errs.md" %}

***

{% include "../../.gitbook/includes/param-tx-approved.md" %}

***

{% include "../../.gitbook/includes/param-txid.md" %}
{% endtab %}
{% endtabs %}

***

## Void Transaction

<mark style="color:green;">`POST`</mark> /ICardProcess/Transaction\_Void

Voids a credit card sale transaction.&#x20;

{% include "../../.gitbook/includes/info-void-credit-transaction.md" %}

{% tabs %}
{% tab title="Request body" %}
{% include "../../.gitbook/includes/param-sess-key.md" %}

***

{% include "../../.gitbook/includes/param-txid.md" %}
{% endtab %}

{% tab title="Response body" %}
{% include "../../.gitbook/includes/param-ok-msg-errs.md" %}

***

{% include "../../.gitbook/includes/param-tx-approved.md" %}

***

{% include "../../.gitbook/includes/param-txid.md" %}
{% endtab %}
{% endtabs %}

***

## Query Transactions

<mark style="color:green;">`POST`</mark> /ICardProcess/Transaction\_Query

Query credit card transactions. Those can include authorizations, charges, credits, and voids.

{% tabs %}
{% tab title="Request body" %}
{% include "../../.gitbook/includes/param-sess-key.md" %}

***

{% include "../../.gitbook/includes/param-query.md" %}
{% endtab %}

{% tab title="Response body" %}
{% include "../../.gitbook/includes/param-ok-msg-errs.md" %}

***

{% include "../../.gitbook/includes/param-num-records.md" %}

***

`Transactions` List\<api\_Transaction> (array\<object>)

Fields: ID, SEQ\_NO, ACCT\_LAST\_NAME, ACCT\_FIRST\_NAME, ACCT\_NO, EXP\_DATE, AMOUNT, TXN\_DATE, TXN\_TIME, TXN\_DATETIME, TXN\_CODE, BatchNO, BatchStatus, BatchLogID, CARD\_TYPE, CardPresent, SALE\_TAX, SURCHARGE, CASHBACK, TxStatus, TxLOCK, REF\_ID, RPGUID, RefTxID, MerchID, SERVER, TIP, CreatedOn, LastChangedOn, LAST\_CHANGED\_BY, Origin, UserID, IsLocked, PAYMENT\_TYPE, TxType, ConsentID, PreAuthID, AcctHolderID, EndCustID, Credits, Flags, AVSr, CVVr, PrepaidBalance, PartialAuthApproved, HAuthorizedAmount, IsPartialApproval.
{% endtab %}
{% endtabs %}

***

## Query Transaction - Full

<mark style="color:green;">`POST`</mark> /ICardProcess/Transaction\_FullDetail

Return the details for the transaction, the card holder contact, and end customer information.

{% tabs %}
{% tab title="Request body" %}
{% include "../../.gitbook/includes/param-sess-key.md" %}

***

{% include "../../.gitbook/includes/param-txid.md" %}
{% endtab %}

{% tab title="Response body" %}
{% include "../../.gitbook/includes/param-ok-msg-errs.md" %}

***

Transaction api\_Transaction (object)

Fields: ID, SEQ\_NO, ACCT\_LAST\_NAME, ACCT\_FIRST\_NAME, ACCT\_NO, EXP\_DATE, AMOUNT, TXN\_DATE, TXN\_TIME, TXN\_DATETIME, TXN\_CODE, BatchNO, BatchStatus, BatchLogID, CARD\_TYPE, CardPresent, SALE\_TAX, SURCHARGE, CASHBACK, TxStatus, TxLOCK, REF\_ID, RPGUID, RefTxID, MerchID, SERVER, TIP, CreatedOn, LastChangedOn, LAST\_CHANGED\_BY, Origin, UserID, IsLocked, PAYMENT\_TYPE, TxType, ConsentID, PreAuthID, AcctHolderID, EndCustID, Credits, Flags, AVSr, CVVr, PrepaidBalance, PartialAuthApproved, HAuthorizedAmount, IsPartialApproval.

***

{% include "../../.gitbook/includes/param-account-holder-full.md" %}

***

{% include "../../.gitbook/includes/param-end-customer-full.md" %}
{% endtab %}
{% endtabs %}



