---
description: Retrieve voice settings
---

# Voice

<mark style="color:orange;">post:</mark> https://easypay5.com/APIcardProcREST/v1.0.0/Query/VoiceSettings

{% tabs %}
{% tab title="Sample Request" %}
```clike
{
  "TxID": 2
}
```
{% endtab %}

{% tab title="Sample Response" %}
```clike
{
  "VoiceSettingsQryResult": {
    "ErrCode": 0,
    "ErrMsg": "",
    "FunctionOk": true,
    "RespMsg": "Successfully Returned Voice Settings",
    "VoiceSettings": {
      "AccountHolder": "Sean Wood",
      "BankNumber": "067600",
      "CardNumber": "wDgEk7v5w7c=is9fm7hewavmpQks4Y5qRMNDNKGGk7on",
      "ChargeAmount": 0,
      "ExpDate": "1028",
      "MerchantID": "27150000350101",
      "PhoneNumber": "1-800-944-1111"
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

{% tab title="Body" %}
**TxID** integer <mark style="color:purple;">optional</mark>

The unique identifier for the transaction

Example: `2`


{% endtab %}
{% endtabs %}
