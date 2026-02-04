# Annual Consent Stats

<mark style="color:orange;">post:</mark> https://easypay5.com/APIcardProcREST/v1.0.0/ConsentAnnual/Stats

{% tabs %}
{% tab title="Sample Request" %}
```clike
{
  "ConsentID": 10
}
```
{% endtab %}

{% tab title="Sample Response" %}
```clike
{
  "ConsentAnnual_StatsResult": {
    "ErrCode": 0,
    "ErrMsg": null,
    "FunctionOk": true,
    "RespMsg": "Successfully Returned Stats For Consent ID : 10",
    "Stats": {
      "FirstChargeAttempt": "\/Date(-62135578800000-0500)\/",
      "ID": 10,
      "IsEnabled": false,
      "LastChargeAmount": 0,
      "LastChargeAttempt": "\/Date(-62135578800000-0500)\/",
      "LastSettledAmount": 0,
      "LimitLifeTime": 100000.0000,
      "NumChargeAttempts": 0,
      "NumFailed": 0,
      "NumFailedAttempts": 0,
      "NumOpen": 0,
      "NumSettled": 0,
      "NumTx": 0,
      "RemainingInConsent": 100000.0000,
      "TotalDollarsOpen": 0,
      "TotalDollarsSettled": 0
    }
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
