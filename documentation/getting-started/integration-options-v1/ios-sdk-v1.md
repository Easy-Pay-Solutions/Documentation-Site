---
description: Getting started with iOS SDK for Number
---

# iOS SDK (v1)

{% embed url="https://github.com/Easy-Pay-Solutions/Mobile-SDK-IOS" %}

The EasyPay iOS SDK offers access to the Number API for effortless integration with any iOS application. For Android integration, refer to the [Android SDK integration guide](android-sdk-v2.md).



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
Configure `EasyPay` class. You can do that in your Payment Module or in `AppDelegate` (`didFinishLaunchingWithOptions`). Set `isProduction = true` to enable jailbroken device detection.

```swift
EasyPay.shared.configureSecrets(apiKey: "YOURAPIKEY",
                                hmacSecret: "YOURHMACSECRET",
                                sentryKey: "YOURSENTRYKEY", 
                                isProduction: Bool)
```
{% endstep %}

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



***



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



## Publics methods in the SDK

### Public methods for configuration

```swift
EasyPay.shared.configureSecrets(apiKey: String, hmacSecret: String)
```

```swift
EasyPay.shared.loadCertificate(_ completion: @escaping (Result<Data, Error>) -> Void)
```

### 1. Charge Credit Card (CreditCardSale\_Manual)

This method processes a credit card card sale when the credit card details are entered manually. Details include the card number, expiration date, CVV, card holder name and address.

```swift
EasyPay.apiClient.chargeCreditCard(request: CardSaleManualRequest,
                                   completion: @escaping (Result<CreditCardSaleResponse, Error>) -> Void)
```

#### **Request parameters**

* `TransactionRequest`
  * `creditCardInfo`: CreditCardInfo
  * `accountHolder`: AccountHolder
  * `endCustomer`: EndCustomer?
  * `amounts`: Amounts
  * `purchItems`: PurchItems
  * `merchantId`: Int

#### **Response body**

