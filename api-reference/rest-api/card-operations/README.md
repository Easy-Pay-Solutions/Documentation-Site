---
description: Process a refund to a settled charge
---

# Card Operations

<mark style="color:orange;">post:</mark> https://easypay5.com/APIcardProcREST/v1.0.0/CardSale/ApplyCredit

Use this call to process a refund to a settled charge. You will need the Transaction ID and the amount to be refunded.

{% tabs %}
{% tab title="Sample Request" %}
```clike
{
  "TxID": 56,
  "CreditAmount": 5
}
```
{% endtab %}

{% tab title="Sample Response" %}
```clike
{
  "Transaction_ApplyCreditResult": {
    "ErrCode": 0,
    "ErrMsg": "",
    "FunctionOk": true,
    "RespMsg": "Successful Credit Pending Transaction ID : 000057",
    "TxApproved": true,
    "TxID": 57
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

Transaction ID of the charge to be refunded

Example: `56`

***

**CreditAmount** number · float <mark style="color:purple;">optional</mark>

Amount to be refunded

Example: `5`
{% endtab %}
{% endtabs %}
