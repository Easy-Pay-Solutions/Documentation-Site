---
description: Modify an existing subscription consent
---

# Consent Subscription

<mark style="color:orange;">post:</mark> https://easypay5.com/APIcardProcREST/v1.0.0/ConsentSubscription/Modify

{% tabs %}
{% tab title="Sample Request" %}
```clike
{
  "ConsentID": 12,
  "ConsentMods": {
    "ExpMonth": 10,
    "ExpYear": 2022,
    "Email": "noreply@easypaysolutions.com",
    "Zip": "04106",
    "RPGUID": "",
    "CustomerRefID": "A123456",
    "ServiceDescrip": "Test",
    "PaymentAmt": 10,
    "PaymentAdjustDate": "2019-04-29T11:26:11.093Z",
    "OnHold": false
  }
}
```
{% endtab %}

{% tab title="Sample Response" %}
```clike
{
  "ErrCode": 0,
  "ErrMsg": "",
  "FunctionOk": true,
  "RespMsg": "Consent successfully modified"
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

ID of the consent to be modified

Example: `12`

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
> Expiration year of the card
>
> Example: `2022`
>
> ***
>
> **Email** string · email <mark style="color:purple;">optional</mark>
>
> Email associated with the consent
>
> Example: `noreply@easypaysolutions.com`
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
> **RPGUID** string <mark style="color:purple;">optional</mark>
>
> A custom, user-defined reference ID or value.
>
> Example: `adf98580-b4ab-42fc-bb99-01c89964afe9`
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
> **PaymentAmt** number · float <mark style="color:purple;">optional</mark>
>
> Payment $ amount
>
> Example: `10`
>
> ***
>
> **PaymentAdjustDate** string · date-time <mark style="color:purple;">optional</mark>
>
> Date and time for payment adjustment
>
> Example: `2019-04-29T11:26:11.093Z`
>
> ***
>
> **OnHold** boolean <mark style="color:purple;">optional</mark>
>
> Whether the consent is on hold
>
> Example: `false`
{% endtab %}

{% tab title="Notes" %}
In most cases you may only want to modify a single parameter such as PaymentAdjustDate or OnHold. You can supply a value of -1 or "-1" to any value which you do not want us to alter. The following example shows how to simply remove the hold from ConsentID 21:

```clike
{
"ConsentID": 21,
"ConsentMods": {
    "ExpMonth": -1,
    "ExpYear": -1,
    "Email": "-1",
    "Zip": "-1",
    "RPGUID": "-1",
    "CustomerRefID": "-1",
    "ServiceDescrip": "-1",
    "PaymentAmt": -1,
    "PaymentAdjustDate": "-1",
    "OnHold": false
   }
}
```
{% endtab %}
{% endtabs %}
