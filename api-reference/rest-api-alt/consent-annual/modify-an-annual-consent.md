# Modify an annual consent

<mark style="color:orange;">post:</mark> https://easypay5.com/APIcardProcREST/v1.0.0/ConsentAnnual/Modify

{% tabs %}
{% tab title="Sample Request" %}
```clike
{
  "ConsentID": 10,
  "ConsentMods": {
    "ExpMonth": 10,
    "ExpYear": 22,
    "Email": "robert@easypaysolutions.com",
    "Zip": "04106",
    "CustomerRefID": "A1235456",
    "ServiceDescrip": "REST API Testor",
    "RPGUID": "adf98580-b4ab-42fc-bb99-01c89964afe9",
    "NumDays": 365,
    "LimitPerCharge": 10000,
    "LimitLifeTime": 100000
  }
}
```
{% endtab %}

{% tab title="Sample Response" %}
```clike
{
  "ConsentAnnual_ModifyResult": {
    "ErrCode": 0,
    "ErrMsg": "",
    "FunctionOk": true,
    "ModifySuccess": true,
    "RespMsg": "Success : Modified Consent ID : 10"
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
ConsentID integer optional

ID of the consent to be modified

Example: `10`

***

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
> Full expiration year of the card or the last 2 digits
>
> Example: `22`
>
> ***
>
> **Email** string · email <mark style="color:purple;">optional</mark>
>
> Email address associated with the consent
>
> Example: `robert@easypaysolutions.com`
>
> ***
>
> **Zip** string <mark style="color:purple;">optional</mark>
>
> ZIP code associated with the consent
>
> Example: `04106`
>
> ***
>
> **CustomerRefID** string <mark style="color:purple;">optional</mark>
>
> Customer reference ID
>
> Example: `A1235456`
>
> ***
>
> **ServiceDescrip** string <mark style="color:purple;">optional</mark>
>
> Description of the service
>
> Example: `REST API Testor`
>
> ***
>
> **RPGUID** string <mark style="color:purple;">optional</mark>
>
> A custom, user-defined reference ID or value.
>
> Example: `adf98580-b4ab-42fc-bb99-01c89964afe9`
>
> ***
>
> **NumDays** integer <mark style="color:purple;">optional</mark>
>
> Number of days for the consent
>
> Example: `365`
>
> ***
>
> **LimitPerCharge** number · float <mark style="color:purple;">optional</mark>
>
> Limit per charge
>
> Example: `10000`
>
> ***
>
> **LimitLifeTime** number · float <mark style="color:purple;">optional</mark>
>
> Lifetime limit
>
> Example: `100000`
{% endtab %}
{% endtabs %}
