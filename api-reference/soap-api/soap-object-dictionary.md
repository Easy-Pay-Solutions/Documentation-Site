---
description: >-
  A dictionary of the objects in some of the requests and responses of the SOAP
  API
---

# SOAP Object Dictionary

## User

Objects describing the user.

{% tabs %}
{% tab title="api_AuthUser" %}
`ID` int

Unique user ID.

Example: 2547

***

***

`AcctID` int

Example: 205

***

`APILocationID` int

Example: 2210

***

`ExpirationDate` datetime

Example: 2019-09-11T16:12:00-04:00

***

`DateCreated` datetime

Example: 2019-03-11T12:32:00-04:00

***

`DateModified` datetime

Example: 2019-03-11T12:32:00-04:00

***

`CreatedBy` string

Example: ADMIN : vidya Venkatraman

***

`IsExpired` boolean

Example: false

***

`IsLockedOut` boolean

Indicates if the account got locked out due to too many attempts.

***

`Alias` string

Example: vidya\_Venkatraman

***

`Description` string

Example: EP DEV ACCT

***

`TokenDescription` string

Example: EP DEV ACCT
{% endtab %}

{% tab title="api_MerchantInfo" %}
`ID` int

Unique merchant ID.

***

`Descrip` string

Example: Test Merchant 1

***

`TermID` string

Example: 006

***

`Location` string

Example: Lodging Merch

***

`Address` string

Example: 45 spring street portland Maine 04101
{% endtab %}
{% endtabs %}



***



## Account

Objects describing the account.

{% tabs %}
{% tab title="api_AccountProfile" %}
`ID` int

Unique account ID.

***

`AccountName` string

***

***

`AutoSettle` boolean

A setting which decides if transactions should automatically be settled for this account.

***

`AutoSchedule` boolean

***

`AutoSettleHour` int

The hour of the day to automatically settle transactions when `AutoSettle` is set to true.

***

`AutoSettleMinute` int

The minute of the hour to automatically settle transactions when `AutoSettle` is set to true.

***

`BatchReport` bool

Indicates whether a batch report should be generated each night after the settlement process runs.

***

`TransReport` bool

***

`DateCreated` datetime

***

`DateModified` datetime

***

`IndustryCode` string

***

`TimeZone` string

Example: Dateline Standard Time
{% endtab %}

{% tab title="api_AccountSettings" %}
`sKey` string

Name of the setting.

***

`sValue` string

Value of the setting under this key.

***

`sOptions` string

Additional options for the setting, if applicable.

***

`sGroup` string

Grouping of the setting, if applicable.

Example: api
{% endtab %}
{% endtabs %}



***



## ACH Transactions

Objects describing ACH transactions.

{% tabs %}
{% tab title="api_ACHDetail" %}
`ID` int

Unique ID of the ACH transaction.

***

`UniqueID` string

***

`TXstamp` string

The date when the transaction occurred, in MMDDYY format.

***

`TXN_DATETIME` datetime

The date and time when the transaction occurred,.

***

`AuthID` string

Example: 69017501

***

`ValMsg` string

Example: Success

***

***

`AcctType` string

Type of account associated with the transaction.

Values:\
\- "PersonalChecking"\
\- "PersonalSavings"\
\- "BusinessChecking"\
\- "BusinessSavings"

***

***

***

***

***

`AcctHolderID` int

Account holder unique ID.

***

`EndCustID` int

End customer unique ID.

***

***

***

`Credits` decimal

The $ amount of credits applied to the transaction.

***

`Amt` decimal

The total $ amount of the transaction.

***

`MerchID` int

The unique identifier for the merchant associated with the transaction.

***

***

`ResolvedOn` datetime

***

`SettledOn` datetime

***

`BatchNO` int

The batch number to which this transaction belongs.

***

`BatchStatus` string

The status of the batch.

Values:\
\- "N" (Not settled yet)\
\- "A" (Approved)\
\- "S" (Locked for resettlement)

***

`BatchLogID` int

The identifier for the batch log associated with the transaction.

***

`AcctLast4` string

***

`ReturnReason` string

***

`CustName` string

***

`FirstName` string

***

`LastName` string

***
{% endtab %}
{% endtabs %}



***



## Batch

Objects describing batch transactions.

{% tabs %}
{% tab title="api_batchSettleLog" %}
`ID` int

Unique batch ID.

***

`BatchNO` int

Number of the batch.

***

`BatchAmt` decimal

Example: 110.0

***

`BatchRecs` int

The number of transactions that were processed in the batch.

Example: 3

***

`TxLOCK` string

A unique value which represents the lock imposed on transactions prior to settlement. \
If the batch fails, the transaction will remain locked to prevent it from being merged with other settlements. In this situation, someone at Number will investigate and resettle the batch in its original grouping.

Example: 7A639CD720CE4B14

***

`CreatedOn` datetime

The date the record was created.

***

`FinishedOn` datetime

***

`CreatedBy` string

The username or identifier of the person who created the record.

***

`MerchID` int

Unique ID of the merchant associated with the batch.

***

`SettleResp` string

Example: APPROVAL Batch:512:Recs:3:$110.00

***

***

`BatchOpen` string

The timestamp indicating when the batch was opened, formatted as a string.

Example: 0720191352

***

`BatchClose` string

The timestamp indicating when the batch was closed, formatted as a string.

Example: 0720191352

***

`Released` int
{% endtab %}
{% endtabs %}



***



## Credit Card

Objects describing credit card information.

{% tabs %}
{% tab title="api_CardInfo" %}
`AccountNumber` string

