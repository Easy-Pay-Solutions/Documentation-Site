# Create a recurring consent with manual card entry

<mark style="color:orange;">post:</mark> https://easypay5.com/APIcardProcREST/v1.0.0/ConsentRecurring/Create

_<mark style="color:red;">**For PCI compliant merchants only (AOC on file with Number required)**</mark>_

{% tabs %}
{% tab title="Sample Request" %}
```clike
{
  "ccCardInfo": {
    "AccountNumber": "4111111111111111",
    "ExpMonth": 10,
    "ExpYear": 23,
    "CSV": "123",
    "Track": "%B4788250000028291^VISA TEST/GOOD^231010100733000000?;4895390000000013=151210100000733?"
  },
  "ConsentCreator": {
    "MerchID": 1,
    "CustomerRefID": "A123456",
    "ServiceDescrip": "",
    "RPGUID": "",
    "StartDate": "/Date(1564409121413-0400)/",
    "NumPayments": 10,
    "TotalAmount": 10000,
    "Period": 2
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
  "ConsentRecurring_CreateResult": {
    "ConsentID": 22,
    "CreationSuccess": true,
    "ErrCode": 0,
    "ErrMsg": "",
    "FunctionOk": true,
    "MySched": [
      {
        "Remaining": 9000,
        "SchedID": 41,
        "paymentAmt": 1000,
        "paymentDate": "2024-12-01T11:19:01.000Z",
        "paymentNo": 1
      }
    ],
    "PreConsentAuthMessage": "APPROVED 298734                 ",
    "PreConsentAuthSuccess": true,
    "PreConsentAuthTxID": 66,
    "RespMsg": "Success : Created Recurring Consent ID : 000022"
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
> ***
>
> **ExpMonth** integer <mark style="color:purple;">optional</mark>
>
> Example: `10`
>
> ***
>
> **ExpYear** integer <mark style="color:purple;">optional</mark>
>
> Example: `2028`
>
> ***
>
> **CSV** string <mark style="color:purple;">optional</mark>
>
> Example: `122`
>
> ***
>
> **Track string** | nullable <mark style="color:purple;">optional</mark>
>
> Example: `%B4788250000028291^VISA TEST/GOOD^231010100733000000?;4895390000000013=151210100000733?`

**ConsentCreator** object <mark style="color:purple;">optional</mark>

> **MerchID** integer <mark style="color:purple;">optional</mark>
>
> Example: `1`
>
> ***
>
> **CustomerRefID** string <mark style="color:purple;">optional</mark>
>
> Example: `A123456`
>
> ***
>
> **ServiceDescrip** string <mark style="color:purple;">optional</mark>
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
> **StartDate** string <mark style="color:purple;">optional</mark>
>
> Date and time in Microsoft JSON date format (Unix timestamp and timezone offset).
>
> Example: `2024-12-01T11:19:01.000Z`
>
> ***
>
> **NumPayments** integer <mark style="color:purple;">optional</mark>
>
> Example: `10`
>
> ***
>
> **TotalAmount** number · float <mark style="color:purple;">optional</mark>
>
> Example: `10000`
>
> ***
>
> **Period** integer <mark style="color:purple;">optional</mark>
>
> Example: `2`

**AcctHolder** object <mark style="color:purple;">optional</mark>

> **Firstname** string <mark style="color:purple;">optional</mark>
>
> Example: `Sally`
>
> ***
>
> **Lastname** string <mark style="color:purple;">optional</mark>
>
> Example: `APIACH`
>
> ***
>
> **Company** string <mark style="color:purple;">optional</mark>
>
> ***
>
> **Title** string <mark style="color:purple;">optional</mark>
>
> ***
>
> **Url** string <mark style="color:purple;">optional</mark>
>
> ***
>
> **BillIngAddress** object <mark style="color:purple;">optional</mark>
>
> ***
>
> **Email** string <mark style="color:purple;">optional</mark>
>
> Example: `testing@easypaysolutions.com`
>
> ***
>
> **Phone** string <mark style="color:purple;">optional</mark>
>
> Example: `8775558472`

**EndCustomer** object <mark style="color:purple;">optional</mark>

> **Firstname** string <mark style="color:purple;">optional</mark>
>
> Example: `Sally`
>
> ***
>
> **Lastname** string <mark style="color:purple;">optional</mark>
>
> Example: `APIACH`
>
> ***
>
> **Company** string <mark style="color:purple;">optional</mark>
>
> ***
>
> **Title** string <mark style="color:purple;">optional</mark>
>
> ***
>
> **Url** string <mark style="color:purple;">optional</mark>
>
> ***
>
> **BillIngAddress** object <mark style="color:purple;">optional</mark>
>
> ***
>
> **Email** string <mark style="color:purple;">optional</mark>
>
> Example: `testing@easypaysolutions.com`
>
> ***
>
> **Phone** string <mark style="color:purple;">optional</mark>
>
> Example: `8775558472`
{% endtab %}
{% endtabs %}
