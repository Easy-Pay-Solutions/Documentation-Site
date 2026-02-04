# Consent Annual Query APR

<mark style="color:orange;">post:</mark> https://easypay5.com/APIcardProcREST/v1.0.0/ConsentAnnual/QueryApr

Use this call to determine if the purchaser has a card on file. If you have created the consent (card on file) using a reference ID or PatientID then you can use the following Query to return an array of Consents ( Card On File Info ) for a particular patient with this PatientID:\
(F='213456')&&(H=1)&& (C>='01/21/2024')&#x20;

This will return consents with a particular PatientID which are still enabled and have not yet expired ( use todays date ).

You will want to present the user with the last 4 digits of each stored card so they can decide to choose a stored card or simply enter a new one. Number offers multiple ways of querying consent data.

{% tabs %}
{% tab title="Sample Request" %}
```clike
{
  "Query": "(A=1)&&(J='07e77e99-b16e-4b0f-8935-8d28e3fa28ef')"
}
```
{% endtab %}

{% tab title="Sample Response" %}
```clike
{
  "ConsentAnnual_Query_AprResult": {
    "Consents": [
      {
        "AcctFirstName": "MTIP08-1 DMC 13A",
        "AcctLastName": "MTIP08-1 DMC 13A",
        "AcctMask": "5457XXXXXXXX0012",
        "CardExpDate": "1225",
        "CardType": "MC",
        "ConsentType": "A",
        "CreatedOn": "\/Date(1642694960190-0500)\/",
        "CustomerRefID": "197",
        "EndDate": "\/Date(1767157200000-0500)\/",
        "ExpiredConsent": false,
        "ID": 386,
        "IsEnabled": true,
        "LimitLifeTime": 1000.0000,
        "LimitPerCharge": 100.0000,
        "MerchID": 1,
        "ModifiedOn": "\/Date(-62135578800000-0500)\/",
        "RPGUID": "07e77e99-b16e-4b0f-8935-8d28e3fa28ef",
        "Remaining": 1000.0000,
        "StartDate": "\/Date(1642654800000-0500)\/"
      }
    ],
    "ErrCode": 0,
    "ErrMsg": "",
    "FunctionOk": true,
    "NumRecords": 1,
    "RespMsg": "Successfully Returned Consent Records : 1"
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

