# Stored Card Only

The transact API call processes a payment and optionally stores the card for future use.

**This sample shows saving the card without processing a payment**_._&#x20;

{% hint style="info" %}
To save the card without processing a payment, set all of the request amount fields to zero and turn on the SaveCard flag. View the Sample Request tab for a complete example.
{% endhint %}

POST https://`[your-terminal-ip]`:8090/transact\
SessKey: `[your-session-key]`\
Content-Type: application/json

#### Response Status Codes

* 200 OK - Transaction submitted successfully. This does not mean the transaction was approved and processed; see the error handling section for more information.
* 401 Unauthorized - Missing or invalid SessKey
* 400 Bad Request - Invalid request format
* 500 Internal Server Error - Processing error

#### Error Handling

Please view our [API Best Practices](https://docs.number.tech/documentation/getting-started/basics/api-best-practices) guide for information on handling errors, logging responses, and checking for declines.

{% tabs %}
{% tab title="Sample Request" %}
{% code overflow="wrap" %}
```
{
  "MerchID": 2,
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
    "BaseAmt": 0,
    "Surcharge": 0,
    "TotalAmt": 0,
    "ConfirmTotalAmt": false
  },
  "Refdata": {
    "ServiceDesc": "Throat Culture",
    "ClientRefID": "1876345",
    "RPGuid": "dcaa9ac0-71a8-4dd4-ad2f-fbe107d1e789",
    "POSUser": "Sally Smith"
  }
}
```
{% endcode %}
{% endtab %}

{% tab title="Sample Response" %}
```
{
  "CreditCardSaleCompositeResult": {
    "AVSresult": null,
    "AcquirerResponseEMV": null,
    "CVVresult": null,
    "ErrCode": 0,
    "ErrMsg": "",
    "FunctionOk": true,
    "IsPartialApproval": false,
    "RequiresVoiceAuth": false,
    "RespMsg": "APPROVED 593742|CVV||AVS|",
    "ResponseApprovedAmount": 0,
    "ResponseAuthorizedAmount": 0,
    "ResponseBalanceAmount": 0,
    "TxApproved": true,
    "TxID": 22475, "TxnCode": null,
    "ConsentResult": {
      "CardLast4": "0885",
      "ConsentCreated": true,
      "ConsentID": 7891,
      "ConsentRequested": true,
      "ErrCode": 0,
      "ErrMsg": "",
      "ExpDate": "1249"
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
* **MerchID** (integer, required) - Merchant identification number
* **SaveCard** (integer, required) - Card storage flag (0 or 1). _Use 1 to store the card for future card not present transactions._
* **AcctHolder** (object, required) - Cardholder and billing information
* **Amounts** (object, required) - Transaction amount details:
* **BaseAmt** (number, required) - Base transaction amount
* **Surcharge** (number, required) - Surcharge/fee amount. You may supply a fee but only if these have been properly configured for each merchant record.
* **TotalAmt** (number, required) - Total amount (BaseAmt + Surcharge)
* **ConfirmTotalAmt** (boolean, optional, default: false) - If true, the customer will be shown an approve amount button on the Ingenico device.
* **Refdata** (object, required) - Reference data for transaction tracking: - **ServiceDesc** (string) - Description of service/product
* **ClientRefID** (string) - Client reference identifier
* **RPGuid** (string) - Unique transaction GUID
* **POSUser** (string) - POS user/operator name
{% endtab %}
{% endtabs %}

