---
description: Initialize PayForm
---

# PayForm

<mark style="color:orange;">post:</mark> https://easypay5.com/APIcardProcREST/v1.0.0/CardSale/InitForm

Call this method to initialize a payment form used for collecting payments, saving card-on-file data, or both. The call returns the URL used to open the form.

For details on configurations and options, view our builder tool at [https://easypay8.com/byopayform/](https://easypay8.com/byopayform/)

{% tabs %}
{% tab title="Header Paramaters" %}
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
**InitParams** object <mark style="color:purple;">optional</mark>

> **MerchID** integer <mark style="color:purple;">optional</mark>
>
> Use 1 unless your account has multiple merchant records. The merchant ID for the transaction.
>
> Example: `1`
>
> ***
>
> **WTYPE** string · enum <mark style="color:orange;">required</mark>
>
> The widget type for the PayForm
>
> * PF: Regular PayForm
> * PA: International PayForm
>
> Example: `PF`
>
> Possible values: `PF  PA`
>
> ***
>
> **PostURL** string <mark style="color:purple;">optional</mark>
>
> The URL where real-time values will be posted after payment completion.
>
> Example: `https://easypay7.com/swidget/JsonGet.aspx`
>
> ***
>
> **RedirectURL** string <mark style="color:purple;">optional</mark>
>
> The URL to redirect to after processing the payment.
>
> Example: `https://easypay8.com/CYWidget/`
>
> ***
>
> **REF\_ID** string <mark style="color:purple;">optional</mark>
>
> A custom, user-defined reference ID or value.
>
> Example: `A97689#`
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
> **EndPoint** string <mark style="color:purple;">optional</mark>
>
> Points to a specific web app on our servers. Should always have the value of PayForm/PF.aspx.
>
> Example: `PayForm/PF.aspx`
>
> ***
>
> **EINDEX** string <mark style="color:purple;">optional</mark>
>
> Integrator key index for encryption assigned when integrator account is first created, received with the initial login credentials
>
> Example: `100`

**Amounts** object <mark style="color:purple;">optional</mark>

> **BaseAmt** number · float <mark style="color:purple;">optional</mark>
>
> The base $ amount for the transaction before any additional charges.
>
> Example: `52`
>
> ***
>
> **Surcharge** number · float <mark style="color:purple;">optional</mark>
>
> The surcharge $ amount added to the base amount, if applicable. Adjusted based on the total.
>
> Example: `1.04`
>
> ***
>
> **TotalAmt** number · float <mark style="color:purple;">optional</mark>
>
> The total $ amount to be charged, which includes the base amount and any surcharges.
>
> Example: `53.04`

**Payer** object <mark style="color:purple;">optional</mark>

> **Firstname** string <mark style="color:purple;">optional</mark>
>
> The first name of the payer.
>
> Example: `John`
>
> ***
>
> **Lastname** string <mark style="color:purple;">optional</mark>
>
> The last name of the payer.
>
> Example: `Doe`
>
> ***
>
> **Email** string <mark style="color:purple;">optional</mark>
>
> The email of the payer.
>
> ***
>
> **Phone** string <mark style="color:purple;">optional</mark>
>
> The phone of the payer.
>
> ***
>
> **BillingAddress** object <mark style="color:purple;">optional</mark>

**WidOptions** object <mark style="color:purple;">optional</mark>

> **eVisible** string <mark style="color:purple;">optional</mark>
>
> Hex digits controlling field visibility.
>
> Example: `0665`
>
> ***
>
> **eReadOnly** string <mark style="color:purple;">optional</mark>
>
> Hex digits dictating read-only fields.
>
> Example: `0040`
>
> ***
>
> **eStyles** string <mark style="color:purple;">optional</mark>
>
> Hex digits controlling form styling.
>
> Example: `0001`
>
> ***
>
> **eSubmission** string <mark style="color:purple;">optional</mark>
>
> Hex digits controlling submission options.
>
> Example: `0A01`
>
> ***
>
> **eColors** string <mark style="color:purple;">optional</mark>
>
> String controlling optional color schemes.
>
> Example: `#ffffff,#428bca,#007bff,#212121,#ffffff,#212121,#ffffff`
{% endtab %}

{% tab title="Sample Request" %}
```clike
{
  "InitParams": {
    "MerchID": 1,
    "WTYPE": "PF",
    "PostURL": "https://easypay7.com/swidget/JsonGet.aspx",
    "RedirectURL": "https://easypay8.com/CYWidget/",
    "REF_ID": "A97689#",
    "RPGUID": "92e1e15c-f64a-466b-8733-9b518b9f374c",
    "EndPoint": "PayForm/PF.aspx",
    "EINDEX": "300",
    "Amounts": {
      "Amount": 20,
      "Surcharge": 0,
      "TotalAmt": 20
    },
    "Payer": {
      "Firstname": "John Doe",
      "Lastname": "",
      "BillingAddress": {
        "StreetAddress": "",
        "City": "",
        "State": "",
        "ZIP": "04048",
        "Country": ""
      },
      "Email": "",
      "Phone": ""
    },
    "WidOptions": {
      "eVisible": "0665",
      "eReadOnly": "0040",
      "eStyles": "0001",
      "eSubmission": "0A01",
      "eColors": "#ffffff,#428bca,#007bff,#212121,#ffffff,#212121,#ffffff"
    }
  }
}
```
{% endtab %}

{% tab title="Sample Response" %}
```clike
{
  "PaymentInitResult": {
    "ErrCode": 0,
    "ErrMsg": "",
    "FunctionOk": true,
    "PaymentUrl": "https://easypay5.com/swidget/?eGUID=239F97C4&CS=021&Digest=tru49A2ncbyvHoaIa6T81Q",
    "RespMsg": "successfully returned payment Url"
  }
}
```
{% endtab %}
{% endtabs %}

