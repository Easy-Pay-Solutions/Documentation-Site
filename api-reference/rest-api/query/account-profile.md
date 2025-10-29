# Account profile

<mark style="color:orange;">post:</mark> https://easypay5.com/APIcardProcREST/v1.0.0/Query/AccountProfile

{% tabs %}
{% tab title="Sample Request" %}
```clike
```
{% endtab %}

{% tab title="Sample Response" %}
```clike
{
  "AccountProfileQryResult": {
    "AccountProfile": {
      "AccountCode": "EP9116875",
      "AccountName": "EP DEV ACCT",
      "AutoSchedule": true,
      "AutoSettle": true,
      "AutoSettleHour": 0,
      "AutoSettleMinute": 0,
      "BatchReport": false,
      "DateCreated": "2024-12-01T11:19:01.000Z",
      "DateModified": "2024-12-01T11:19:01.000Z",
      "ID": 205,
      "IndustryCode": "",
      "TimeZone": "Dateline Standard Time",
      "TransReport": false
    },
    "ErrCode": 0,
    "ErrMsg": "",
    "FunctionOk": true,
    "RespMsg": "Successfully Returned Account profile for Account ID 205"
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

{% endtab %}
{% endtabs %}

