# Create an annual consent with manual card entry

<mark style="color:orange;">post:</mark> https://easypay5.com/APIcardProcREST/v1.0.0/ConsentAnnual/Create\_MAN

_<mark style="color:red;">**For PCI compliant merchants only (AOC on file with Number required)**</mark>_

{% tabs %}
{% tab title="Sample Request" %}
```clike
{
  "ccCardInfo": {
    "AccountNumber": "4111111111111111",
    "ExpMonth": 10,
    "ExpYear": 2022,
    "CSV": "122"
  },
  "ConsentCreator": {
    "MerchID": 1,
    "CustomerRefID": "A1523644",
    "ServiceDescrip": "REST Test",
    "RPGUID": "4c269391-a698-4e10-a1a8-0353ee80d1a6",
    "StartDate": "/Date(1563800567934-0400)/",
    "NumDays": 365,
    "LimitPerCharge": 1000,
    "LimitLifeTime": 100000
  },
  "AcctHolder": {
    "Firstname": "Sean",
    "Lastname": "Wood",
    "Company": "",
    "Title": "",
    "Url": "",
    "BillIngAdress": {
      "Address1": "123 Fake St",
      "Address2": "",
      "City": "PORTLAND",
      "State": "ME",
      "ZIP": "04106",
      "Country": "USA"
    },
    "Email": "robert@easypaysolutions.com",
    "Phone": "8777248472"
  },
  "EndCustomer": {
    "Firstname": "Sean",
    "Lastname": "Wood",
    "Company": "",
    "Title": "",
    "Url": "",
    "BillIngAdress": {
      "Address1": "123 Fake St.",
      "Address2": "",
      "City": "PORTLAND",
      "State": "ME",
      "ZIP": "04106",
      "Country": "USA"
    },
    "Email": "robert@easypaysolutions.com",
    "Phone": "8777248472"
  }
}
```
{% endtab %}

{% tab title="Sample Response" %}
```clike
{
  "ConsentAnnual_Create_MANResult": {
    "ConsentID": 18,
    "CreationSuccess": true,
    "ErrCode": 0,
    "ErrMsg": "",
    "FunctionOk": true,
    "PreConsentAuthMessage": "APPROVED 297311                 ",
    "PreConsentAuthSuccess": true,
    "PreConsentAuthTxID": 61,
    "RespMsg": "Success : Created Consent ID : 000018"
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
**ccCardInfo** object <mark style="color:purple;">optional</mark>

> **AccountNumber** string <mark style="color:purple;">optional</mark>
>
> Example: `4111111111111111`
>
>
>
> **ExpMonth** integer <mark style="color:purple;">optional</mark>
>
> Example: `10`
>
>
>
> **ExpYear** integer <mark style="color:purple;">optional</mark>
>
> Example: `2028`
>
>
>
> **CSV** string <mark style="color:purple;">optional</mark>
>
> Example: `122`

**ConsentCreator** object <mark style="color:purple;">optional</mark>

> **MerchID** integer <mark style="color:purple;">optional</mark>
>
> Example: `1`
>
>
>
> **CustomerRefID** string <mark style="color:purple;">optional</mark>
>
> Example: `A1523644`
>
>
>
> **ServiceDescrip** string <mark style="color:purple;">optional</mark>
>
> Example: `REST Test`
>
>
>
> **RPGUID** string <mark style="color:purple;">optional</mark>
>
> A custom, user-defined reference ID or value.
>
> Example: `adf98580-b4ab-42fc-bb99-01c89964afe9`
>
>
>
> **StartDate** string <mark style="color:purple;">optional</mark>
>
> Date and time in Microsoft JSON date format (Unix timestamp and timezone offset).
>
> Example: `2024-12-01T11:19:01.000Z`
>
>
>
> **NumDays** integer <mark style="color:purple;">optional</mark>
>
> Example: `365`
>
>
>
> **LimitPerCharge** number · float <mark style="color:purple;">optional</mark>
>
> Example: `1000`
>
>
>
> **LimitLifeTime** number · float <mark style="color:purple;">optional</mark>
>
> Example: `100000`

**AcctHolder** object optional

> **Firstname** string <mark style="color:purple;">optional</mark>
>
> Example: `Sally`
>
>
>
> **Lastname** string <mark style="color:purple;">optional</mark>
>
> Example: `APIACH`
>
>
>
> **Company** string <mark style="color:purple;">optional</mark>
>
>
>
> **Title** string <mark style="color:purple;">optional</mark>
>
>
>
> **Url** string <mark style="color:purple;">optional</mark>
>
>
>
> **BillIngAddress** object <mark style="color:purple;">optional</mark>
>
>
>
> **Email** string <mark style="color:purple;">optional</mark>
>
> Example: `testing@easypaysolutions.com`
>
>
>
> **Phone** string <mark style="color:purple;">optional</mark>
>
> Example: `8775558472`

**EndCustomer** object <mark style="color:purple;">optional</mark>

> **Firstname** string <mark style="color:purple;">optional</mark>
>
> Example: `Sally`
>
>
>
> **Lastname** string <mark style="color:purple;">optional</mark>
>
> Example: `APIACH`
>
>
>
> **Company** string <mark style="color:purple;">optional</mark>
>
>
>
> **Title** string <mark style="color:purple;">optional</mark>
>
>
>
> **Url** string <mark style="color:purple;">optional</mark>
>
>
>
> **BillIngAddress** object <mark style="color:purple;">optional</mark>
>
>
>
> **Email** string <mark style="color:purple;">optional</mark>
>
> Example: `testing@easypaysolutions.com`
>
>
>
> **Phone** string <mark style="color:purple;">optional</mark>
>
> Example: `8775558472`
{% endtab %}
{% endtabs %}
