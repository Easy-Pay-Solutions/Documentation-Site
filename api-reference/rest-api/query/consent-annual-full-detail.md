# Consent Annual Full Detail

<mark style="color:orange;">post:</mark> https://easypay5.com/APIcardProcREST/v1.0.0/Query/ConsentAnnual\_FullDetail



{% tabs %}
{% tab title="Sample Request" %}
```clike
{
  "ConsentID": 12
}
```
{% endtab %}

{% tab title="Sample Response" %}
```clike
{
  "ConsentAnnual_FullDetailResult": {
    "AccounttHolder": {
      "AccountNum": "",
      "AcctMask": "4111XXXXXXXX1111",
      "Address1": "123 Fake St.",
      "Address2": "",
      "CardType": "VI",
      "City": "PORTLAND",
      "Company": "",
      "CreatedOn": "\/Date(1549853386493-0500)\/",
      "Email": "robert@easypaysolutions.com",
      "ExpDate": "1022",
      "Firstname": "Sean",
      "ID": 1,
      "LastChanged": "\/Date(1555496226490-0400)\/",
      "LastName": "Wood",
      "MerchID": 1,
      "Phone": "8777248472",
      "State": "ME",
      "Zip": "04106"
    },
    "ConsentAnnual": {
      "AcctHolderFirstName": "JOHN",
      "AcctHolderID": 1,
      "AcctHolderLastName": "DOE",
      "AcctNo": "1111",
      "AuthTxID": 15,
      "CreatedBy": "vidya_Venkatraman",
      "CreatedOn": "\/Date(1549942786773-0500)\/",
      "CustID": 15,
      "CustomerRefID": "A12345NO-99",
      "EndDate": "\/Date(1581483600000-0500)\/",
      "ID": 12,
      "IsEnabled": true,
      "LimitLifeTime": 1000000.0000,
      "LimitPerCharge": 1000000.0000,
      "MerchID": 1,
      "NumDays": 365,
      "RPGUID": "",
      "ServiceDescrip": "",
      "StartDate": "\/Date(1549947600000-0500)\/"
    },
    "EndCustomer": {
      "Address1": "21 ELM ST.",
      "Address2": "          ",
      "City": "TULSA     ",
      "ClientRefID": "A12345NO-99",
      "Company": "",
      "CreatedOn": "\/Date(1549942786770-0500)\/",
      "Email": "",
      "Firstname": "JOHN",
      "ID": 15,
      "LastChanged": "\/Date(1549942786770-0500)\/",
      "LastName": "DOE",
      "MerchID": 1,
      "Phone": "",
      "Service": "",
      "State": "          ",
      "Zip": "98324          "
    },
    "ErrCode": 0,
    "ErrMsg": "",
    "FunctionOk": true,
    "RespMsg": "Successfully Returned Full Detail For Consent ID : 12"
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
{% endtabs %}

