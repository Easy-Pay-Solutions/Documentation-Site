---
description: Reconcile transactions
---

# Reconcile

<mark style="color:orange;">post:</mark> https://easypay5.com/APIcardProcREST/v1.0.0/Query/Reconcile

The reconcile Query is designed to be called at a specific periodic interval, perhaps once per day. We will return all the unique transaction IDs encountered during that interval. The query allows you to reconcile this list with data you have gathered during cardholder data interactions such as PayForm or Verifone Activity. If you find that a particular transaction is missing in your database you can call the TRANSACTION FULL DETAIL to consume any missing information.

You may specify either Credit Card or ACH transactions to be returned in the Query ( see qType parameter ) use "CARD" or "ACH". When choosing dates you can consider the StartDate to be Included in your data request however the EndDate will not. You will receive all data which runs up to but not including the end date. For example choosing the following dates will provide data for a single day on the calendar: "2024-12-01" "2024-12-02"

IMPORTANT: Do not call this method more than once a day. Excessive queries can cause your endpoint to be blocked. The max date range for this method is 31 days. The max records returned is 20,000. If you notice that the NumRecords returned equals 20000 then this means you have maxed out your query and you should use a smaller date range.

{% tabs %}
{% tab title="Sample Request" %}
```clike
{
  "StartDate": "2024-12-01T00:00:00.000Z",
  "EndDate": "2025-01-01T00:00:00.000Z",
  "qType": "CARD"
}
```
{% endtab %}

{% tab title="Sample Response" %}
```clike
{
  "ReconcileResult": {
    "ErrCode": 0,
    "ErrMsg": "",
    "FunctionOk": true,
    "NumRecords": 1,
    "RespMsg": "Successfully Returned Transaction Records : 1",
    "Transactions": [
      {
        "AMOUNT": 10,
        "CreatedOn": "2024-12-01T11:19:01.000Z",
        "Origin": "API",
        "TxID": -1,
        "TxSTATUS": "OPEN"
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
**StartDate** object <mark style="color:purple;">optional</mark>

The start date

Example: `2024-12-01T00:00:00.000Z`

***

**EndDate** object <mark style="color:purple;">optional</mark>

The end date

Example: `2025-01-01T00:00:00.000Z`

***

**qType** string <mark style="color:purple;">optional</mark>

Type of transactions returned

Example: `CARD`
{% endtab %}
{% endtabs %}
