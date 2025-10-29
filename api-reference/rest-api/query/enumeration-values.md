---
description: Methods related querying general information such as enum values
---

# Enumeration values

<mark style="color:orange;">post:</mark> https://easypay5.com/APIcardProcREST/v1.0.0/Query/Enum

{% tabs %}
{% tab title="Sample Request" %}
```clike
{
  "Query": "TXStatus"
}
```
{% endtab %}

{% tab title="Sample Response" %}
```clike
{
  "Enum_QueryResult": {
    "EnumItems": [
      {
        "EnumText": "ALL",
        "EnumValue": -1
      }
    ],
    "ErrCode": 0,
    "ErrMsg": "",
    "FunctionOk": true,
    "RespMsg": "Successfully Returned Enum Records : 6"
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
**Query** string · enum <mark style="color:purple;">optional</mark>

The enumeration type to query.

Example: `TXStatus`

Possible values: `ACHStatus`

`ACHType`

`AConsentType`

`BatchSettleMode`

`BatchSettleStatus`

`ConsentType`

`IntAction`

`IntlAction`

`IntlResult`

`IntlStatus`

`Period`

`ReceiptType`

`Recipient`

`RecurSchedStatus`

`TxStatus`

`TxType`
{% endtab %}
{% endtabs %}
