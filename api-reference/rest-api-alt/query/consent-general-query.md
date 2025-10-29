# Consent General Query

<mark style="color:orange;">post:</mark> https://easypay5.com/APIcardProcREST/v1.0.0/Query/ConsentGeneral

Query general consent records using specific filter criteria.

{% tabs %}
{% tab title="Sample Request" %}
```clike
{
  "Query": "(A=-1)&&(G=1)&&(E>='3/29/2023')&&(E<'4/29/2023')"
}
```
{% endtab %}

{% tab title="Sample Response" %}
```clike
{
  "ConsentGeneral_QueryResult": {
    "Consents": [
      {
        "AcctHolderFirstName": "Sean",
        "AcctHolderID": 1140,
        "AcctHolderLastName": "Tester",
        "AcctNo": "0055",
        "AuthTxID": 2175,
        "ConsentType": "S",
        "CreatedBy": "Sally_Smith",
        "CreatedOn": "2024-12-01T11:19:01.000Z",
        "CustID": 1165,
        "CustomerRefID": "A1523644",
        "EndDate": "2024-12-01T11:19:01.000Z",
        "ID": 568,
        "IsEnabled": true,
        "MerchID": 1,
        "ModifiedBy": ":",
        "ModifiedOn": "2024-12-01T11:19:01.000Z",
        "NumDays": 2107,
        "RPGUID": "adf98580-b4ab-42fc-bb99-01c89964afe9",
        "ServiceDescrip": "REST Test",
        "StartDate": "2024-12-01T11:19:01.000Z"
      }
    ],
    "ErrCode": 0,
    "ErrMsg": "",
    "FunctionOk": true,
    "NumRecords": 1,
    "RespMsg": "Successfully Returned Consent Records : 1"
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

A query string for obtaining specific consent records using Number's query language. Build logical terms and join them with '&&' for logical AND or '||' for logical OR. Use single quotes for text and date values. Refer to the variable chart for query composition:

* A: MERCHANT ID - The merchant record you are interested in, e.g. (A=1).
* B: START DATE - The date the consent becomes active, e.g. (B>='10/20/2024').
* C: END DATE - The date the consent expires, e.g. (C<='10/20/2024').
* D: ACCOUNT HOLDER LAST NAME - Last name of the account holder, e.g. (D LIKE '%MITH') for all names that end with 'MITH'.
* E: CREATED ON - The date the consent was created, e.g. (E<='10/20/2024').
* F: CUSTOMER REFERENCE ID - User-defined value on the consent.
* G: CONSENT TYPE - The type of consent, e.g. (G='-1').
  * -1: ALL
  * 1: ANNUAL
  * 2: ONE-TIME
  * 3: RECURRING
  * 4: SUBSCRIPTION
* H: ENABLED - Indicates whether the consent is currently enabled, e.g. (H=1).
* J: RPGUID - User-defined value on the consent.
* K: ACCOUNT HOLDER FIRST NAME - First name of the account holder, e.g. (K LIKE 'ROB%') for all names that start with 'ROB'.
* Z: CONSENT ID - The unique identifier for the consent, e.g. (Z=15875).

Example: `(G=1)&&(B>'10/20/2024')`
{% endtab %}
{% endtabs %}
