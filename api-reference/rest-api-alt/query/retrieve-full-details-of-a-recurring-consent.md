# Retrieve full details of a recurring consent

<mark style="color:orange;">post:</mark> https://easypay5.com/APIcardProcREST/v1.0.0/Query/ConsentRecurring\_FullDetail

{% tabs %}
{% tab title="Sample Request" %}
```clike
{
  "ConsentID": 24
}
```
{% endtab %}

{% tab title="Sample Response" %}
```clike
{
  "ConsentRecurring_FullDetailResult": {
    "AccounttHolder": {
      "AccountNum": "wj8HlAYlMJI=jvje9l7qZuEFiDDeEDDym6ZdlL0DX8HX",
      "AcctMask": "4111XXXXXXXX1111",
      "Address1": "123 Fake St",
      "Address2": "",
      "CardType": "VI",
      "City": "PORTLAND",
      "Company": "",
      "CreatedOn": "2024-12-01T11:19:01.000Z",
      "Email": "robert@easypaysolutions.com",
      "ExpDate": "1023",
      "Firstname": "Sean",
      "ID": 1,
      "LastChanged": "2024-12-01T11:19:01.000Z",
      "LastName": "Wood",
      "MerchID": 1,
      "Phone": "8777248472",
      "State": "ME",
      "Zip": "04106"
    },
    "ConsentRecurring": {
      "AcctHolderFirstName": "Sean",
      "AcctHolderID": 1,
      "AcctHolderLastName": "Wood",
      "AcctNo": "1111",
      "AuthTxID": 75,
      "CreatedBy": "vidya_Venkatraman",
      "CreatedOn": "2024-12-01T11:19:01.000Z",
      "CustID": 72,
      "CustRefID": "A123456",
      "EndDate": "2024-12-01T11:19:01.000Z",
      "ID": 24,
      "IsEnabled": true,
      "MerchID": 1,
      "ModifiedBy": ":",
      "ModifiedOn": "2024-12-01T11:19:01.000Z",
      "RAmtPaidSoFar": -1,
      "RLastPaymentAmt": 1000,
      "RNumPayments": 10,
      "RPGUID": "adf98580-b4ab-42fc-bb99-01c89964afe9",
      "RPaymentAmt": 1000,
      "RPeriod": "BI_WEEKLY",
      "RTotalAmt": 10000,
      "ServiceDescrip": "",
      "StartDate": "2024-12-01T11:19:01.000Z"
    },
    "EndCustomer": {
      "Address1": "123 Fake St.",
      "Address2": "          ",
      "City": "PORTLAND  ",
      "ClientRefID": "A123456",
      "Company": "",
      "CreatedOn": "2024-12-01T11:19:01.000Z",
      "Email": "robert@easypaysolutions.com",
      "Firstname": "Sean",
      "ID": 72,
      "LastChanged": "2024-12-01T11:19:01.000Z",
      "LastName": "Wood",
      "MerchID": 1,
      "Phone": "8777248472",
      "Service": "",
      "State": "ME        ",
      "Zip": "04106          "
    },
    "ErrCode": 0,
    "ErrMsg": "",
    "FunctionOk": true,
    "RespMsg": "Successfully Returned Full Detail For Consent ID : 24"
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

Consent ID for which to retrieve full details

Example: `24`
{% endtab %}
{% endtabs %}
