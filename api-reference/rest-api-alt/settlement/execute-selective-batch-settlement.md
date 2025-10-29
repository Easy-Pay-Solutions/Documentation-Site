# Execute selective batch settlement

<mark style="color:orange;">post:</mark> https://easypay5.com/APIcardProcREST/v1.0.0/Settlement/ExecuteBatch\_Selective

{% tabs %}
{% tab title="Sample Request" %}
```clike
{
  "TransactionIDs": [
    52
  ],
  "MerchID": 1
}
```
{% endtab %}

{% tab title="Sample Response" %}
```clike
{
  "Settlement_ExecuteBatch_SelectiveResult": {
    "BatchResult": {
      "BatchClose": 720191352,
      "BatchLogID": 103,
      "BatchNetAmount": 10,
      "BatchNum": 3,
      "BatchOpen": 720191352,
      "BatchTransCount": 1,
      "Code": "A",
      "RemainingUnsettled": 0,
      "ResultText": "OK 003 0720 0000                ",
      "TxLock": "7A639CD720CE4B14"
    },
    "ErrCode": 0,
    "ErrMsg": "",
    "FunctionOk": true,
    "RespMsg": "Successful Settlement : OK 003 0720 0000                ",
    "SettlementApproved": true
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
**TransactionIDs** integer\[] <mark style="color:purple;">optional</mark>

List of transaction IDs to be settled

Example: `[52]`

***

**MerchID** integer <mark style="color:purple;">optional</mark>

The merchant identifier

Example: `1`
{% endtab %}
{% endtabs %}

