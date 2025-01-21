---
description: Getting started with Android SDK for Number
---

# Android SDK (v2)

{% embed url="https://github.com/Easy-Pay-Solutions/Mobile-SDK-Android" %}

The EasyPay Android SDK offers access to the Number API for seamless integration with any and all Android applications. For iOS integration, refer to the [iOS SDK integration guide](ios-sdk-v1.md).



***



## Installation

### Requirements

* Android 6.0 (API level 23) and above
* Gradle 8.2 and above
* Android Gradle Plugin 8.2.1
* Kotlin 1.9.22 and above

### Configuration

Add `easypay` to your dependencies in the `build.gradle` file.

```gradle
dependencies {
    implementation 'com.easypaysolutions:easypay:1.1.5'
    
    // If you want to use widgets, add the following line
    implementation 'com.easypaysolutions:easypay-widgets:1.1.5'
}
```



***



## Get started

### Integration

{% stepper %}
{% step %}
Prerequisites - get API key, HMAC secret and optional Sentry DSN from Number.
{% endstep %}

{% step %}
Configure the `EasyPay` class at the very beginning of the application lifecycle, e.g. in the main Application class (in the `onCreate()` method).

```kotlin
class MainApplication : Application() {
    override fun onCreate() {
        super.onCreate()
        EasyPay.init(applicationContext, "YOUR_API_KEY", "YOUR_HMAC_SECRET", "SENTRY_DSN")
    }
}
```
{% endstep %}

{% step %}
During initialization, the RSA certificate download begins. Proceeding with any call before downloading has finished will result with an exception `RSA_CERTIFICATE_NOT_FETCHED`.&#x20;

You can check the download status by accessing the following enum:

```kotlin
EasyPayConfiguration.getInstance().getRsaCertificateFetchingStatus()
```
{% endstep %}
{% endstepper %}



### Using widgets

#### **PaymentSheet**

Number's prebuilt payment UI component that allows you to collect credit card information in a secure way and process payments.

{% stepper %}
{% step %}
Initialize a `PaymentSheet` inside `onCreate` of your checkout `Fragment` or `Activity`, passing a method to handle the payment result.

<pre class="language-kotlin"><code class="lang-kotlin"><strong>import com.easypaysolutions.payment_sheet.PaymentSheet
</strong>import com.easypaysolutions.payment_sheet.utils.PaymentSheetResult

class PaymentSheetFragment : Fragment() {
    private lateinit var paymentSheet: PaymentSheet

    override fun onCreate(savedInstanceState: Bundle?) {
        super.onCreate(savedInstanceState)
        paymentSheet = PaymentSheet(this, ::onPaymentSheetResult)
    }
    
    private fun onPaymentSheetResult(paymentSheetResult: PaymentSheetResult) {
        // implemented in the next steps
    }
}
</code></pre>
{% endstep %}

{% step %}
When the customer taps the payment button, call `present` method on the `PaymentSheet` instance with your configuration. `PaymentSheet.Configuration` requires the following parameters:

* `AmountsParam` - total $ amount of the payment;
* `ConsentCreatorParam` - annual consent details, that contains the following:
  * `limitLifeTime` - the maximum $ amount that can be charged in total,
  * `limitPerCharge` - the maximum $ amount that can be charged per transaction,
  * `merchantId` - the ID of the merchant that the consent is created for,
  * `startDate` - the date when the consent is created,
  * `customerReferenceId` or `consentId` to identify the customer.&#x20;

**Other parameters are optional.**

```kotlin
// ...
import com.easypaysolutions.repositories.annual_consent.create.ConsentCreatorParam
import com.easypaysolutions.repositories.charge_cc.AmountsParam

class PaymentSheetFragment : Fragment() {
    // ...
    
    private fun presentPaymentSheet() {
        val totalAmount: Double = 1000.0
        val consentCreator = ConsentCreatorParam(
            limitLifeTime = 100000.0,
            limitPerCharge = 1000.0,
            merchantId = 1,
            startDate = Date(),
            customerReferenceId = "CUSTOMER_REFERENCE_ID"
        )
    
        val config = PaymentSheet.Configuration
            .Builder()
            .setAmounts(AmountsParam(totalAmount))
            .setConsentCreator(consentCreator)
            .build()
            
        paymentSheet.present(config)
    }
}
```
{% endstep %}

