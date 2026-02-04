# Process Consent

<mark style="color:orange;">post:</mark> https://easypay5.com/APIcardProcREST/v1.0.0/Intl/ProcPayment

_This API call is for merchant accounts that are specifically configured for international processing._

{% tabs %}
{% tab title="Sample Request" %}
```clike
{
  "TokenID": "a64d8a2a-5994-11ef-95fc-3e580ecac30f",
  "ChargeAmt": 5.0
}
```
{% endtab %}

{% tab title="Sample Response" %}
```clike
{
  "Intl_ProcPaymentResult": {
    "AuthorizedAmt": 5.00,
    "ErrCode": 0,
    "ErrMsg": "",
    "FunctionOk": true,
    "RespMsg": "Successfully charged Consent a64d8a2a-5994-11ef-95fc-3e580ecac30f For $5.00",
    "TransID": "a63f6936-5994-11ef-8613-3e580ecac30f",
    "TxApproved": true,
    "TxnCode": ""
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

