# Process a Card Sale with Surcharge

<mark style="color:orange;">post:</mark> https://easypay5.com/APIcardProcNumber/v1.0.0/CardSale/WithOptions\
&#xNAN;_<mark style="color:$danger;">**For PCI compliant merchants only (AOC on file with Number required)**</mark>_

{% tabs %}
{% tab title="Sample Request" %}
```clike
{
  "MerchID": 1,
  "ccCardInfo": {
    "AccountNumber": "4111111111111111",
    "ExpMonth": 10,
    "ExpYear": 2028,
    "CSV": "122"
  },
  "AcctHolder": {
    "Firstname": "Sean",
    "Lastname": "Testing",
    "Company": "",
    "Title": "",
    "Url": "",
    "BillingAddress": {
      "Address1": "123 Fake St.",
      "Address2": "",
      "City": "PORTLAND",
      "State": "ME",
      "ZIP": "04106",
      "Country": "USA"
    },
    "Email": "robert@easypaysolutions.com",
    "Phone": "8777248472"
  },
  "EndCustomer": {
    "Firstname": "Sean",
    "Lastname": "Testing",
    "Company": "",
    "Title": "",
    "Url": "",
    "BillingAddress": {
      "Address1": "123 Fake St.",
      "Address2": "",
      "City": "PORTLAND",
      "State": "ME",
      "ZIP": "04106",
      "Country": "USA"
    },
    "Email": "tester@easypaysolutions.com",
    "Phone": "8777248472"
  },
  "Amounts": {
    "BaseAmt": 52,
    "Surcharge": 1.04,
    "TotalAmt": 53.04
  },
  "PurchItems": {
    "ServiceDescrip": "FROM API TESTER",
    "ClientRefID": "1876345",
    "RPGUID": "3d3424a6-c5f3-4c28-a294-490b6f674b41"
  }
}
```
{% endtab %}

{% tab title="Sample Response" %}
```clike
{
  "CreditCardSale_WithOptionsResult": {
    "AVSresult": "Y",
    "AcquirerResponseEMV": null,
    "CVVresult": "",
    "ErrCode": 0,
    "ErrMsg": "",
    "FunctionOk": true,
    "IsPartialApproval": false,
    "RequiresVoiceAuth": false,
    "RespMsg": "APPROVED 099804                 ",
    "ResponseApprovedAmount": -1,
    "ResponseAuthorizedAmount": -1,
    "ResponseBalanceAmount": -1,
    "TxApproved": true,
    "TxID": 41,
    "TxnCode": 99804,
    "ApprovedAmounts": {
      "BaseAmt": 52,
      "Surcharge": 1.04,
      "TotalAmt": 53.04
    }
  }
}
```
{% endtab %}

{% tab title="Body" %}
**MerchID** integer optional

Example: `1`

***

**ccCardInfo** object optional

> **AccountNum** string optional
>
> Example: `4111111111111111`
>
> ***
>
> **ExpMonth** integer optional
>
> Example: `10`
>
> ***
>
> **ExpYear** integer optional
>
> Example: `2028`
>
> ***
>
> **CSV** string optional

**AcctHolder** object optional

> **AccountNum** string optional
>
> The unique account number associated with the account holder.
>
> Example: `wj8HlAYlMJI=jvje9l7qZuEFiDDeEDDym6ZdlL0DX8HX`
>
> ***
>
> **AcctMask** string optional
>
> The masked version of the account number for security purposes.
>
> Example: `4111XXXXXXXX1111`
>
> ***
>
> **Address1** string optional
>
> The primary address line of the account holder.
>
> Example: `123 Fake St`
>
> ***
>
> **Address2** string optional
>
> The secondary address line of the account holder, if applicable.
>
> ***
>
> **CardType** string optional
>
> The type of card associated with the account (e.g., Visa, MasterCard).
>
> Example: `VI`
>
> ***
>
> **City** string optional
>
> The city where the account holder resides.
>
> Example: `PORTLAND`
>
> ***
>
> **Company** string optional
>
> The name of the company associated with the account holder, if applicable.
>
> ***
>
> **CreatedOn** string optional
>
> Date and time in Microsoft JSON date format (Unix timestamp and timezone offset).
>
> Example: `2024-12-01T11:19:01.000Z`
>
> ***
>
> **Email** string optional
>
> The email address of the account holder.
>
> Example: `robert@easypaysolutions.com`
>
> ***
>
> **ExpDate** string optional
>
> The expiration date of the card in MMYY format.
>
> Example: `1023`
>
> ***
>
> **Firstname** string optional
>
> The first name of the account holder.
>
> Example: `Sean`
>
> ***
>
> **ID** integer optional
>
> The unique identifier for the account holder in the system.
>
> Example: `1`
>
> ***
>
> **LastChanged** string optional
>
> Date and time in Microsoft JSON date format (Unix timestamp and timezone offset).
>
> Example: `2024-12-01T11:19:01.000Z`
>
> ***
>
> **LastName** string optional
>
> The last name of the account holder.
>
> Example: `Wood`
>
> ***
>
> **MerchID** integer optional
>
> The unique identifier for the merchant associated with the account.
>
> Example: `1`
>
> ***
>
> **Phone** string optional
>
> The phone number of the account holder.
>
> Example: `8777248472`
>
> ***
>
> **State** string optional
>
> The state where the account holder resides.
>
> Example: `ME`
>
> ***
>
> **Zip** string optional
>
> The postal code for the account holder's address.
>
> Example: `04106`