{% step %}
Handle the payment result in the `onPaymentSheetResult` method.

```kotlin
// ...
class PaymentSheetFragment : Fragment() {
    // ...
    
    private fun onPaymentSheetResult(paymentSheetResult: PaymentSheetResult) {
        when (paymentSheetResult) {
            is PaymentSheetResult.Failed -> {
                // Handle failure
            }
    
            is PaymentSheetResult.Completed -> {
                // Handle successful payment
            }
    
            is PaymentSheetResult.Canceled -> {
                // Handle cancellation
            }
        }
    }
}
```
{% endstep %}
{% endstepper %}

#### **CustomerSheet**

Number's prebuilt UI component that lets your customers manage their saved credit cards.

{% stepper %}
{% step %}
Initialize a `CustomerSheet` inside `onCreate` of your checkout `Fragment` or `Activity`, passing a method to handle the customer sheet result.

```kotlin
import com.easypaysolutions.customer_sheet.CustomerSheet
import com.easypaysolutions.customer_sheet.utils.CustomerSheetResult

class CustomerSheetFragment : Fragment() {
    private lateinit var customerSheet: CustomerSheet

    override fun onCreate(savedInstanceState: Bundle?) {
        super.onCreate(savedInstanceState)
        customerSheet = CustomerSheet(this, ::onCustomerSheetResult)
    }
    
    private fun onCustomerSheetResult(customerSheetResult: CustomerSheetResult) {
        // implemented in the next steps
    }
}
```
{% endstep %}

{% step %}
To present the customer sheet, call the `present` method on the `CustomerSheet` instance, passing your configuration. `CustomerSheet.Configuration` requires the following parameters:

* `ConsentCreatorParam` - annual consent details, that contains the following:
  * `limitLifeTime` - the maximum $ amount that can be charged in total,
  * `limitPerCharge` - the maximum $ amount that can be charged per transaction,
  * `merchantId` - the ID of the merchant that the consent is created for,
  * `startDate` - the date when the consent is created,
  * `customerReferenceId` or `consentId` to identify the customer.&#x20;

**Other parameters are optional.**

```kotlin
// ...
import com.easypaysolutions.repositories.annual_consent.create.ConsentCreatorParam

class CustomerSheetFragment : Fragment() {
    // ...
    
    private fun presentCustomerSheet() {
        val consentCreator = ConsentCreatorParam(
            limitLifeTime = 100000.0,
            limitPerCharge = 1000.0,
            merchantId = 1,
            startDate = Date(),
            customerReferenceId = "CUSTOMER_REFERENCE_ID"
        )
    
        val config = CustomerSheet.Configuration
            .Builder()
             .setConsentCreator(consentCreator)
            .build()
            
        customerSheet.present(config)
    }
}
```
{% endstep %}

{% step %}
Handle the customer sheet result in the `onCustomerSheetResult` method.

```kotlin
// ...
class CustomerSheetFragment : Fragment() {
    // ...
    
    private fun onCustomerSheetResult(customerSheetResult: CustomerSheetResult) {
        when (customerSheetResult) {
            is CustomerSheetResult.Failed -> {
                // Handle failure
            }

            is CustomerSheetResult.Selected -> {
                // Handle selected card - customerSheetResult.annualConsentId
            }
        }
    }
}
```
{% endstep %}
{% endstepper %}



***



## Screenshots

#### **Save Card**

<figure><img src="../../../.gitbook/assets/Save card - mobile.png" alt=""><figcaption></figcaption></figure>

