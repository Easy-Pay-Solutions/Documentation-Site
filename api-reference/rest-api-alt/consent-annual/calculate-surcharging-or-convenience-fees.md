# Calculate surcharging or convenience fees

<mark style="color:orange;">post:</mark> https://easypay5.com/APIcardProcREST/v1.0.0/ConsentAnnual/CalcFees

This API call is for merchant accounts that are specifically configured for surcharge and/or convenience fee processing. Prior to charging a card on file, you may use this method to properly calculate the intended fees (Surcharging or Convenience fees ).

Fees will be calculated based on the merchant configuration and the card type itself. It is important to show the calculated fees at the point of sale so that a cardholder can reject the sale if they desire.

You can specify a Alternate MerchID rather than use the merchant record originally designated when you saved the card. A Value Of ZERO will use the original Merchant record.

Once you have determined your fees you can then call the method named : Charge Stored Card with Options to authorize the sale.

{% tabs %}
{% tab title="Sample Request" %}
```clike
{
  "ConsentID": 7849,
  "Amount": 52,
  "AlternateMerchID": 0
}
```
{% endtab %}

{% tab title="Sample Response" %}
```clike
{
  "ConsentAnnual_CalcFeesResult": {
    "ErrCode": 0,
    "ErrMsg": "",
    "FunctionOk": true,
    "RespMsg": "Fees calculated for CREDIT Card 4663XXXXXXXX2741",
    "Amounts": {
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

ID for consent associated with the merchant account

Example: `7849`

***

**Amount** number · float <mark style="color:purple;">optional</mark>

Base $ amount for which fees are to be calculated

Example: `52`

***

**AlternateMerchID** integer <mark style="color:purple;">optional</mark>

ID of the merchant to collect the payment funds. Use 0 for the merchant on consent.

Example: `0`
{% endtab %}
{% endtabs %}
