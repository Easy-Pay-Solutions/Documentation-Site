---
description: Getting started with iOS SDK for Number
---

# iOS SDK

The EasyPay iOS SDK offers access to the Number API for effortless integration with any iOS application. For Android integration, refer to the [Android SDK integration guide](android-sdk.md).



***



## Installation

### Requirements

* Xcode 15 or above
* Compatible with iOS 13.0 or above

### Configuration

{% stepper %}
{% step %}
Setup with Swift Package Manager

```swift
.package(url: "https://github.com/Easy-Pay-Solutions/Mobile-SDK-IOS.git", from: "1.0.6")
```
{% endstep %}

{% step %}
Setup with Cocoapods

```ruby
pod 'EasyPay'
```
{% endstep %}
{% endstepper %}



***



## Get started

### Integration

{% stepper %}
{% step %}
Prerequisites - get HMAC secret, API key and optional Sentry DSN from Number.
{% endstep %}

{% step %}

{% step %}
During the initialization, the process of downloading the certificate is starting. Proceeding with any call before downloading has finished will result in an error `RsaCertificateError.failedToLoadCertificateData`.&#x20;

You can check the status of downloading by accessing the following enum:

```swift
EasyPay.shared.certificateStatus
```
{% endstep %}

{% step %}
To enable jailbreak detection, please set `isProduction = true` when initializing the library and add the following URL schemes to main `Info.plist`.

```xml
<key>LSApplicationQueriesSchemes</key>
<array>
    <string>undecimus</string>
    <string>sileo</string>
    <string>zbra</string>
    <string>filza</string>
    <string>activator</string>
</array>
```
{% endstep %}
{% endstepper %}



### Using widgets

Number's prebuilt payment UI components allow you to collect and process credit card information and payments in a secure way.

#### Managing cards

For managing saved cards without paying, the following initializer should be used:

```swift
 CardSelectionViewController(selectionDelegate: AnyObject, preselectedCardId: Int?, paymentDetails: AddAnnualConsentWidgetModel) throws
```

`preselectedCardId` is an optional parameter that allows to mark a card as selected by passing the `ConsentId` of this card. If nil or incorrect, the selection will be ignored.

`paymentDetails` parameter is used for passing additional payment details not visible for the end user. Either `customerReferenceId` or `rpguid` must be provided to get the list of consents of a specific customer. In case of of incorrect initialization data, `CardSelectionViewControllerInitError` will be thrown.

If you would like to receive callbacks, conform to `CardSelectionDelegate` with following methods:

```swift
func didSelectCard(consentId: String) {}
```

```swift
func didDeleteCard(consentId: Int, success: Bool) {}
```

```swift
func didSaveCard(consentId: Int?, 
                 expMonth: Int?,
                 expYear: Int?,
                 last4digits: String?,
                 success: Bool)  {}
```

#### Managing cards and payment

For managing saved cards and paying, following initializer should be used:

```swift
CardSelectionViewController(amount: String, paymentDelegate: AnyObject, preselectedCardId: Int?, paymentDetails: AddAnnualConsentWidgetModel) throws
```

`amount` should be higher than 0 and it is required parameter.

`preselectedCardId` is an optional parameter that allows to mark a card as selected by passing the `ConsentId` of this card. If nil or incorrect, the selection will be ignored.

`paymentDetails` parameter is used for passing additional payment details not visible for the end user. Either `customerReferenceId` or `rpguid` must be provided to get the list of consents of a specific customer. In case of of incorrect initialization data, `CardSelectionViewControllerInitError` will be thrown.

If you would like to receive callbacks, conform to `CardPaymentDelegate` with following methods:

```swift
func didPayWithCard(consentId: Int?, paymentData: PaymentData?, success: Bool) {}
```

```swift
func didDeleteCard(consentId: Int, success: Bool) {}
```



### Screenshots

#### **Save Card**

<figure><img src="../../../.gitbook/assets/Save card - mobile (1).png" alt=""><figcaption></figcaption></figure>

<figure><img src="../../../.gitbook/assets/Save card - Tablet (1).png" alt=""><figcaption></figcaption></figure>

#### **Manage Cards**

<figure><img src="../../../.gitbook/assets/Manage Cards - Mobile.png" alt=""><figcaption></figcaption></figure>

