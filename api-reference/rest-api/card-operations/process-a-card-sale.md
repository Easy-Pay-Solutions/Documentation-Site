---
description: Process a card sale with card present
---

# Process a Card Sale

<mark style="color:orange;">post:</mark> https://easypay5.com/APIcardProcREST/v1.0.0/CardSale/CardPresent

_<mark style="color:$danger;">**For PCI compliant merchants only (AOC on file with Number required)**</mark>_

{% tabs %}
{% tab title="Sample Request" %}
```clike
{
  "Track": "%B4788250000028291^VISA TEST/GOOD^231010100733000000?;4895390000000013=151210100000733?",
  "AcctHolder": {
    "Firstname": "Sean",
    "Lastname": "Wood",
    "Company": "",
    "Title": "",
    "Url": "",
    "BillIngAdress": {
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
    "Lastname": "Wood",
    "Company": "",
    "Title": "",
    "Url": "",
    "BillIngAdress": {
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
  "Amounts": {
    "TotalAmt": 10,
    "SalesTax": 0,
    "Surcharge": 0,
    "Tip": 0,
    "CashBack": 0,
    "ClinicAmount": 0,
    "VisionAmount": 0,
    "PrescriptionAmount": 0,
    "DentalAmount": 0,
    "TotalMedicalAmount": 0
  },
  "PurchItems": {
    "ServiceDescrip": "FROM API TESTER",
    "ClientRefID": "",
    "RPGUID": "a8e2bbfc-e423-4a84-a9e9-2a6e08153368"
  },
  "MerchID": 1
}
```
{% endtab %}

