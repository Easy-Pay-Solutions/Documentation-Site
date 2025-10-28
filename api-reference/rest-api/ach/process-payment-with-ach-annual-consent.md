# Process payment with ACH annual consent

<mark style="color:orange;">post:</mark> https://easypay5.com/APIcardProcREST/v1.0.0/ACH/ProcPayment

{% tabs %}
{% tab title="Sample Request" %}
```clike
{
  "ConsentID": 21,
  "ProcessAmount": 5.1
}
```
{% endtab %}

{% tab title="Sample Response" %}
```clike
{
  "ACHConsentAnnual_ProcPaymentResult": {
    "ErrCode": 0,
    "ErrMsg": "",
    "FunctionOk": true,
    "RespMsg": "APPROVED 67210748 TXID 000035",
    "TxApproved": true,
    "TxID": 72,
    "uniqueTranID": "16790131F349BCBA"
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
**ConsentID** integer <mark style="color:purple;">optional</mark>

Example: `21`

***

**ProcessAmount** number · float <mark style="color:purple;">optional</mark>

Example: `5.1`
{% endtab %}
{% endtabs %}
