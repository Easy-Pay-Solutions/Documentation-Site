# Process a Combination Payment

The transact API call processes a payment and optionally stores the card for future use.

**This sample shows processing a payment and saving the card**. Look at the sample response tab to view the ConsentResult element.

<mark style="color:orange;">POST</mark> https://`[your-terminal-ip]`:8090/transact\
SessKey: `[your-session-key]`\
Content-Type: application/json

#### Response Status Codes

* 200 OK - Transaction submitted successfully. This does not mean the transaction was approved and processed; see the error handling section for more information.
* 401 Unauthorized - Missing or invalid SessKey
* 400 Bad Request - Invalid request format
* 500 Internal Server Error - Processing error

#### Error Handling

Please view our [API Best Practices](https://docs.number.tech/documentation/getting-started/basics/api-best-practices) guide for information on handling errors, logging responses, and checking for declines.

* Sample Request
* Sample Response
* Header Parameters
* Body

{% tabs %}
{% tab title="Sample Request" %}
```
{
  "MerchID": 1,
  "SaveCard": 1,
  "AcctHolder": {
    "Firstname": "Fred",
    "Lastname": "Smith",
    "Company": "",
    "Title": "",
    "Url": "",
    "BillingAddress": {
      "Address1": "1307 Broad Hollow Road",
      "Address2": "",
      "City": "",
      "State": "",
      "ZIP": "11747",
      "Country": "USA"
    },
    "Email": "tester@easypaysolutions.com",
    "Phone": "8777248472"
  },
  "Amounts": {
    "BaseAmt": 20.00,
    "Surcharge": 0,
    "TotalAmt": 20.00,
    "ConfirmTotalAmt": true
  },
  "Refdata": {
    "ServiceDesc": "Throat Culture",
    "ClientRefID": "1876345",
    "RPGuid": "dcaa9ac0-71a8-4dd4-ad2f-fbe107d1e789",
    "POSUser": "Sally Smith"
  }
}
```
{% endtab %}

{% tab title="Sample Response" %}
```
{
  "CreditCardSaleCompositeResult": {
    "AVSresult": "U",
    "AcquirerResponseEMV": "8A0230309F36020001",
    "CVVresult": "",
    "ErrCode": 0,
    "ErrMsg": "",
    "FunctionOk": true,
    "IsPartialApproval": false,
    "RequiresVoiceAuth": false,
    "RespMsg": "APPROVED 784823",
    "ResponseApprovedAmount": 0,
    "ResponseAuthorizedAmount": 20,
    "ResponseBalanceAmount": 0,
    "TxApproved": true,
    "TxID": 22469,
    "TxnCode": "784823",
    "ConsentResult": {
      "CardLast4": "0027",
      "ConsentCreated": true,
      "ConsentID": 7889,
      "ConsentRequested": true,
      "ErrCode": 0,
      "ErrMsg": "",
      "ExpDate": "1231"
    }
  }
 }
```

{% code overflow="wrap" %}
```
IMPORTANT: Always check your response to determine the fees which are approved as this may differ from what was requested. The ResponseAuthorizedAmount element shows the amount that was charged.
```
{% endcode %}
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
* **MerchID** (integer, required) - Merchant identification number&#x20;
* **SaveCard** (integer, required) - Card storage flag (0 or 1). Use 1 to store the card for future card not present transactions.
* **AcctHolder** (object, required) - Cardholder and billing information - **Amounts** (object, required) - Transaction amount details:
* **BaseAmt** (number, required) - Base transaction amount - **Surcharge** (number, required) - Surcharge/fee amount. You may supply a fee but only if these have been properly configured for each merchant record.
* **TotalAmt** (number, required) - Total amount (BaseAmt + Surcharge)
* **ConfirmTotalAmt** (boolean, optional, default: false) - If true, the customer will be shown an approve amount button on the Ingenico device.
* **Refdata** (object, required) - Reference data for transaction tracking:
* **ServiceDesc** (string) - Description of service/product
* **ClientRefID** (string) - Client reference identifier
* **RPGuid** (string) - Unique transaction GUID
* **POSUser** (string) - POS user/operator name
{% endtab %}
{% endtabs %}