<figure><img src="../../../.gitbook/assets/Manage Cards - Tablet.png" alt=""><figcaption></figcaption></figure>

#### **Store and Pay**

<figure><img src="../../../.gitbook/assets/Store and Pay - Mobile.png" alt=""><figcaption></figcaption></figure>

<figure><img src="../../../.gitbook/assets/Store and Pay - Tablet.png" alt=""><figcaption></figcaption></figure>



***



## Common components

### SecureTextField component

The SDK's widgets use a component called `SecureTextField` which ensures a safe input of credit card numbers. It is a subclass of `UITextField` which enables freedom of styling as needed.

Setting up requires configuring the certificate once it was downloaded to encrypt credit card data.

```swift
nameOfYourTextField.setupConfig(EasyPay.shared.config)
```

To receive the encrypted card string required to send to the API, you can use the following method:

```swift
nameOfYourTextField.encryptCardData()
```

{% hint style="info" %}
Data in the SecureTextField component is already encrypted and can be used in the API calls without any additional encryption.
{% endhint %}



***



## Common objects

Below you'll find code describing some of the objects that are commonly used in requests or responses. You can use it as a reference. The code includes parameter names and types.



### `CreditCardInfo`

The object consists of the following fields:

```swift
let accountNumber: String //credit card number encoded in base 64
let expirationMonth: Int?
let expirationYear: Int?
let cvv: String
```



### `AccountHolder`

The object consists of the following fields:

```swift
let firstName: String
let lastName: String
let company: String?
let billingAddress: BillingAddress
let email: String?
let phone: String?
```



### `BillingAddress`

The object consists of the following fields:

```swift
let address1: String
let address2: String?
let city: String?
let state: String?
let zip: String
let country: String?
```



### `EndCustomer`

The object consists of the following fields:

```swift
let firstName: String?
let lastName: String?
let company: String?
let billingAddress: EndCustomerBillingAddress?
let email: String?
let phone: String?
```



### `EndCustomerBillingAddress`

The object consists of the following fields:

```swift
let address1: String?
let address2: String?
let city: String?
let state: String?
let zip: String?
let country: String?
```



### `Amounts`

The object consists of the following fields:

```swift
let totalAmount: String
let salesAmount: String?
let surcharge: String?
```



### `PurchItems`

The object consists of the following fields:

```swift
let serviceDescription: String?
let clientRefId: String?
let rpguid: String?
```



### `CreateConsentAnnual`

The object consists of the following fields:

```swift
let merchID: Int?
let customerRefID: String?
let serviceDescrip: String?
let rpguid: String?
let startDate: String //Timestamp in milliseconds in format \/Date(1710936735853)\/
let limitPerCharge: String
let limitLifeTime: String
```



### `AnnualEndCustomer`

The object consists of the following fields:

```swift
let firstName: String?
let lastName: String?
let company: String?
let billingAddress: AnnualEndCustomerBillingAddress?
let email: String?
let phone: String?
```



### `AnnualEndCustomerBillingAddress`

The object consists of the following fields:

```swift
let address1: String?
let address2: String?
let city: String?
let state: String?
let zip: String?
let country: String?
```



***



## Publics methods in the SDK

### Configuration

These methods allow you to configure the SDK secrets and load the certificate.

```swift
EasyPay.shared.configureSecrets(apiKey: String, hmacSecret: String)
```

```swift
EasyPay.shared.loadCertificate(_ completion: @escaping (Result<Data, Error>) -> Void)
```



### 1. Charge credit card

This method processes a credit card card sale when the credit card details are entered manually. Details include the card number, expiration date, CVV, card holder name and address.

```swift
EasyPay.apiClient.chargeCreditCard(request: CardSaleManualRequest,
                                   completion: @escaping (Result<CreditCardSaleResponse, Error>) -> Void)
```

