# Modify a recurring consent

<mark style="color:orange;">post:</mark> https://easypay5.com/APIcardProcREST/v1.0.0/ConsentRecurring/Modify

{% tabs %}
{% tab title="Sample Request" %}
```clike
{
  "ConsentID": 42,
  "ConsentMods": {
    "ExpMonth": 10,
    "ExpYear": 2028,
    "Email": "sean@easypaysolutions.com",
    "Zip": "04101",
    "CustomerRefID": "A123456",
    "ServiceDescrip": "Test",
    "RPGUID": ""
  }
}
```
{% endtab %}

{% tab title="Sample Response" %}
```clike
{
  "ConsentRecurring_ModifyResult": {
    "ErrCode": 0,
    "ErrMsg": "",
    "FunctionOk": true,
    "ModifySuccess": true,
    "RespMsg": "Success : Modified Consent ID : 42"
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

ID of the consent to be cancelled

Example: `42`

**ConsentMods** object <mark style="color:purple;">optional</mark>

> **ExpMonth** integer <mark style="color:purple;">optional</mark>
>
> Expiration month of the card
>
> Example: `10`
>
> ***
>
> **ExpYear** integer <mark style="color:purple;">optional</mark>
>
> Expiration year of the card
>
> Example: `2028`
>
> ***
>
> **Email** string · email <mark style="color:purple;">optional</mark>
>
> Email associated with the consent
>
> Example: `sean@easypaysolutions.com`
>
> ***
>
> **Zip** string <mark style="color:purple;">optional</mark>
>
> ZIP code associated with the consent
>
> Example: `04101`
>
> ***
>
> **CustomerRefID** string <mark style="color:purple;">optional</mark>
>
> Customer reference ID
>
> Example: `A123456`
>
> ***
>
> **ServiceDescrip** string <mark style="color:purple;">optional</mark>
>
> Description of the service
>
> Example: `Test`
>
> ***
>
> **RPGUID** string <mark style="color:purple;">optional</mark>
>
> A custom, user-defined reference ID or value.
>
> Example: `adf98580-b4ab-42fc-bb99-01c89964afe9`
{% endtab %}
{% endtabs %}
