# Receipt Details

<mark style="color:orange;">post:</mark> https://easypay5.com/APIcardProcREST/v1.0.0/Query/ReceiptDetail

{% tabs %}
{% tab title="Sample Request" %}
```clike
{
  "TxID": 12
}
```
{% endtab %}

{% tab title="Sample Response" %}
```clike
{
  "ReceiptDetail_QueryResult": {
    "ErrCode": 0,
    "ErrMsg": "",
    "FunctionOk": true,
    "ReceiptInfo": {
      "AC": null,
      "AID": "A0000000031010",
      "ARC": "00",
      "AcctHolderID": 1,
      "CardHolder": "Sean Wood",
      "CardNumber": "1111",
      "CardType": "VI",
      "EndCustID": 12,
      "EndCustomer": "JOHN DOE",
      "EntryType": "MANUAL",
      "MerchAddress": "45 spring street",
      "MerchCity": "portland",
      "MerchDescrip": "Test Merchant 1",
      "MerchEmail": "vidya",
      "MerchNumber": "700000000768",
      "MerchPhone": "2078548547",
      "MerchState": "Maine",
      "MerchTID": null,
      "MerchZip": "04101",
      "RefID": "",
      "TSI": "F800",
      "TVR": 8000,
      "TxAmount": 0,
      "TxDateTime": "2024-12-01T11:19:01.000Z",
      "TxID": 12,
      "TxStatus": "OPEN",
      "TxType": "CCAUTHONLY",
      "TxnCode": "297620"
    },
    "RespMsg": "Successfully Returned Receipt Detail for TxID 12"
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

Transaction ID for which to retrieve the receipt details

Example: `12`
{% endtab %}
{% endtabs %}
