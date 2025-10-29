---
description: Retrieve a transaction receipt
---

# Transaction Receipt

<mark style="color:orange;">post:</mark> https://easypay5.com/APIcardProcREST/v1.0.0/Query/TransactionReceipt

{% tabs %}
{% tab title="Sample Request" %}
```clike
{
  "TxID": 2,
  "ReceiptType": 2
}
```
{% endtab %}

{% tab title="Sample Response" %}
```clike
{
  "TransactionReceiptQryResult": {
    "ErrCode": 0,
    "ErrMsg": "",
    "FunctionOk": true,
    "ReceiptHtml": "html",
    "RespMsg": "Successfully Returned Transaction Receipt Markup"
  }
}
```
{% endtab %}

{% tab title="Header Parameters" %}
**SessKey** string <mark style="color:orange;">required</mark>

A unique session key used for authentication in API calls. This key is generated upon successful authentication and must be included in all subsequent requests.

Example: `A1842D663E9A4A72XXXXXXXX303541303234373138`

***

**Content-Type** string <mark style="color:orange;">required</mark>

Example: `application/json`

***

**Accept** string <mark style="color:orange;">required</mark>

Example: `application/json`
{% endtab %}

{% tab title="Body" %}
**TxID** integer <mark style="color:purple;">optional</mark>

The unique identifier for the transaction

Example: `2`

***

**ReceiptType** integer · enum <mark style="color:purple;">optional</mark>

The type of receipt

* 1: Transaction
* 2: Void
* 3: Refund
* 4: Annual Consent
* 5: Recurring Consent
* 6: Subscription
* 7: ACH Transaction
* 8: ACH Void
* 9: ACH Refund

Example: 2

Possible values: 1,2,3,4,5,6,7,8,9
{% endtab %}
{% endtabs %}