**EndCustomer** object optional

> **AccountNum** string optional
>
> The unique account number associated with the account holder.
>
> Example: `wj8HlAYlMJI=jvje9l7qZuEFiDDeEDDym6ZdlL0DX8HX`
>
> ***
>
> **AcctMask** string optional
>
> The masked version of the account number for security purposes.
>
> Example: `4111XXXXXXXX1111`
>
> ***
>
> **Address1** string optional
>
> The primary address line of the account holder.
>
> Example: `123 Fake St`
>
> ***
>
> **Address2** string optional
>
> The secondary address line of the account holder, if applicable.
>
> ***
>
> **CardType** string optional
>
> The type of card associated with the account (e.g., Visa, MasterCard).
>
> Example: `VI`
>
> ***
>
> **City** string optional
>
> The city where the account holder resides.
>
> Example: `PORTLAND`
>
> ***
>
> **Company** string optional
>
> The name of the company associated with the account holder, if applicable.
>
> ***
>
> **CreatedOn** string optional
>
> Date and time in Microsoft JSON date format (Unix timestamp and timezone offset).
>
> Example: `2024-12-01T11:19:01.000Z`
>
> ***
>
> **Email** string optional
>
> The email address of the account holder.
>
> Example: `robert@easypaysolutions.com`
>
> ***
>
> **ExpDate** string optional
>
> The expiration date of the card in MMYY format.
>
> Example: `1023`
>
> ***
>
> **Firstname** string optional
>
> The first name of the account holder.
>
> Example: `Sean`
>
> ***
>
> **ID** integer optional
>
> The unique identifier for the account holder in the system.
>
> Example: `1`
>
> ***
>
> **LastChanged** string optional
>
> Date and time in Microsoft JSON date format (Unix timestamp and timezone offset).
>
> Example: `2024-12-01T11:19:01.000Z`
>
> ***
>
> **LastName** string optional
>
> The last name of the account holder.
>
> Example: `Wood`
>
> ***
>
> **MerchID** integer optional
>
> The unique identifier for the merchant associated with the account.
>
> Example: `1`
>
> ***
>
> **Phone** string optional
>
> The phone number of the account holder.
>
> Example: `8777248472`
>
> ***
>
> **State** string optional
>
> The state where the account holder resides.
>
> Example: `ME`
>
> ***
>
> **Zip** string optional
>
> The postal code for the account holder's address.
>
> Example: `04106`

**Amounts** object optional

> **BaseAmt** number - float optional
>
> The base $ amount for the transaction before any additional charges.
>
> Example: `15`
>
> ***
>
> **Surcharge** number - float optional
>
> The surcharge $ amount added to the base amount, if applicable. Adjusted based on the total.
>
> Example: `1.04`
>
> ***
>
> **TotalAmt** number - float optional

**PurchItems** object optional

> **ServiceDescrip** string optional
>
> A description of the service or item.
>
> Example: `FROM API TESTER`
>
> ***
>
> **ClientRefID** string optional
>
> A reference ID provided by the client for tracking purposes.
>
> Example: `12456AA`
>
> ***
>
> **RPGUID** string optional
>
> A custom, user-defined reference ID or value.
>
> Example: `adf98580-b4ab-42fc-bb99-01c89964afe9`


{% endtab %}

{% tab title="Header Parameters" %}
**SessKey** string <mark style="color:$warning;">required</mark>

A unique session key used for authentication in API calls. This key is generated upon successful authentication and must be included in all subsequent requests.

Example: `A1842D663E9A4A72XXXXXXXX303541303234373138`

***

**Content-Type** string <mark style="color:$warning;">required</mark>

Example: `application/json`

***

**Accept** string <mark style="color:$warning;">required</mark>

Example: `application/json`
{% endtab %}
{% endtabs %}