The account number on the card.

***

`ExpMonth` int

The expiration month on the card.

***

`ExpYear` int

The full expiration year on the card or the last 2 digits.

***

`CSV` string

The CSV code from the back on the card used to prevent credit card fraud.
{% endtab %}

{% tab title="api_EmvReceipt" %}
`AID` string

Small bits of information encoded on the chip that identify the type of card.

***

`TSI` string

Transaction Status Indicator. Indicates the functions performed in transaction.

***

`TVR` string

Transaction Verification Result.

***

`AC` string

The Application Cryptogram code generated by the smart chip on the card during a transaction, used to protect against fraud.

***

`ARC` string

The Authorization Response Code.
{% endtab %}
{% endtabs %}



***



## Person

Objects describing people and locations.

{% tabs %}
{% tab title="api_Address" %}
`Address1` string

***

`Address2` string

***

`City` string

***

`State` string

***

`ZIP` string

***

`County` string
{% endtab %}

{% tab title="api_Person" %}
`Firstname` string

***

`Lastname` string

***

`Company` string

***

`Title` string

***

`Url` string

***

`BillIngAdress` [api\_Address](soap-object-dictionary.md#api_address) (object)

***

`Email` string

***

`Phone` string
{% endtab %}
{% endtabs %}



***



## Transactions

Objects describing transactions in general.

{% tabs %}
{% tab title="api_Amounts" %}
`TotalAmt` decimal

***

`SalesTax` decimal

***

`Surcharge` decimal

***

`Tip` decimal

***

`CashBack` decimal

***

`ClinicAmount` decimal

***

`VisionAmount` decimal

***

`PrescriptionAmount` decimal

***

`DentalAmount` decimal

***

`TotalMedicalAmount` decimal
{% endtab %}

{% tab title="api_Purchase" %}

{% tab title="api_PurchaseDetails" %}
***

***
{% endtab %}
{% endtabs %}



***



## Lodging

Objects describing sales related to lodging.

{% tabs %}
{% tab title="api_LodgingCheckInDetails" %}
`FirstName` string

***

`LastName` string

***

`AuthAmount` decimal

***

`Folio` string

***

`ArrivalDate` datetime

The date of arrival.

***

`Duration` int

The duration of stay in days.

***

`CustomerData` string

***

`ServiceDescription` string

Service description.

***
{% endtab %}

{% tab title="api_LodgingDetails" %}
`FirstName` string

***

`LastName` strring

***

`IsAuthOnly` boolean

***

`ConsentID4Auth` int

***

`Folio` string

***

`ArrivalDate` datetime

The date of arrival.

***

`DepartureDate` datetime

The date of departure.

***

`Duration` int

The duration of stay in days.

***

`ChargeDescriptor` int

Values: \
\- 0 (cdHealthClub) \
\- 1 (cdLodging) \
\- 2 (cdRestaurant) \
\- 3 (cdGiftShop) \
\- 4 (cdHairSalon) \
\- 5 (cdConventionFees) \
\- 6 (cdTennisClub) \
\- 7 (cdGolfShop)

***

`ChargeAmount` decimal

***

`ExtraChargeAmount` decimal

The extra charge $ amount related to the `ExtraChargesCode`.

***

***

`SaleCode` int

Values: \
\- 0 (scNotSet) \
\- 1 (scSale) \
\- 2 (scNoShow) \
\- 3 (scDeposit) \
\- 4 (scDelayedCharge) \
\- 5 (scExpressService) \
\- 6 (scAssuredReservation)

***

`StayID` int

The ID that is returned after a checkin.

***

`CustomerData` string
{% endtab %}
{% endtabs %}

***



## Annual Consent

Objects describing annual consent.



{% tabs %}
{% tab title="api_ConsentAnnual" %}
`ID` int

***

`AcctHolderID` int

***

`CustID` int

***

***

***

***

***

`AcctHolderLastName` string

***

`AcctHolderFirstName` string

***

`IsEnabled` bool

***

`StartDate` date

Start date for the consent.

***

`EndDate` date

End date for the consent.

***

***

`LimitLifeTime` decimal

Total $ limit for the lifetime of the consent.

***

`AuthTxID` int

***

`CreatedOn` date

***

`CreatedBy` date

***

`AcctNo` string
{% endtab %}

{% tab title="api_ConsentAnnualCreate" %}
***

***

***

***

`StartDate` date

Start date for the consent.

***
{% endtab %}

{% tab title="api_ConsentAnnualEditor" %}
`ExpMonth` int

Expiration month of the card.

***

`ExpYear` int

Full expiration year of the card or the last 2 digits.

***

`Email` string

Email address associated with the consent.

***

`Zip` string

ZIP code associated with the consent.

***

***

***

***

***

`LimitLifeTime` decimal

Total $ limit for the lifetime of the consent.
{% endtab %}

{% tab title="api_ConsentAnnualStats" %}
`ID` int

ID of the consent.

***

`IsEnabled` bool

***

`NumChargeAttempts` int

***

`NumFailedAttempts` int

***

`FirstChargeAttempt` date

***

`LastChargeAttempt` date

***

`TotalDollarsSettled` decimal

***

`TotalDollarsOpen` decimal

***

`LastSettledAmount` decimal

***

`LastChargeAmount` decimal

***

`RemainingInConsent` decimal

Total $ limit remaining for the consent.

***

`NumTx` int

***

`NumSettled` int

***

`NumFailed` int

***

`NumOpen` int

***

`LimitLifeTime` decimal

Total $ limit for the lifetime of the consent.
{% endtab %}
{% endtabs %}



