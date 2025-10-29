---
description: Search for transactions based on parameters
---

# Transaction Search

<mark style="color:orange;">post:</mark> https://easypay5.com/APIcardProcREST/v1.0.0/Query/Transaction

Easy Pay provides a variety of ways to search for and query transactions. To view a complete list of options, view the [https://easypaysoftware.com/en/Querying](https://easypaysoftware.com/en/Querying) Query Guide.

Use this call to search for transactions based on one or more parameters. A collection of transaction objects is returned. Transactions can be searched using several different parameters including the following.

* ID ( TxID ) ( Unique Identifier for the transaction )
* TRANSACTION STATUS ( OPEN , VOID, SETTLED, FAILED )
* DATE CREATED
* CARDHOLDER LAST NAME / FIRST NAME
* BATCH NUMBER ( Settlement group )
* TRANSACTION TYPE ( CCSALE, CCCREDIT , CCAUTHONLY)
* APPROVAL CODE / DECLINE CODE
* AMOUNT
* Reference ID (User defined field which can be searchable)
* RPGUID (Another user defined field which can be searchable)
* Last 4 Digits of the Card

{% tabs %}
{% tab title="Sample Request" %}
```clike
{
  "Query": "(A=-1)&&(B=-1)&&(C>='4/13/2023')&&(C<'4/29/2023')"
}
```
{% endtab %}

{% tab title="Sample Response" %}
```clike
{
  "Transaction_QueryResult": {
    "ErrCode": 0,
    "ErrMsg": "",
    "FunctionOk": true,
    "NumRecords": 5,
    "RespMsg": "Successfully Returned Transaction Records : 5",
    "Transactions": [
      {
        "ACCT_FIRST_NAME": "Sean",
        "ACCT_LAST_NAME": "Wood",
        "ACCT_NO": "4788XXXXXXXX8291",
        "AMOUNT": 10,
        "AVSr": "Y",
        "AcctHolderID": 3,
        "BatchLogID": 0,
        "BatchNO": 0,
        "BatchStatus": "N",
        "CARD_TYPE": "VI",
        "CASHBACK": 0,
        "CVVr": "",
        "CardPresent": true,
        "ConsentID": 0,
        "CreatedOn": "2024-12-01T11:19:01.000Z",
        "Credits": 0,
        "EMVPresent": false,
        "EMVRecTags": "",
        "EXP_DATE": "1028",
        "EndCustID": 44,
        "Flags": "",
        "HAuthorizedAmount": -1,
        "ID": 44,
        "IsLocked": false,
        "IsPartialApproval": false,
        "LAST_CHANGED_BY": "vidya_Venkatraman",
        "LastChangedOn": "2024-12-01T11:19:01.000Z",
        "MerchID": 1,
        "Origin": "API",
        "PAYMENT_TYPE": "C",
        "PartialAuthApproved": -1,
        "PreAuthID": 0,
        "PrepaidBalance": -1,
        "REF_ID": "A97689#",
        "RPGUID": "adf98580-b4ab-42fc-bb99-01c89964afe9",
        "RefTxID": 0,
        "SALE_TAX": 0,
        "SEQ_NO": 51,
        "SERVER": "",
        "SURCHARGE": 0,
        "TIP": 0,
        "TXN_CODE": 92682,
        "TXN_DATE": 42419,
        "TXN_DATETIME": "2024-12-01T11:19:01.000Z",
        "TXN_TIME": 82544,
        "TxLOCK": "7A639CD720CE4B14",
        "TxSTATUS": "OPEN",
        "TxType": "CCSALE",
        "UserID": 2547
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

A query string for obtaining specific transaction records using Number's query language. Build logical terms and join them with '&&' for logical AND or '||' for logical OR. Use single quotes for text and date values. Refer to the variable chart for query composition:

* A: MERCHANT ID - The merchant record you are interested in, e.g. (A=1).
* B: TRANSACTION STATUS - The status of the transaction, e.g. (B=1).
  * -1: ALL
  * 1: OPEN
  * 2: SETTLED
  * 3: FAILED
  * 4: RETURNED
  * 5: VOID
* C: DATE CREATED - The date the transaction was created, e.g. (C>='7/5/2024 12:00:00 AM').
* D: LAST NAME - Last name of the account holder, e.g. (D LIKE '%MITH') for all names that end with 'MITH'.
* E: TRANSACTION LOCK - Lock status of the transaction, e.g. (E<>'0') for locked transactions.
* H: TRANSACTION ID - The unique identifier for the transaction, e.g. (H=58258).
* J: FIRST NAME - First name of the account holder, e.g. (J LIKE 'ROB%') for all names that start with 'ROB'.
* K: TRANSACTION TYPE - The type of transaction, e.g. (K=-1).
  * -1: ALL
  * 1: ACHDEBIT
  * 2: ACHCREDIT
* L: AMOUNT - The $ amount of the transaction, e.g. (L>100.00).
* M: CLIENT REFERENCE ID - User-defined value on the transaction.
* N: RPGUID - User-defined value on the transaction.
* P: CONSENT ID - The Consent ID of card on file the transactions were charged against, e.g. (P=15875).
* Q: ACCOUNT NUMBER LAST 4 - The last 4 digits of a credit card, e.g. (Q='4123').
* R: APPROVAL CODE - The approval code for the transaction, e.g. (R='TAS626').
* S: CUSTOMER LAST NAME - The last name of the customer, e.g. (S='SMITH').
* T: CUSTOMER FIRST NAME - The first name of the customer, e.g. (T='FOSTER').
* U: ORIGIN - The origin of the transaction, e.g. (U='API').
  * "API": REST / SOAP API
  * "WID": Widget
  * "VT": Virtual Terminal

Example: `(B=3)&&(E=1)&&(C>'2024-09-01')`
{% endtab %}
{% endtabs %}