* `CardSaleManualResponseModel`
  * \[See fields listed in the REST API reference - [Process a manual card sale](../../../api-reference/rest-api-v2/card-operations-v2/process-a-card-sale-v2.md#apicardprocrest-v1.0.0-cardsale-manual)]

### 2. List Annual Consents (ConsentAnnual\_Query)

A query that returns annual consent details. Depending on the query sent, a single consent or multiple consents may be returned.

```swift
EasyPay.apiClient.listAnnualConsents(request: ConsentAnnualListingRequest,
                                     completion: @escaping (Result<ListingConsentAnnualResponse, Error>) -> Void)
```

#### **Request body**

*   `AnnualQueryHelper`

    * `merchantId`: String
    * `customerReferenceId`: String?
    * `rpguid`: String?
    * `endDate`: Date?&#x20;

    Either `customerReferenceId` or `rpguid` must be provided to get the list of consents of a specific customer.

#### **Response body**

* `ConsentAnnualListingResponseModel`
  * \[See fields listed in the REST API reference - [Query annual consent](../../../api-reference/rest-api-v2/query-v2.md#apicardprocrest-v1.0.0-consentannual-queryapr)]

### 3. Create Annual Consent (ConsentAnnual\_Create\_MAN)

This method creates an annual consent by sending the credit card details, which include: card number, expiration date, CVV, and card holder contact data. It is not created by swiping the card through a reader device.

```swift
EasyPay.apiClient.createAnnualConsent(request: CreateConsentAnnualRequest,
                                      completion: @escaping (Result<CreateConsentAnnualResponse, Error>) -> Void)
```

#### **Request body**

* `CreateConsentAnnualManualRequestModel`
  * `creditCardInfo`: CreditCardInfo
  * `consentAnnualCreate`: CreateConsentAnnual
  * `accountHolder`: AccountHolder
  * `endCustomer`: AnnualEndCustomer?

#### **Response body**

* `CreateConsentAnnualResponseModel`
  * \[See fields listed in the REST API reference - [Create an annual consent with manual card entry](../../../api-reference/rest-api-v2/consent-annual-v2/create-consent-v2.md#apicardprocrest-v1.0.0-consentannual-create_man)]

### 4. Cancel Annual Consent (ConsentAnnual\_Cancel)

Cancels an annual consent. Credit card data is removed from the system after the cancellation is complete.

```swift
EasyPay.apiClient.cancelAnnualConsent(request: CancelConsentAnnualRequest,
                                      completion: @escaping (Result<CancelConsentAnnualResponse, Error>) -> Void)
```

#### Request parameters

* `CancelConsentAnnualManualRequestModel`
  * `consentId`: Int

#### **Response body**

* `CancelConsentAnnualResponseModel`
  * \[See fields listed in the REST API reference - [Cancel a consent (Card on file)](../../../api-reference/rest-api-v2/consent-annual-v2/#apicardprocrest-v1.0.0-consentannual-cancel)]

### 5. Process Payment Annual Consent (ConsentAnnual\_ProcPayment)

This method uses the credit card stored on file to process a payment for an existing consent.

```swift
EasyPay.apiClient.processPaymentAnnualConsent(request: ProcessPaymentAnnualRequest,
                                              completion: @escaping (Result<ProcessPaymentAnnualResponse, Error>) -> Void)
```

#### **Request body**

* `ProcessPaymentAnnualRequestModel`
  * `consentId`: Int
  * `processAmount`: String

#### Response body

* `ProcessPaymentAnnualResponseModel`
  * \[See fields listed in the REST API reference - [Process a payment using a stored card consent](../../../api-reference/rest-api-v2/consent-annual-v2/#apicardprocrest-v1.0.0-consentannual-procpayment)]



***



## SecureTextField

The SDK contains a component called `SecureTextField` which ensures a safe input of numbers for credit card details. It is a subclass of `UITextField` which enables freedom of styling as needed.

Setting up requires configuring the certificate once it was downloaded to encrypt credit card data.

```swift
nameOfYourTextField.setupConfig(EasyPay.shared.config)
```

To receive the encrypted card string required to send to the API, you can use the following method:

```swift
nameOfYourTextField.encryptCardData()
```

**This data is already encrypted and can be used in the API calls without any additional encryption.**



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

If there is no `TxApproved` flag, then you can omit the last evaluation. More information about consuming the API response can be found in [Consuming the API response](../basics-v1/api-best-practices-v2.md#consuming-the-api-response) section.



***



## Possible Errors

### RsaCertificateError

| Error name                    |                                                    Suggested solution                                                   |
| ----------------------------- | :---------------------------------------------------------------------------------------------------------------------: |
| `failedToLoadCertificateData` | Check certificate status, wait until the full download before proceeding with calls, try to download it again manually. |
| `failedToCreateCertificate`   |                                                     Contact Number.                                                     |
| `failedToExtractPublicKey`    |                                                     Contact Number.                                                     |

### AuthenticationError

| Error name                   |                                              Suggested solution                                              |
| ---------------------------- | :----------------------------------------------------------------------------------------------------------: |
| `missingSessionKeyOrExpired` | Check if you have provided the correct `apiKey` and `hmacSecret`, contact Number to receive updated secrets. |

### NetworkingError

| Error name                  |                      Suggested solution                     |
| --------------------------- | :---------------------------------------------------------: |
| `unsuccesfulRequest`        |                   Check HTTP status code.                   |
| `noDataReceived`            |         Data from backend was empty, contact Number.        |
| `dataDecodingFailure`       | Data from backend was not decoded properly, contact Number. |
| `invalidCertificatePathURL` |                       Contact Number.                       |



***



## Semantic Versioning

The SDK follows semantic versioning with a three-part version number: `MAJOR`.`MINOR`.`PATCH`.

* `MAJOR` version is incremented when there are incompatible API changes,
* `MINOR` version is incremented when functionality is added in a backwards-compatible manner,
* `PATCH` version is incremented when there are backwards-compatible bug fixes.



