---
description: Retrieve full details of a transaction
---

# Transaction Full Detail

<mark style="color:orange;">post:</mark> https://easypay5.com/APIcardProcREST/v1.0.0/Query/Transaction\_FullDetail

Use this call to return all the details for a single transaction. Details are separated into 3 distinct objects including:

* AccountHolder (Card Holder)
* EndCustomer (Optional user entity if not the actual cardholder such as a child or spouse receiving the services)
* Transaction (All Transaction details)

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
  "Transaction_FullDetailResult": {
    "AccountHolder": {
      "AccountNum": "wj8HlAYlMJI=jvje9l7qZuEFiDDeEDDym6ZdlL0DX8HX",
      "AcctMask": "4111XXXXXXXX1111",
      "Address1": "123 Fake St",
      "Address2": "",
      "CardType": "VI",
      "City": "PORTLAND",
      "Company": "",
      "CreatedOn": "2024-12-01T11:19:01.000Z",
      "Email": "robert@easypaysolutions.com",
      "ExpDate": "1023",
      "Firstname": "Sean",
      "ID": 1,
      "LastChanged": "2024-12-01T11:19:01.000Z",
      "LastName": "Wood",
      "MerchID": 1,
      "Phone": "8777248472",
      "State": "ME",
      "Zip": "04106"
    },
    "EndCustomer": {
      "Address1": "123 Fake St.",
      "Address2": "          ",
      "City": "PORTLAND  ",
      "ClientRefID": "A123456",
      "Company": "",
      "CreatedOn": "2024-12-01T11:19:01.000Z",
      "Email": "robert@easypaysolutions.com",
      "Firstname": "Sean",
      "ID": 72,
      "LastChanged": "2024-12-01T11:19:01.000Z",
      "LastName": "Wood",
      "MerchID": 1,
      "Phone": "8777248472",
      "Service": "",
      "State": "ME        ",
      "Zip": "04106          "
    },
    "ErrCode": 0,
    "ErrMsg": "",
    "FunctionOk": true,
    "RespMsg": "Successfully Returned Transaction Detail Record",
    "Transaction": {
      "ACCT_FIRST_NAME": "JOHN",
      "ACCT_LAST_NAME": "DOE",
      "ACCT_NO": "4111XXXXXXXX1111",
      "AMOUNT": 0,
      "AVSr": "Y",
      "AcctHolderID": 1,
      "BatchLogID": 0,
      "BatchNO": -1,
      "BatchStatus": "N",
      "CARD_TYPE": "VI",
      "CASHBACK": 0,
      "CVVr": "",
      "CardPresent": false,
      "ConsentID": 0,
      "CreatedOn": "2024-12-01T11:19:01.000Z",
      "Credits": 0,
      "EMVPresent": false,
      "EMVRecTags": "",
      "EXP_DATE": "1028",
      "EndCustID": 12,
      "Flags": "",
      "HAuthorizedAmount": -1,
      "ID": 12,
      "IsLocked": false,
      "IsPartialApproval": false,
      "LAST_CHANGED_BY": "vidya_Venkatraman",
      "LastChangedOn": "2024-12-01T11:19:01.000Z",
      "MerchID": 1,
      "Origin": "WID",
      "PAYMENT_TYPE": "C",
      "PartialAuthApproved": -1,
      "PreAuthID": 0,
      "PrepaidBalance": -1,
      "REF_ID": "A97689#",
      "RPGUID": "adf98580-b4ab-42fc-bb99-01c89964afe9",
      "RefTxID": 0,
      "SALE_TAX": 0,
      "SEQ_NO": 16,
      "SERVER": "",
      "SURCHARGE": 0,
      "TIP": 0,
      "TXN_CODE": "297620",
      "TXN_DATE": 21219,
      "TXN_DATETIME": "2024-12-01T11:19:01.000Z",
      "TXN_TIME": "125122",
      "TxLOCK": "7A639CD720CE4B14",
      "TxSTATUS": "OPEN",
      "TxType": "CCAUTHONLY",
      "UserID": 2546
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

Transaction ID for which to retrieve the receipt details

Example: `12`
{% endtab %}
{% endtabs %}
