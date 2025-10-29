# Modify a recurring payment schedule

<mark style="color:orange;">post:</mark> https://easypay5.com/APIcardProcREST/v1.0.0/RecurringSchedule/Modify

{% tabs %}
{% tab title="Sample Request" %}
```clike
{
  "SchedID": 10,
  "PaymentAmount": 10,
  "DueDate": "2023-07-10T00:00:00.000Z"
}
```
{% endtab %}

{% tab title="Sample Response" %}
```clike
{
  "RecurringSchedule_ModifyResult": {
    "ErrCode": 0,
    "ErrMsg": "",
    "FunctionOk": true,
    "RespMsg": "Successful Reschedule of SchedID 10 For $10.00 On 7/10/2023",
    "ScheduledPayment": {
      "AcctHolderID": 782,
      "AcctNo": 119,
      "ConsentID": 396,
      "ConsentType": "S",
      "DueOn": "2024-12-01T11:19:01.000Z",
      "ID": 282,
      "LastName": "Draper",
      "MerchID": 1,
      "OfTotalPayment": 100,
      "OfTotalPayments": 10,
      "PaymentAmt": 300,
      "PaymentNum": 1,
      "Period": "WEEKLY",
      "RPGUID": "adf98580-b4ab-42fc-bb99-01c89964afe9",
      "RStatus": "S",
      "SchedNum": 59,
      "Tries": 0,
      "TxID": -1
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
**SchedID** integer <mark style="color:purple;">optional</mark>

The unique identifier for the schedule to be modified

Example: `10`

***

**PaymentAmount** number · float <mark style="color:purple;">optional</mark>

The new $ payment amount for the schedule

Example: `10`

***

**DueDate** string · date <mark style="color:purple;">optional</mark>

The new due date for the schedule

Example: `2023-07-10T00:00:00.000Z`
{% endtab %}
{% endtabs %}