{% tab title="Sample Response" %}
```clike
{
  "CreditCardSale_CardPresentResult": {
    "AVSresult": "Y",
    "AcquirerResponseEMV": null,
    "CVVresult": "",
    "ErrCode": 0,
    "ErrMsg": "",
    "FunctionOk": true,
    "IsPartialApproval": false,
    "RequiresVoiceAuth": false,
    "RespMsg": "APPROVED 092682",
    "ResponseApprovedAmount": "-1Pl",
    "ResponseAuthorizedAmount": -1,
    "ResponseBalanceAmount": -1,
    "TxApproved": true,
    "TxID": 44,
    "TxnCode": 92682
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
**Track** string <mark style="color:purple;">optional</mark>

Example: `%B4788250000028291^VISA TEST/GOOD^231010100733000000?;4895390000000013=151210100000733?`

***

**AcctHolder** object <mark style="color:purple;">optional</mark>

> **AccountNum** string <mark style="color:purple;">optional</mark>
>
> The unique account number associated with the account holder.
>
> Example: `wj8HlAYlMJI=jvje9l7qZuEFiDDeEDDym6ZdlL0DX8HX`
>
> ***
>
> **AcctMask** string <mark style="color:purple;">optional</mark>
>
> The masked version of the account number for security purposes.
>
> Example: `4111XXXXXXXX1111`
>
> ***
>
> **Address1** string <mark style="color:purple;">optional</mark>
>
> The primary address line of the account holder.
>
> Example: `123 Fake St`
>
> ***
>
> **Address2** string <mark style="color:purple;">optional</mark>
>
> The secondary address line of the account holder, if applicable.
>
> ***
>
> **CardType** string <mark style="color:purple;">optional</mark>
>
> The type of card associated with the account (e.g., Visa, MasterCard).
>
> Example: `VI`
>
> ***
>
> **City** string <mark style="color:purple;">optional</mark>
>
> The city where the account holder resides.
>
> Example: `PORTLAND`
>
> ***
>
> **Company** string <mark style="color:purple;">optional</mark>
>
> The name of the company associated with the account holder, if applicable.
>
> ***
>
> **CreatedOn** string <mark style="color:purple;">optional</mark>
>
> Date and time in Microsoft JSON date format (Unix timestamp and timezone offset).
>
> Example: `2024-12-01T11:19:01.000Z`
>
> ***
>
> **Email** string <mark style="color:purple;">optional</mark>
>
> The email address of the account holder.
>
> Example: `robert@easypaysolutions.com`
>
> ***
>
> **ExpDate** string <mark style="color:purple;">optional</mark>
>
> The expiration date of the card in MMYY format.
>
> Example: `1023`
>
> ***
>
> **Firstname** string <mark style="color:purple;">optional</mark>
>
> The first name of the account holder.
>
> Example: `Sean`
>
> ***
>
> **ID** integer <mark style="color:purple;">optional</mark>
>
> The unique identifier for the account holder in the system.
>
> Example: `1`
>
> ***
>
> **LastChanged** string <mark style="color:purple;">optional</mark>
>
> Date and time in Microsoft JSON date format (Unix timestamp and timezone offset).
>
> Example: `2024-12-01T11:19:01.000Z`
>
> ***
>
> **LastName** string <mark style="color:purple;">optional</mark>
>
> The last name of the account holder.
>
> Example: `Wood`
>
> ***
>
> **MerchID** integer <mark style="color:purple;">optional</mark>
>
> The unique identifier for the merchant associated with the account.
>
> Example: `1`
>
> ***
>
> **Phone** string <mark style="color:purple;">optional</mark>
>
> The phone number of the account holder.
>
> Example: `8777248472`
>
> ***
>
> **State** string <mark style="color:purple;">optional</mark>
>
> The state where the account holder resides.
>
> Example: `ME`
>
> ***
>
> **Zip** string <mark style="color:purple;">optional</mark>
>
> The postal code for the account holder's address.
>
> Example: `04106`

**EndCustomer** object <mark style="color:purple;">optional</mark>

> **AccountNum** string <mark style="color:purple;">optional</mark>
>
> The unique account number associated with the account holder.
>
> Example: `wj8HlAYlMJI=jvje9l7qZuEFiDDeEDDym6ZdlL0DX8HX`
>
> ***
>
> **AcctMask** string <mark style="color:purple;">optional</mark>
>
> The masked version of the account number for security purposes.
>
> Example: `4111XXXXXXXX1111`
>
> ***
>
> **Address1** string <mark style="color:purple;">optional</mark>
>
> The primary address line of the account holder.
>
> Example: `123 Fake St`
>
> ***
>
> **Address2** string <mark style="color:purple;">optional</mark>
>
> The secondary address line of the account holder, if applicable.
>
> ***
>
> **CardType** string <mark style="color:purple;">optional</mark>
>
> The type of card associated with the account (e.g., Visa, MasterCard).
>
> Example: `VI`
>
> ***
>
> **City** string <mark style="color:purple;">optional</mark>
>
> The city where the account holder resides.
>
> Example: `PORTLAND`
>
> ***
>
> **Company** string <mark style="color:purple;">optional</mark>
>
> The name of the company associated with the account holder, if applicable.
>
> ***
>
> **CreatedOn** string <mark style="color:purple;">optional</mark>
>
> Date and time in Microsoft JSON date format (Unix timestamp and timezone offset).
>
> Example: `2024-12-01T11:19:01.000Z`
>
> ***
>
> **Email** string <mark style="color:purple;">optional</mark>
>
> The email address of the account holder.
>
> Example: `robert@easypaysolutions.com`
>
> ***
>
> **ExpDate** string <mark style="color:purple;">optional</mark>
>
> The expiration date of the card in MMYY format.
>
> Example: `1023`
>
> ***
>
> **Firstname** string <mark style="color:purple;">optional</mark>
>
> The first name of the account holder.
>
> Example: `Sean`
>
> ***
>
> **ID** integer <mark style="color:purple;">optional</mark>
>
> The unique identifier for the account holder in the system.
>
> Example: `1`
>
> ***
>
> **LastChanged** string <mark style="color:purple;">optional</mark>
>
> Date and time in Microsoft JSON date format (Unix timestamp and timezone offset).
>
> Example: `2024-12-01T11:19:01.000Z`
>
> ***
>
> **LastName** string <mark style="color:purple;">optional</mark>
>
> The last name of the account holder.
>
> Example: `Wood`
>
> ***
>
> **MerchID** integer <mark style="color:purple;">optional</mark>
>
> The unique identifier for the merchant associated with the account.
>
> Example: `1`
>
> ***
>
> **Phone** string <mark style="color:purple;">optional</mark>
>
> The phone number of the account holder.
>
> Example: `8777248472`
>
> ***
>
> **State** string <mark style="color:purple;">optional</mark>
>
> The state where the account holder resides.
>
> Example: `ME`
>
> ***
>
> **Zip** string <mark style="color:purple;">optional</mark>
>
> The postal code for the account holder's address.
>
> Example: `04106`

**Amounts** object <mark style="color:purple;">optional</mark>

> **TotalAmt** number <mark style="color:purple;">optional</mark>
>
> The total $ amount to be charged.
>
> Example: `10`
>
> ***
>
> **SalesTax** number <mark style="color:purple;">optional</mark>
>
> Example: `0`
>
> ***
>
> **Surcharge** number <mark style="color:purple;">optional</mark>
>
> The surcharge $ amount added to the base amount, if applicable.
>
> Example: `0`
>
> ***
>
> **Tip number** <mark style="color:purple;">optional</mark>
>
> Example: `0`
>
> ***
>
> **CashBack** number <mark style="color:purple;">optional</mark>
>
> Example: `0`
>
> ***
>
> **ClinicAmount** number <mark style="color:purple;">optional</mark>
>
> Example: `0`
>
> ***
>
> **VisionAmount** number <mark style="color:purple;">optional</mark>
>
> Example: `0`
>
> ***
>
> **PrescriptionAmount** number <mark style="color:purple;">optional</mark>
>
> Example: `0`
>
> ***
>
> **DentalAmount** number <mark style="color:purple;">optional</mark>
>
> Example: `0`
>
> ***
>
> **TotalMedicalAmount** number <mark style="color:purple;">optional</mark>
>
> Example: `0`

**PurchItems** object <mark style="color:purple;">optional</mark>

> **ServiceDescrip** string <mark style="color:purple;">optional</mark>
>
> A description of the service or item.
>
> Example: `FROM API TESTER`
>
> ***
>
> **ClientRefID** string <mark style="color:purple;">optional</mark>
>
> A reference ID provided by the client for tracking purposes.
>
> Example: `12456AA`
>
> ***
>
> **RPGUID** string <mark style="color:purple;">optional</mark>
>
> A custom, user-defined reference ID or value.
>
> Example: `adf98580-b4ab-42fc-bb99-01c89964afe9`

**MerchID** integer <mark style="color:purple;">optional</mark>

Example: `1`
{% endtab %}
{% endtabs %}

