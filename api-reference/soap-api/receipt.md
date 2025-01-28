---
description: Methods related to receipts
---

# Receipt

## Generate Receipt

<mark style="color:green;">`POST`</mark> /ICardProcess/ReceiptGenerate

Generate the html layout needed to create a customer, merchant, or dual receipt. Can be used for various receipt types such as: transaction, void, refund, annual and recurring consents.

{% tabs %}
{% tab title="Request body" %}
{% include "../../.gitbook/includes/param-sess-key.md" %}

***

`RefID` int

The transaction ID or consent ID

***

`ReceiptTypes` int

Values:\
\- 1 (Customer)\
\- 2 (Merchant)\
\- 3 (Both)

***

`Recipient` int

Values:\
\- 1 (Transaction)\
\- 2 (Void)\
\- 3 (Refund)\
\- 4 (Annual)\
\- 5 (Recurring)
{% endtab %}

{% tab title="Response body" %}
{% include "../../.gitbook/includes/param-ok-msg-errs.md" %}

***

`ReceiptHtml` string

The html of the receipt.
{% endtab %}
{% endtabs %}

***

## Query Receipt Details

<mark style="color:green;">`POST`</mark> /ICardProcess/ReceiptDetail\_Query

Return the details needed to generate a receipt for a credit card sale. For other receipt types, see the [#generate-receipt](receipt.md#generate-receipt "mention") method.

{% tabs %}
{% tab title="Request body" %}
{% include "../../.gitbook/includes/param-sess-key.md" %}

***

{% include "../../.gitbook/includes/param-txid.md" %}
{% endtab %}

{% tab title="Response body" %}
{% include "../../.gitbook/includes/param-ok-msg-errs.md" %}

***

`ReceiptInfo` api\_ReceiptDetail (object)

The details you'll need to create a credit card sale receipt.

Fields: MerchNumber, MerchDescrip, MerchAddress, MerchCity, MerchState, MerchZip, MerchPhone, MerchEmail, MerchTID, EntryType, TxDateTime, TxAmount, CardHolder, EndCustomer, TxID, TxnCode, TxType, TxStatus, RefID, CardType, CardNumber, AcctHolderID, EndCustID, AID, TVR, TSI, AC, ARC.
{% endtab %}
{% endtabs %}

