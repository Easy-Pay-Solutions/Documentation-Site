---
hidden: true
icon: comment-dollar
---

# Msg Pay

One of our most popular features enables you to generate payment links on demand through the API and deliver them directly to cardholders via SMS or email.  Our newest revision of this feature is called “Message Pay’.&#x20;

The API call needed to invoke this activity is shown here:->  [Msg Pay](../../../api-reference/rest-api/msg-pay.md)&#x20;

This feature combines our ultra flexible [PayForm](https://docs.number.tech/documentation/getting-started/integration-options/payform) feature with a messaging system such as SMS or EMAIL. &#x20;

The PayForm component allows you to design the actual cardholder data collection format in advance. You may  be targeting a specific cardholder who owes a specific amount, or you may simply want to collect funds in more general terms. &#x20;

Before diving into the Message Pay feature, we encourage you to first get acquainted with the [PayForm](https://docs.number.tech/documentation/getting-started/integration-options/payform) feature, as this is the main component of Message Pay.  Added, is the messaging component which dictates the SMS or EMAIL specifics. &#x20;

***

With a single API call, you can define the following:

1. The number of fields on the form&#x20;
2. &#x20;Initial prepopulated data with Read-Only or editable attributes  &#x20;
3. The behavior and submission options of the form&#x20;
4. The style / appearance of the form &#x20;
5. The specific messaging aspects for Email or SMS &#x20;

The API call will  return a URL which is sent via SMS/EMAIL along with a custom message. &#x20;

If you are trying to collect a specific statement invoice you can also define and communicate the due date to the recipient.&#x20;

The standard Message Pay URL will be available for up to 3 months. After this period the generated URL will no longer be active. &#x20;

***

### Field Descriptions&#x20;

If you inspect the Json Request for this API call [HERE](../../../api-reference/rest-api/msg-pay.md), you will notice it is comprised of two parent objects &#x20;

1. Message parameters ( MsgParams ) &#x20;
2. PayForm parameters  ( InitParams) &#x20;

#### Message Parameters  (R = Required , O = Optional)&#x20;

* MessageType :    \[R]  ->  EMAIL, SMS or URLONLY
* MessageBody : \[O]  ->  Here you can define a message to accompany your payment link
* DueOn:  \[O] You can provide a due Date within your message
* ExpiresOn:  \[R]  You must supply a date with which the link will expire. Any dates beyond three months will be clamped
* SingleUsage: \[R}  Set value 1 if you expect a single payment for a specific statement amount. Set Value 0 if the URL provided can collect multiple transactions &#x20;

#### PayForm Parameters  (R = Required , O = Optional)

* MerchID:  \[R}  integer value pointing to a merchant record within the Account
* WTYPE:  \[ O ]  (not required)
* PostURL: \[O]  depending on your PayForm submission options  , we can send data to the URL of your choice regarding the transaction
* RedirectURL: \[O]  depending on your PayForm submission options  , we can redirect to a specific page once a transaction has been completed
* RPGUID: \[O]  this is a user defined field which you may want to tie to the transaction
* EndPoint: \[R]  this is determined by NUMBER (Use PF initially)
* EINDEX: \[O], Placing an integer here will force encryption when we send you submission data ( 300 is a sandbox Key )
* Amount: \[R] Required Amounts
* Surcharge: \[R] Required Amounts
* TotalAmt: \[R] Required Amounts
* "Firstname": \[O]  for prepopulating data on the PayForm
* "Lastname": \[O]  for prepopulating data on the PayForm
* "StreetAddress": \[O]  for prepopulating data on the PayForm
* "City":  \[O]  for prepopulating data on the PayForm
* "State": \[O]  for prepopulating data on the PayForm
* "ZIP":  \[O]  for prepopulating data on the PayForm
* "Country":  \[O]  for prepopulating data on the PayForm
* "Email": \[O]  this is required if choosing the EMAIL option
* "Phone": O]  this is required if choosing the SMSL option
* "Company": \[O]  for prepopulating data on the PayForm
* "eVisible": \[R] These are required Configuration settings : see PayForm
* "eReadOnly":  \[R] These are required Configuration settings : see PayForm
* "eStyles":  \[R] These are required Configuration settings : see PayForm
* "eSubmission":  \[R] These are required Configuration settings : see PayForm
* "eFeatures":  \[R] These are required Configuration settings : see PayForm
* "eColors":  \[R] These are required Configuration settings : see PayForm  &#x20;
