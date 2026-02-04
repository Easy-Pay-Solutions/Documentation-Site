# Charge a stored card

<mark style="color:orange;">post:</mark> https://easypay5.com/APIcardProcREST/v1.0.0/ConsentAnnual/ChargeStoredCard

This Method allows the user to charge a stored Card.

**ConsentID:** Please supply the ID of the Consent ( or stored card data )

**AlternateMerchID:** Here you can use ZERO if you plan to charge the same merchant record which was specified when saving the Card Info. You can use a positive integer if you plan to charge a merchant record which differs from the one originally used.

**purchDetails:** If you want to attach new reference data to the transaction you may do so using the following fields:

* ServiceDescrip : description of the transaction
* ClientRefID : your user defined reference ID
* RPGUID : another user defined reference ID&#x20;

If you choose NOT to supply these fields ( use empty string ) the system will pull this data from the original stored card data.

**Amounts:** Here you will supply the amount of the transaction. You may supply FEES but only if these have been properly configured for each Merchant record.

If you don't have FEES configured simply supply the BaseAmt and TotalAmt.

If you do Have Fees Configured you can call the method named: _Calculate Annual Consent Fees_ prior to calling this method.

You can specify fee values up to and including those determined using the above method.

If you specify values greater than those calculated above, then your value will be clamped.

_<mark style="color:$danger;">IMPORTANT : Always check your response to determine the fees which are APPROVED as this may differ from what was REQUESTED.</mark>_

**User:** Here you can assign a user to the sale so that we record the person which is initiating the sale within the integrator software.

{% tabs %}
{% tab title="Sample Request" %}
```clike
{
  "ConsentID": 8,
  "Amounts": {
    "BaseAmt": 52,
    "Surcharge": 1.04,
    "TotalAmt": 53.04
  },
  "purchDetails": {
    "ServiceDescrip": "Annual Checkup",
    "ClientRefID": "174356",
    "RPGUID": "99438332"
  },
  "AlternateMerchID": 0,
  "User": "Samuel"
}
```
{% endtab %}

{% tab title="Sample Response" %}
```clike
{
  "ConsentAnnual_ChargeStoredCardResult": {
    "AVSresult": "Y",
    "AcquirerResponseEMV": null,
    "CVVresult": "",
    "ErrCode": 0,
    "ErrMsg": "",
    "FunctionOk": true,
    "IsPartialApproval": false,
    "RequiresVoiceAuth": false,
    "RespMsg": "APPROVED OK1400",
    "ResponseApprovedAmount": 0,
    "ResponseAuthorizedAmount": 53.04,
    "ResponseBalanceAmount": 0,
    "TxApproved": true,
    "TxID": 37,
    "TxnCode": "OK1400",
    "ApprovedAmounts": {
      "BaseAmt": 52,
      "Surcharge": 1.04,
      "TotalAmt": 53.04
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
**ConsentID** integer <mark style="color:purple;">optional</mark>

ID of the consent (or stored card data)

Example: `8`

***

**Amounts** object <mark style="color:purple;">optional</mark>

***

**purchDetails** object <mark style="color:purple;">optional</mark>

***

**AlternateMerchID** integer <mark style="color:purple;">optional</mark>

Use 0 for the original merchant record or a positive integer for a different merchant record

Example: `0`

***

**User** string <mark style="color:purple;">optional</mark>

The user initiating the sale. Used for reporting.

Example: `Samuel`
{% endtab %}
{% endtabs %}
