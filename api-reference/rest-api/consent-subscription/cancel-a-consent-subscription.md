---
description: Cancel an existing subscription consent
---

# Cancel a consent subscription

<mark style="color:orange;">post:</mark> https://easypay5.com/APIcardProcREST/v1.0.0/ConsentSubscription/Cancel

{% tabs %}
{% tab title="Sample Request" %}
```clike
{
    "ConsentID": 4162
}
```
{% endtab %}

{% tab title="Sample Response" %}
```clike
{
    "ConsentSubscription_CancelResult": {
        "CancelSuccess": true,
        "CancelledConsentID": 4162,
        "ErrCode": 0,
        "ErrMsg": "",
        "FunctionOk": true,
        "RespMsg": "Successfully DISABLED ConsentID 4162 : Card Number Removed"
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

Example: `12`


{% endtab %}
{% endtabs %}
