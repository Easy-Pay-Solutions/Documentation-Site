# Process scheduled payments

<mark style="color:orange;">post:</mark> https://easypay5.com/APIcardProcREST/v1.0.0/RecurringSchedule/ProcessScheduledPayments

{% tabs %}
{% tab title="Sample Request" %}
```clike
{
  "MerchID": 1
}
```
{% endtab %}

{% tab title="Sample Response" %}
```clike
{
  "ProcessScheduledPaymentsResult": {
    "ApprovedPayments": [
      {
        "AcctNo": "1111",
        "CardHolder": "JOHN DOE",
        "CardType": "VI",
        "ConsentID": 6,
        "ConsentType": "S",
        "ErrMsg": "",
        "IsPartialApproval": false,
        "MerchID": 1,
        "PaymentAmt": 10,
        "PaymentDate": "2024-12-01T11:19:01.000Z",
        "PaymentNum": 1,
        "SEQ": "119",
        "SchedID": 1,
        "SchedNum": 1,
        "TxApproved": true,
        "TxID": 104,
        "TxnCode": 90944
      }
    ],
    "DeclinedPayments": [
      {
        "AcctNo": "1111",
        "CardHolder": "JOHN DOE",
        "CardType": "VI",
        "ConsentID": 6,
        "ConsentType": "S",
        "ErrMsg": "",
        "IsPartialApproval": false,
        "MerchID": 1,
        "PaymentAmt": 10,
        "PaymentDate": "2024-12-01T11:19:01.000Z",
        "PaymentNum": 1,
        "SEQ": "119",
        "SchedID": 1,
        "SchedNum": 1,
        "TxApproved": true,
        "TxID": 104,
        "TxnCode": 90944
      }
    ],
    "ErrCode": 0,
    "ErrMsg": "",
    "FunctionOk": true,
    "NumApproved": 2,
    "NumDeclined": 1,
    "NumPartialAuths": 0,
    "NumProcessed": 3,
    "RespMsg": "Total Processed: 3 Approved: 2 Declined: 1 Partial: 0"
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
**MerchID** integer <mark style="color:purple;">optional</mark>

The merchant identifier for processing payments

Example: `1`
{% endtab %}
{% endtabs %}

