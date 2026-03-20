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

{% tab title="Notes" %}
To Implement Incremental Auth you can follow these steps:

* To Begin, you will need to create an AUTHORIZATION (AuthOnly) for a specific \
  amount using the PayForm or Virtual Terminal.
* You will need to take note of the ORIGINAL returned TxID as this must be sent in all \
  subsequent Incremental Authorizations using this API method.  &#x20;
* You can Increment the Authorization multiple times.
* When you are finished incrementing the authorization you have placed on the Cardholder account, you can then set the Finalize Flag to 1 . This will place the total authorized amount in the queue for settlement.  NO funds will be transferred until you have finalized the Authorization.
* You can set the finalize flag with a zero amount if you simply want to finalize without an additional increment.&#x20;
* Always send the ORIGINAL TXID in any case so that the system can reference all the activity properly.
* The API call returns the Total authorized amount each time you increment or Finalize or Both.
{% endtab %}
{% endtabs %}