REST API equivalent: [#apicardprocrest-v1.0.0-cardsale-manual](../../../api-reference/rest-api/card-operations-1/process-a-card-sale.md#apicardprocrest-v1.0.0-cardsale-manual "mention")

#### **Request parameters**

* `TransactionRequest`
  * `creditCardInfo`: [CreditCardInfo](ios-sdk.md#creditcardinfo)
  * `accountHolder`: [AccountHolder](ios-sdk.md#accountholder)
  * `endCustomer`: [EndCustomer](ios-sdk.md#endcustomer)?
  * `amounts`: [Amounts](ios-sdk.md#amounts)
  * `purchItems`: [PurchItems](ios-sdk.md#purchitems)
  * `merchantId`: Int

#### **Response body**

The response will be serialized to `CardSaleManualResponseModel` and include:

```swift
public let avsResult: String
public let acquirerResponseEMV: String?
public let cvvResult: String
public let errorCode: Int
public let errorMessage: String
public let functionOk: Bool
public let isPartialApproval: Bool
public let requiresVoiceAuth: Bool
public let responseMessage: String
public let responseApprovedAmount: Double
public let responseAuthorizedAmount: Double
public let responseBalanceAmount: Double
public let txApproved: Bool
public let txId: Int
public let txnCode: String
```



### 2. List annual consents

A query that returns annual consent details. Depending on the query sent, a single consent or multiple consents may be returned.

```swift
EasyPay.apiClient.listAnnualConsents(request: ConsentAnnualListingRequest,
                                     completion: @escaping (Result<ListingConsentAnnualResponse, Error>) -> Void)
```

REST API equivalent: [#apicardprocrest-v1.0.0-query-consentannual](../../../api-reference/rest-api/query/#apicardprocrest-v1.0.0-query-consentannual "mention")

#### **Request body**

*   `AnnualQueryHelper`

    * `merchantId`: String
    * `customerReferenceId`: String?
    * `rpguid`: String?
    * `endDate`: Date?&#x20;

    Either `customerReferenceId` or `rpguid` must be provided to get the list of consents of a specific customer.

#### **Response body**

The response will be serialized to `ConsentAnnualListingResponseModel` and include:

```swift
public let functionOk: Bool?
public var responseMessage: String?
public let errorMessage: String?
public let errorCode: Int?
public let numberOfRecords: Int?
public let consents: [ConsentAnnual]?
```

And the `ConsentAnnual` consists of the following fields:

```swift
public let id: Int?
public let accountHolderId: Int?
public let customerId: Int?
public let merchantId: Int?
public let customerRefId: String?
public let rpguid: String?
public let serviceDescription: String?
public let accountHolderLastName: String?
public let accountHolderFirstName: String?
public let isEnabled: Bool?
public let startDate: String?
public let endDate: String?
public let numberOfDays: Int?
public let limitPerCharge: Double?
public let limitLifeTime: Double?
public let authTxID: Int?
public let createdOn: String?
public let createdBy: String?
public let accountNumber: String?
```



### 3. Create annual consent

This method creates an annual consent by sending the credit card details, which include: card number, expiration date, CVV, and card holder contact data. It is not created by swiping the card through a reader device.

```swift
EasyPay.apiClient.createAnnualConsent(request: CreateConsentAnnualRequest,
                                      completion: @escaping (Result<CreateConsentAnnualResponse, Error>) -> Void)
```

REST API equivalent: [#apicardprocrest-v1.0.0-consentannual-create\_man](../../../api-reference/rest-api/consent-annual/create-annual-consent.md#apicardprocrest-v1.0.0-consentannual-create_man "mention")

#### **Request body**

* `CreateConsentAnnualManualRequestModel`
  * `creditCardInfo`: [CreditCardInfo](ios-sdk.md#creditcardinfo)
  * `consentAnnualCreate`: [CreateConsentAnnual](ios-sdk.md#createconsentannual)
  * `accountHolder`: [AccountHolder](ios-sdk.md#accountholder)
  * `endCustomer`: [AnnualEndCustomer](ios-sdk.md#annualendcustomer)?

#### **Response body**

The response will be serialized to `CreateConsentAnnualResponseModel` and include:

```swift
public let functionOk: Bool
public let responseMessage: String
public let errorMessage: String
public let errorCode: Int
public let creationSuccess: Bool
public let preConsentAuthSuccess: Bool
public let preConsentAuthMessage: String
public let preConsentAuthTxId: Int
public let consentId: Int
```



### 4. Cancel annual consent

Cancels an annual consent. Credit card data is removed from the system after the cancellation is complete.

```swift
EasyPay.apiClient.cancelAnnualConsent(request: CancelConsentAnnualRequest,
                                      completion: @escaping (Result<CancelConsentAnnualResponse, Error>) -> Void)
```

REST API equivalent: [#apicardprocrest-v1.0.0-consentannual-cancel](../../../api-reference/rest-api/consent-annual/#apicardprocrest-v1.0.0-consentannual-cancel "mention")

#### Request parameters

* `CancelConsentAnnualManualRequestModel`
  * `consentId`: Int

#### **Response body**

The response will be serialized to `CancelConsentAnnualResponseModel` and include:

```swift
public let functionOk: Bool?
public let responseMessage: String?
public let errorMessage: String?
public let errorCode: Int?
public let cancelledConsentId: Int?
public let cancelSuccess: Bool?
```



### 5. Process payment for an annual consent

This method uses the credit card stored on file to process a payment for an existing consent.

```swift
EasyPay.apiClient.processPaymentAnnualConsent(request: ProcessPaymentAnnualRequest,
                                              completion: @escaping (Result<ProcessPaymentAnnualResponse, Error>) -> Void)
```

REST API equivalent: [#apicardprocrest-v1.0.0-consentannual-procpayment](../../../api-reference/rest-api/consent-annual/#apicardprocrest-v1.0.0-consentannual-procpayment "mention")

#### **Request body**

* `ProcessPaymentAnnualRequestModel`
  * `consentId`: Int
  * `processAmount`: String

#### Response body

The response will be serialized to `ProcessPaymentAnnualResponseModel` and include:

```swift
public let functionOk: Bool?
public let txApproved: Bool?
public let responseMessage: String?
public let errorMessage: String?
public let errorCode: Int?
public let txnCode: String?
public let avsResult: String?
public let cvvResult: String?
public let acquirerResponseEMV: String?
public let txId: Int?
public let requiresVoiceAuth: Bool?
public let isPartialApproval: Bool?
public let responseAuthorizedAmount: Double?
public let responseBalanceAmount: Double?
public let responseApprovedAmount: Double?
```



***



## How to properly consume the API response

The response must be consumed in the intended order and format. Clients who deviate from this can experience unwanted behavior.

```swift
if response.data.errorMessage != "" && response.data.errorCode != 0 {
    //This indicates an error which was handled on the Number servers, consume the ErrCode and the ErrMsg 
    return
} else if response.data.functionOk == true && response.data.txApproved == false {
    //This indicates a declined authorization, display the TXID, RspMsg (friendly decline message), also the decline Code (TxnCode)
} else {
   //Transaction has been approved, display the TXID,  and approval code (also in TXNCODE)  
}
```

If there is no `TxApproved` flag, then you can omit the last evaluation. More information about consuming the API response can be found in [Consuming the API response](../basics/api-best-practices.md#consuming-the-api-response) section.



***



## Possible errors

### RsaCertificateError

<table><thead><tr><th width="317">Error name</th><th>Suggested solution</th></tr></thead><tbody><tr><td><code>failedToLoadCertificateData</code></td><td>Check certificate status, wait until the full download before proceeding with calls, try to download it again manually.</td></tr><tr><td><code>failedToCreateCertificate</code></td><td>Contact Number.</td></tr><tr><td><code>failedToExtractPublicKey</code></td><td>Contact Number.</td></tr></tbody></table>



### AuthenticationError

<table><thead><tr><th width="312">Error name</th><th>Suggested solution</th></tr></thead><tbody><tr><td><code>missingSessionKeyOrExpired</code></td><td>Check if you have provided the correct <code>apiKey</code> and <code>hmacSecret</code>, contact Number to receive updated secrets.</td></tr></tbody></table>



### NetworkingError

<table><thead><tr><th width="309">Error name</th><th>Suggested solution</th></tr></thead><tbody><tr><td><code>unsuccesfulRequest</code></td><td>Check HTTP status code.</td></tr><tr><td><code>noDataReceived</code></td><td>Data from backend was empty, contact Number.</td></tr><tr><td><code>dataDecodingFailure</code></td><td>Data from backend was not decoded properly, contact Number.</td></tr><tr><td><code>invalidCertificatePathURL</code></td><td>Contact Number.</td></tr></tbody></table>



***



## Semantic versioning

The SDK follows semantic versioning with a three-part version number: `MAJOR`.`MINOR`.`PATCH`.

* `MAJOR` version is incremented when there are incompatible API changes,
* `MINOR` version is incremented when functionality is added in a backwards-compatible manner,
* `PATCH` version is incremented when there are backwards-compatible bug fixes.



