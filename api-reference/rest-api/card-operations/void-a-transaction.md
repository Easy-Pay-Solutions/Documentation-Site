---
description: Void a Transaction
---

# Void a Transaction

<mark style="color:orange;">post:</mark> https://easypay5.com/APIcardProcREST/v1.0.0/CardSale/CardPresent

{% tabs %}
{% tab title="Sample Request" %}
```clike
{
  "TxID": 53
}
```
{% endtab %}

{% tab title="Sample Response" %}
```clike
{
  "Transaction_VoidResult": {
    "ErrCode": 0,
    "ErrMsg": "",
    "FunctionOk": true,
    "RespMsg": "Successful Transaction Void TxID : 53 [097706]",
    "TxApproved": true,
    "TxID": 53
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
{% endtabs %}

