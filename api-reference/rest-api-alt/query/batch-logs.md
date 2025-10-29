# Batch logs

<mark style="color:orange;">post:</mark> https://easypay5.com/APIcardProcREST/v1.0.0/Query/BatchLog

{% tabs %}
{% tab title="Sample Request" %}
```clike
{
  "Query": "(C>='7/19/2023')&&(C<'7/20/2023')"
}
```
{% endtab %}

{% tab title="Sample Response" %}
```clike
{
  "Batch_Log_QueryResult": {
    "BatchLogs": [
      {
        "BatchAmt": 110,
        "BatchClose": "020224054035",
        "BatchNO": 512,
        "BatchOpen": "020224054031",
        "BatchRecs": 3,
        "Code": "A",
        "CreatedBy": "AUTOSCHED",
        "CreatedOn": "2024-12-01T11:19:01.000Z",
        "FinishedOn": "2024-12-01T11:19:01.000Z",
        "ID": 612,
        "MerchID": 3,
        "Released": 0,
        "SettleResp": "APPROVAL Batch:512:Recs:3:$110.00",
        "TxLOCK": "7A639CD720CE4B14"
      }
    ],
    "ErrCode": 0,
    "ErrMsg": "",
    "FunctionOk": true,
    "NumRecords": 9,
    "RespMsg": "Successfully Returned Batch Log Records : 9"
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

A query string for obtaining specific batch log records using Number's query language. Build logical terms and join them with '&&' for logical AND or '||' for logical OR. Use single quotes for text and date values. Refer to the variable chart for query composition:

* A: MERCHANT ID - The merchant record you are interested in, e.g. (A=545).
* B: STATUS - The status of the batch log, e.g. (B=-1).
  * -1: ALL
  * 1: FAILED
  * 2: APPROVED
* C: CREATED ON - The date the batch log was created, e.g. (C>='3/2/2024')&&(C<='4/2/2024').
* D: BATCH LOG ID - The unique identifier for the batch log, e.g. (D=1777).
* E: BATCH NUMBER - The batch number for the batch log, e.g. (E=185).

Example: `(B=1)&&(C>='3/2/2024')&&(C<='4/2/2024')`
{% endtab %}
{% endtabs %}
