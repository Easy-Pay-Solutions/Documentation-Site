# Incremental Auth

<mark style="color:orange;">post:</mark> https://easypay5.com/APIcardProcREST/v1.0.0/CardSale/IncrementAuth

{% tabs %}
{% tab title="Sample Request" %}
```clike
{
  "OrigAuthTxID": 111,
  "AdditionalAmt": 5.0,
  "Finalize": 0
}
```
{% endtab %}

{% tab title="Sample Response" %}
```clike
{
  "CreditCardSale_IncrementalResult": {
    "AVSresult": "Y",
    "AcquirerResponseEMV": null,
    "Amts": {
      "OrigAuthAmt": 10.0000,
      "ThisAuthAmt": 5.0,
      "TotalAuthAmt": 15.0000
    },
    "CVVresult": "",
    "ErrCode": 0,
    "ErrMsg": "",
    "FunctionOk": true,
    "IsPartialApproval": false,
    "RespMsg": "APPROVED OK8343",
    "TxApproved": true,
    "TxID": 112,
    "TxnCode": "OK8343"
  }
}
```
{% endtab %}
{% endtabs %}
