# Consents Expiring Cards 01

<mark style="color:orange;">post:</mark> https://easypay5.com/APIcardProcREST/v1.0.0/Query/ConsentsExpiringCards\_01

Query general consent records using specific filter criteria.

{% tabs %}
{% tab title="Sample Request" %}
```clike
{
  "StartDate": "7/10/2023",
  "EndDate": "8/9/2023"
}
```
{% endtab %}

{% tab title="Sample Response" %}
```clike
{
  "ConsentsExpiringCards_01Result": {
    "Consents": [
      {
        "AcctHolderFirstName": "Sally",
        "AcctHolderID": 541,
        "AcctHolderLastName": "Smith",
        "AcctNo": "5439",
        "CardExpDate": "/Date(1706677200000-0500)/",
        "CardExpDateMMYY": "0128",
        "ConsentType": null,
        "CreatedBy": "Savannah_Tester",
        "CreatedByOrigin": "WID",
        "CreatedOn": "/Date(1697832095713-0400)/",
        "CustID": 548,
        "CustomerRefID": "12345",
        "EndDate": "/Date(1706677200000-0500)/",
        "ID": 271,
        "IsEnabled": true,
        "MerchID": 3,
        "ModifiedOn": "/Date(-62135578800000-0500)/",
        "RPGUID": "54321",
        "ServiceDescrip": "",
        "StartDate": "/Date(1697774400000-0400)/"
      }
    ],
    "ErrCode": 0,
    "ErrMsg": "",
    "FunctionOk": true,
    "NumRecords": 1,
    "RespMsg": ""
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
