# Consent Annual Query

<mark style="color:orange;">post:</mark> https://easypay5.com/APIcardProcREST/v1.0.0/Query/ConsentAnnual

Use this call to determine if the purchaser has a card on file. If you have created the consent (card on file) using a reference ID or PatientID then you can use the following Query to return an array of Consents ( Card On File Info ) for a particular patient with this PatientID:\
(F='213456')&&(H=1)&& (C>='01/21/2024')&#x20;

This will return consents with a particular PatientID which are still enabled and have not yet expired ( use todays date ).

You will want to present the user with the last 4 digits of each stored card so they can decide to choose a stored card or simply enter a new one. Number offers multiple ways of querying consent data.

{% tabs %}
{% tab title="Sample Request" %}
```clike
{
  "Query": "(A=-1)&&(G=1)&&(H='True')"
}
```
{% endtab %}

{% tab title="Sample Response" %}
```clike
{
  "ConsentAnnual_QueryResult": {
    "Consents": [
      {
        "AcctHolderFirstName": "JOHN",
        "AcctHolderID": 1,
        "AcctHolderLastName": "DOE",
        "AcctNo": "1111",
        "AuthTxID": 15,
        "CreatedBy": "John_Doe",
        "CreatedOn": "2024-12-01T11:19:01.000Z",
        "CustID": 15,
        "CustomerRefID": "A12345NO-99",
        "EndDate": "2024-12-01T11:19:01.000Z",
        "ID": 12,
        "IsEnabled": true,
        "LimitLifeTime": 1000000,
        "LimitPerCharge": 1000000,
        "MerchID": 1,
        "NumDays": 365,
        "RPGUID": "adf98580-b4ab-42fc-bb99-01c89964afe9",
        "ServiceDescrip": "",
        "StartDate": "2024-12-01T11:19:01.000Z"
      }
    ],
    "ErrCode": 0,
    "ErrMsg": "",
    "FunctionOk": true,
    "NumRecords": 2,
    "RespMsg": "Successfully Returned Consent Records : 2"
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

