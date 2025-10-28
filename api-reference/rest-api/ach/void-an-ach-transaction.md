# Void an ACH transaction

<mark style="color:orange;">post:</mark> https://easypay5.com/APIcardProcREST/v1.0.0/ACH/Void

{% tabs %}
{% tab title="Sample Request" %}
```clike
{
  "TxID": 35
}
```
{% endtab %}

{% tab title="Sample Response" %}
```clike
{
  "ACHTransaction_VoidResult": {
    "AuthID": "67210748",
    "ErrCode": 0,
    "ErrMsg": "",
    "FunctionOK": true,
    "RespMsg": "VOID APPROVED 67210748 TXID 35",
    "TxApproved": true,
    "TxID": 35
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

Example: `35`
{% endtab %}
{% endtabs %}
