---
description: Authenticate user and retrieve session key
---

# Authentication

<mark style="color:orange;">post:</mark> https://easypay5.com/APIcardProcREST/v1.0.0/Authenticate

{% tabs %}
{% tab title="Sample Request" %}
```clike
{
  "AcctCode": "EP911XXXX",
  "Token": "2148B239CF6846BDA5D141BF4A4CFBE8"
}
```
{% endtab %}

{% tab title="Sample Response" %}
```clike
{
  "AuthenticateResult": {
    "AuthSuccess": true,
    "ErrCode": 0,
    "ErrMsg": "",
    "FunctionOk": true,
    "MerchantList": [
      {
        "Address": "45 spring street portland Maine 04101",
        "Descrip": "Test Merchant 1",
        "ID": 1,
        "Location": "Test Merchant 1",
        "TermID": "006"
      }
    ],
    "RespMsg": "SessKey Expires|4/18/2019 7:29:47 AM",
    "SessKey": "B9F24903C3BA4770AE303032303541303032353437",
    "ThisUser": {
      "APILocationID": 2210,
      "AccountCode": "EP9116875",
      "AcctID": 205,
      "Alias": "vidya_Venkatraman",
      "CreatedBy": "ADMIN : vidya Venkatraman",
      "DateCreated": "2024-12-01T11:19:01.000Z",
      "DateModified": "2024-12-01T11:19:01.000Z",
      "Description": "EP DEV ACCT",
      "ExpirationDate": "2024-12-01T11:19:01.000Z",
      "ID": 2547,
      "IsExpired": false,
      "IsLockedOut": false,
      "TokenDescription": "EP DEV ACCT"
    }
  }
}
```
{% endtab %}

{% tab title="Header Parameters" %}
**Content-Type** string <mark style="color:orange;">required</mark>

Example: `application/json`

***

**Accept** string <mark style="color:orange;">required</mark>

Example: `application/json`
{% endtab %}

{% tab title="Body" %}
**AcctCode** string <mark style="color:purple;">optional</mark>

Account code that never changes

Example: `EP911XXXX`

***

**Token** string <mark style="color:purple;">optional</mark>

Token that expires every 2 years

Example: `2148B239CF6846BDA5D141BF4A4CFBE8`
{% endtab %}
{% endtabs %}
