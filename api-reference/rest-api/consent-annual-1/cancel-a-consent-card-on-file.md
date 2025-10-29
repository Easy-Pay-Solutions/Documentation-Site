# Cancel a consent (Card On File)

<mark style="color:orange;">post:</mark> https://easypay5.com/APIcardProcREST/v1.0.0/ConsentAnnual/Cancel

Use this call to Cancel a consent (Card On File). You will need the ConsentID in order to execute this method.

{% tabs %}
{% tab title="Sample Request" %}
```clike
{
  "ConsentID": 20
}
```
{% endtab %}

{% tab title="Sample Response" %}
```clike
{
  "ConsentAnnual_CancelResult": {
    "CancelSuccess": true,
    "CancelledConsentID": 20,
    "ErrCode": 0,
    "ErrMsg": "",
    "FunctionOk": true,
    "RespMsg": "Successfully DISBALED ConsentID 20 : Card Number Removed"
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

ID of the consent to be canceled

Example: `20`
{% endtab %}
{% endtabs %}
