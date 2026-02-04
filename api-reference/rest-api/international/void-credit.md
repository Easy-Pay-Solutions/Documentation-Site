# Void Credit

<mark style="color:orange;">post:</mark> https://easypay5.com/APIcardProcREST/v1.0.0/Intl/VoidCredit

_This API call is for merchant accounts that are specifically configured for international processing._

{% tabs %}
{% tab title="Sample Request" %}
```clike
{
  "TransID": "a88ed0e4-5a3b-11ef-b49b-46647bd59a7a",
  "CreditAmt": 5.0
}
```
{% endtab %}

{% tab title="Sample Response" %}
```clike
{
  "Intl_VoidCredtResult": {
    "CreditAmt": 5.0,
    "ErrCode": 0,
    "ErrMsg": "",
    "FunctionOk": true,
    "RespMsg": "Succesfull VOID\/Credit",
    "TransID": "a88ed0e4-5a3b-11ef-b49b-46647bd59a7a",
    "TxApproved": true
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

