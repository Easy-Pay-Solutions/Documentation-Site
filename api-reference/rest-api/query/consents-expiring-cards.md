# Consents Expiring Cards

<mark style="color:orange;">post:</mark> https://easypay5.com/APIcardProcREST/v1.0.0/Query/ConsentsExpiringCards

{% tabs %}
{% tab title="Sample Request" %}
```clike
{
  "NumDays": 20
}
```
{% endtab %}

{% tab title="Sample Response" %}
```clike
{
  "ConsentsExpiringCardsResult": {
    "Consents": [
      {
        "AcctHolderFirstName": "Bruce",
        "AcctHolderID": 78,
        "AcctHolderLastName": "Wayne",
        "AcctNo": "5439",
        "CardExpDate": "/Date(1703998800000-0500)/",
        "CardExpDateMMYY": "1228",
        "ConsentType": null,
        "CreatedBy": "Savannah_Tester",
        "CreatedByOrigin": "API",
        "CreatedOn": "/Date(1695651051350-0400)/",
        "CustID": 77,
        "CustomerRefID": "modify",
        "EndDate": "/Date(1727150400000-0400)/",
        "ID": 55,
        "IsEnabled": true,
        "MerchID": 3,
        "ModifiedOn": "/Date(1695651058587-0400)/",
        "RPGUID": "ConsentSubscription_Modify",
        "ServiceDescrip": "API Modify",
        "StartDate": "/Date(1695614400000-0400)/"
      },
      {
        "AcctHolderFirstName": "Bruce",
        "AcctHolderID": 90,
        "AcctHolderLastName": "Wayne",
        "AcctNo": "5439",
        "CardExpDate": "/Date(1703998800000-0500)/",
        "CardExpDateMMYY": "1228",
        "ConsentType": null,
        "CreatedBy": "Savannah_Tester",
        "CreatedByOrigin": "API",
        "CreatedOn": "/Date(1695733920813-0400)/",
        "CustID": 89,
        "CustomerRefID": "modify",
        "EndDate": "/Date(1727236800000-0400)/",
        "ID": 65,
        "IsEnabled": true,
        "MerchID": 1,
        "ModifiedOn": "/Date(1695733935477-0400)/",
        "RPGUID": "ConsentSubscription_Modify",
        "ServiceDescrip": "API Modify",
        "StartDate": "/Date(1695700800000-0400)/"
      },
      {
        "AcctHolderFirstName": "Test Card 15",
        "AcctHolderID": 843,
        "AcctHolderLastName": "UAT USA",
        "AcctNo": "0133",
        "CardExpDate": "/Date(1703998800000-0500)/",
        "CardExpDateMMYY": "1228",
        "ConsentType": null,
        "CreatedBy": "Savannah_Tester",
        "CreatedByOrigin": "SDK",
        "CreatedOn": "/Date(1700592744063-0500)/",
        "CustID": 862,
        "CustomerRefID": "",
        "EndDate": "/Date(1728964800000-0400)/",
        "ID": 427,
        "IsEnabled": true,
        "MerchID": 6,
        "ModifiedOn": "/Date(1703609621300-0500)/",
        "RPGUID": "",
        "ServiceDescrip": "",
        "StartDate": "/Date(1700542800000-0500)/"
      }
    ],
    "ErrCode": 0,
    "ErrMsg": "",
    "FunctionOk": true,
    "NumRecords": 3,
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