<figure><img src="../../../.gitbook/assets/Save card - Tablet.png" alt=""><figcaption></figcaption></figure>

#### **Manage Cards**

<figure><img src="../../../.gitbook/assets/Manage Cards - mobile.png" alt=""><figcaption></figcaption></figure>

#### **Store and Pay**

<figure><img src="../../../.gitbook/assets/Store and Pay.png" alt=""><figcaption></figcaption></figure>



***



## Public methods in the Android SDK

### 1. Charge Credit Card (CreditCardSale\_Manual)

This method processes a credit card when the credit card details are entered manually. Details include the card number, expiration date, CVV, card holder name and address.

```kotlin
ChargeCreditCard().chargeCreditCard(params: ChargeCreditCardBodyParams): NetworkResource<ChargeCreditCardResult>
```

#### **Request parameters**

* `ChargeCreditCardBodyParams`
  * `encryptedCardNumber`: SecureData
  * `creditCardInfo`: CreditCardInfoParam
  * `accountHolder`: AccountHolderDataParam
  * `endCustomer`: EndCustomerDataParam?
  * `amounts`: AmountsParam
  * `purchaseItems`: PurchaseItemsParam
  * `merchantId`: Int

#### **Response body**

* `ChargeCreditCardResult`
  * \[See fields listed in the REST API reference - [Process a manual card sale](../../../api-reference/rest-api-v3/query-v2.md#apicardprocrest-v1.0.0-query-consentannual)]



### 2. List Annual Consents (ConsentAnnual\_Query)

A query that returns annual consent details. Depending on the query sent, a single consent or multiple consents may be returned.

```kotlin
ListAnnualConsents().listAnnualConsents(params: ListAnnualConsentsBodyParams): NetworkResource<ListAnnualConsentsResult>
```

#### **Request parameters**

*   `ListAnnualConsentsBodyParams`

    * `merchantId`: Int?
    * `customerReferenceId`: String?
    * `rpguid`: String?&#x20;

    Either `customerReferenceId` or `rpguid` must be provided to get the list of consents of a specific customer.

#### **Response body**

* `ListAnnualConsentsResult`
  * \[See fields listed in the REST API reference - [Query annual consent](../../../api-reference/rest-api-v3/query-v2.md#apicardprocrest-v1.0.0-query-consentannual_fulldetail)]



### 3. Create Annual Consent (ConsentAnnual\_Create\_MAN)

This method creates an annual consent by sending the credit card details, which include: card number, expiration date, CVV, and card holder contact data. It is **not** created by swiping the card through a reader device.

```kotlin
CreateAnnualConsent().createAnnualConsent(params: CreateAnnualConsentBodyParams): NetworkResource<CreateAnnualConsentResult>
```

#### **Request parameters**

* `CreateAnnualConsentBodyParams`
  * `encryptedCardNumber`: SecureData
  * `creditCardInfo`: CreditCardInfoParam
  * `accountHolder`: AccountHolderDataParam
  * `endCustomer`: EndCustomerDataParam?
  * `consentCreator`: ConsentCreatorParam

#### **Response body**

* `CreateAnnualConsentResult`
  * \[See fields listed in the REST API reference - [Create an annual consent with manual card entry](../../../api-reference/rest-api-v3/consent-annual-v2/create-consent-v2.md#apicardprocrest-v1.0.0-consentannual-create_man)]



### 4. Cancel Annual Consent (ConsentAnnual\_Cancel)

Cancels an annual consent. Credit card data is removed from the system after the cancellation is complete.

```kotlin
CancelAnnualConsent().cancelAnnualConsent(params: CancelAnnualConsentBodyParams): NetworkResource<CancelAnnualConsentResult>
```

#### **Request parameters**

* `CancelAnnualConsentBodyParams`
  * `consentId`: Int

#### **Response body**

* `CancelAnnualConsentResult`
  * \[See fields listed in the REST API reference - [Cancel a consent (Card on file)](../../../api-reference/rest-api-v3/consent-annual-v2/#apicardprocrest-v1.0.0-consentannual-cancel)]



### 5. Process Payment Annual Consent (ConsentAnnual\_ProcPayment)

This method uses the credit card stored on file to process a payment for an existing consent.

```kotlin
ProcessPaymentAnnual().processPaymentAnnual(params: ProcessPaymentAnnualBodyParams): NetworkResource<ProcessPaymentAnnualResult>
```

#### **Request parameters**

* `ProcessPaymentAnnualBodyParams`
  * `consentId`: Int

#### **Response body**

* `ProcessPaymentAnnualResult`
  * \[See fields listed in the REST API reference - [Process a payment using a stored card consent](../../../api-reference/rest-api-v3/consent-annual-v2/#apicardprocrest-v1.0.0-consentannual-procpayment)]



***



## SecureTextField

The SDK contains a component called `SecureTextField` which ensures a safe input of number of numbers for credit card. It is a subclass of `TextInputEditText` which enables freedom of styling as needed.

`SecureTextField` supports only XML layout configuration:

```xml
<com.easypaysolutions.utils.secured.SecureTextField
    ... />
```

To get the `SecureData` from the `SecureTextField`, use the following property:

```kotlin
val secureData = secureTextField.secureData
```

**This data is already encrypted and can be used in the API calls without any additional encryption.**



***



## How to properly consume the API response

All requests are suspended functions, so they should be called from coroutine scope. The result of the request is wrapped in a `NetworkResource` object, which can be handled in the following way:

```kotlin
viewModelScope.launch {
    // Example of suspended function call
    val result = ChargeCreditCard().chargeCreditCard(params)
    when (result) {
        is NetworkResource.Status.SUCCESS -> {
            // Handle success
        }
        is NetworkResource.Status.ERROR -> {
            // Handle error
        }
        is NetworkResource.Status.DECLINED -> {
            // Handle declined
        }
    }
}
```



***



## Possible Exceptions

### EasyPaySdkException

Exceptions that are thrown by the SDK.

<table><thead><tr><th width="342">Exception name</th><th>Suggested solution</th></tr></thead><tbody><tr><td><code>EASY_PAY_CONFIGURATION_NOT_INITIALIZED</code></td><td>Check if <code>EasyPay.init(...)</code> method has been called.</td></tr><tr><td><code>MISSED_SESSION_KEY</code></td><td>Check if correct <code>SESSION_KEY</code> has been provided in the <code>EasyPay.init(...)</code> method.</td></tr><tr><td><code>MISSED_HMAC_SECRET</code></td><td>Check if correct <code>HMAC_SECRET</code> has been provided in the <code>EasyPay.init(...)</code> method.</td></tr><tr><td><code>RSA_CERTIFICATE_NOT_FETCHED</code></td><td>RSA certificate might not be fetched yet. Check the status by calling the <code>EasyPayConfiguration.getInstance().getRsaCertificateFetchingStatus()</code> method.</td></tr><tr><td><code>RSA_CERTIFICATE_FETCH_FAILED</code></td><td>Contact Number.</td></tr><tr><td><code>RSA_CERTIFICATE_PARSING_ERROR</code></td><td>Contact Number.</td></tr></tbody></table>

### EasyPayApiException

Exceptions that are thrown by the Number API.



***



## Semantic Versioning

The SDK follows semantic versioning with a three-part version number: `MAJOR`.`MINOR`.`PATCH`.

* `MAJOR` version is incremented when there are incompatible API changes,
* `MINOR` version is incremented when functionality is added in a backwards-compatible manner,
* `PATCH` version is incremented when there are backwards-compatible bug fixes.



***



## Feature flags

### Rooted device detection

To enable rooted device detection, call the following method before calling `EasyPay.init(...)`:

```kotlin
EasyPayFeatureFlagManager.setRootedDeviceDetectionEnabled(true)
```





