# Recurring Schedules

<mark style="color:orange;">post:</mark> https://easypay5.com/APIcardProcREST/v1.0.0/Query/RecurringSchedule

{% tabs %}
{% tab title="Sample Request" %}
```clike
{
  "Query": "(E=1)&&(H=4)"
}
```
{% endtab %}

{% tab title="Sample Response" %}
```clike
{
  "RecurringSchedule_QueryResult": {
    "ErrCode": 0,
    "ErrMsg": "",
    "FunctionOk": true,
    "NumRecords": 3,
    "RespMsg": "Successfully Returned Transaction Records : 3",
    "Schedule": [
      {
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
    ]
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
**Query** string <mark style="color:purple;">optional</mark>

A query string for obtaining specific recurring schedule records using Number's query language. Build logical terms and join them with '&&' for logical AND or '||' for logical OR. Use single quotes for text and date values. Refer to the variable chart for query composition:

* A: CONSENT ID - The unique identifier for the consent associated with the recurring schedule, e.g. (A=545).
* B: STATUS - The status of the recurring schedule, e.g. (B=-1).
  * -1: ALL
  * 1: SCHEDULED
  * 2: PAID
  * 3: FAILED
  * 4: CANCELLED
* C: DUE DATE - The date the next payment is due, e.g. (C='10/20/2024').
* D: ACCOUNT HOLDER LAST NAME - Last name of the account holder, e.g. (D LIKE '%MITH') for all names that end with 'MITH'.
* E: MERCHANT ID - The unique identifier for the merchant associated with the recurring schedule, e.g. (E=1).
* F: ACCOUNT NUMBER LAST 4 - The last 4 digits of the account number associated with the recurring schedule, e.g. (F='1234').
* G: SCHEDULE ID - The unique identifier for the recurring schedule, e.g. (G=12).
* H: TYPE - The type of recurring schedule, e.g. (H=-1).
  * -1: ALL
  * 3: RECURRING
  * 4: SUBSCRIPTION

Example: `(H=3)&&(C>='10/20/2024')`
{% endtab %}
{% endtabs %}
