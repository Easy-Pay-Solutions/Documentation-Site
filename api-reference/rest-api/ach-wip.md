---
description: Create an ACH Sale
hidden: true
---

# ACH wip

<mark style="color:orange;">post:</mark> https://easypay5.com/APIcardProcREST/v1.0.0/ACH/Sale

**For member variable "AccountType" use the following values:**

1. Personal Checking = 1
2. Personal Saving = 2
3. Business Checking = 3
4. Business Saving = 4

{% tabs %}
{% tab title="Sample Request" %}
```clike
{
  "ChargeDetails": {
    "AccountNumber": "878460000256",
    "RoutingNumber": "211274515",
    "Amount": 10.25,
    "AccountType": 1
  },
  "AcctHolder": {
    "Firstname": "Sally",
    "Lastname": "Smith",
    "Company": "",
    "Title": "",
    "Url": "",
    "BillIngAdress": {
      "Address1": "123 Test Road",
      "Address2": "",
      "City": "Portland",
      "State": "ME",
      "ZIP": "04005",
      "Country": "USA"
    },
    "Email": "testing@easypaysolutions.com",
    "Phone": "8775558472"
  },
  "EndCustomer": {
    "Firstname": "Sally",
    "Lastname": "Smith",
    "Company": "",
    "Title": "",
    "Url": "",
    "BillIngAdress": {
      "Address1": "123 Test Road",
      "Address2": "",
      "City": "Portland",
      "State": "ME",
      "ZIP": "04005",
      "Country": "USA"
    },
    "Email": "testing@easypaysolutions.com",
    "Phone": "8775558472"
  },
  "PurchItems": {
    "ServiceDescrip": "FROM API TESTER",
    "ClientRefID": "12456AA",
    "RPGUID": "3d3424a6-c5f3-4c28"
  },
  "MerchID": 1
}
```
{% endtab %}

{% tab title="Sample Response" %}
```clike
{
  "ACHTransactionResult": {
    "AuthID": "69017501",
    "ErrCode": 0,
    "ErrMsg": "",
    "FunctionOk": true,
    "RespMsg": "TxID 1381 Approved",
    "TxApproved": true,
    "TxID": 1381,
    "uniqueTranID": "16790131F349BCBA"
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
**ChargeDetails** object <mark style="color:purple;">optional</mark>

> **AccountNumber** string <mark style="color:purple;">optional</mark>
>
> The account number associated with the bank account from which funds will be withdrawn.
>
> Example: `878460000256`
>
> ***
>
> **RoutingNumber** string <mark style="color:purple;">optional</mark>
>
> The routing number of the bank, used to identify the financial institution for the transaction.
>
> Example: `211274515`
>
> ***
>
> **Amount** number · float <mark style="color:purple;">optional</mark>
>
> The $ amount to be charged, specified in decimal format.
>
> Example: `10.25`
>
> ***
>
> **AccountType** integer · enum <mark style="color:purple;">optional</mark>
>
> The type of bank account. Possible values are:
>
> * 1: Personal Checking.
> * 2: Personal Saving.
> * 3: Business Checking.
> * 4: Business Saving.

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
> **BillIngAdress** object <mark style="color:purple;">optional</mark>
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
> **BillIngAdress** object <mark style="color:purple;">optional</mark>
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

**PurchItems** object <mark style="color:purple;">optional</mark>

> **ServiceDescrip** string <mark style="color:purple;">optional</mark>
>
> A description of the service or item.
>
> Example: `FROM API TESTER`
>
> ***
>
> **ClientRefID** string <mark style="color:purple;">optional</mark>
>
> A reference ID provided by the client for tracking purposes.
>
> Example: `12456AA`
>
> ***
>
> **RPGUID** string <mark style="color:purple;">optional</mark>
>
> A custom, user-defined reference ID or value.
>
> Example: `adf98580-b4ab-42fc-bb99-01c89964afe9`

**MerchID** integer <mark style="color:purple;">optional</mark>

Example: `1`
{% endtab %}
{% endtabs %}
