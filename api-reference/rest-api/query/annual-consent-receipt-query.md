# Annual Consent Receipt Query

<mark style="color:orange;">post:</mark> <mark style="color:$info;">https://easypay5.com/APIcardProcREST/v1.0.0/Query/ConsentAnnualReceipt</mark>

{% tabs %}
{% tab title="Sample Request" %}
```clike
{
  "ConsentID": 2,
  "ReceiptType": 2
}
```
{% endtab %}

{% tab title="Sample Response" %}
```clike
{
  "ConsentAnnualReceiptQryResult": {
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
{% endtabs %}

