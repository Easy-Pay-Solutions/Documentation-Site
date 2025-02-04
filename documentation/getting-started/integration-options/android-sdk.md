---
description: Getting started with Android SDK for Number
---

# Android SDK

{% include "../../../.gitbook/includes/link-android-sdk.md" %}

The EasyPay Android SDK offers access to the Number API for seamless integration with any and all Android applications. For iOS integration, refer to the [iOS SDK integration guide](ios-sdk.md).



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
{% include "../../../.gitbook/includes/block-android-config-ep.md" %}
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



### Screenshots

#### **Save Card**

<figure><img src="../../../.gitbook/assets/Save card - mobile.png" alt=""><figcaption></figcaption></figure>

<figure><img src="../../../.gitbook/assets/Save card - Tablet.png" alt=""><figcaption></figcaption></figure>

#### **Manage Cards**

<figure><img src="../../../.gitbook/assets/Manage Cards - mobile.png" alt=""><figcaption></figcaption></figure>

#### **Store and Pay**

<figure><img src="../../../.gitbook/assets/Store and Pay.png" alt=""><figcaption></figcaption></figure>



***



## Common components

### SecureTextField component

The SDK's widgets use a component called `SecureTextField` which ensures a safe input of credit card number. It is a subclass of `TextInputEditText` which enables freedom of styling as needed.

`SecureTextField` supports only XML layout configuration:

```xml
<com.easypaysolutions.utils.secured.SecureTextField
    ... />
```

To get the `SecureData` from the `SecureTextField`, use the following property:

```kotlin
val secureData = secureTextField.secureData
```

{% hint style="info" %}
Data in the SecureTextField component is already encrypted and can be used in the API calls without any additional encryption.
{% endhint %}



***



## Common objects

Below you'll find code describing some of the objects that are commonly used in requests or responses. You can use it as a reference. The code includes parameter names, types, and some validation rules.



### `SecureData`

Most commonly used as `SecureData<String>` coming from the [#securetextfield-component](android-sdk.md#securetextfield-component "mention").

```kotlin
data class SecureData<T> internal constructor(
    val data: T,
)
```



### `CreditCardInfoParam`

```kotlin
data class CreditCardInfoParam(
    @ValidateNumberGreaterThanZero
    @ValidateLength(maxLength = 2)
    val expMonth: Int,

    @ValidateNumberGreaterThanZero
    @ValidateLength(maxLength = 4)
    val expYear: Int,

    @ValidateLength(maxLength = 4)
    @ValidateNotBlank
    val csv: String,
)
```



### `AccountHolderDataParam`

```kotlin
data class AccountHolderDataParam(
    @ValidateLength(maxLength = 75)
    @ValidateRegex(regex = FIRST_OR_LAST_NAME)
    val firstName: String? = null,

    @ValidateLength(maxLength = 75)
    @ValidateRegex(regex = FIRST_OR_LAST_NAME)
    val lastName: String? = null,

    @ValidateLength(maxLength = 100)
    @ValidateRegex(regex = COMPANY)
    val company: String? = null,

    val billingAddress: AccountHolderBillingAddressParam,

    @ValidateLength(maxLength = 150)
    @ValidateRegex(regex = EMAIL)
    val email: String? = null,

    @ValidateLength(maxLength = 16)
    @ValidateRegex(regex = ONLY_NUMBERS)
    val phone: String? = null,
)
```



### `AccountHolderBillingAddressParam`

```kotlin
data class AccountHolderBillingAddressParam(
    @ValidateLength(maxLength = 100)
    @ValidateRegex(regex = ADDRESS1)
    @ValidateNotBlank
    val address1: String,

    @ValidateLength(maxLength = 100)
    @ValidateRegex(regex = ADDRESS2)
    val address2: String? = null,

    @ValidateLength(maxLength = 75)
    @ValidateRegex(regex = CITY)
    val city: String? = null,

    @ValidateLength(maxLength = 75)
    @ValidateRegex(regex = COUNTRY_OR_STATE)
    val state: String? = null,

    @ValidateLength(maxLength = 20)
    @ValidateRegex(regex = ZIP_CODE)
    @ValidateNotBlank
    val zip: String,

    @ValidateLength(maxLength = 75)
    @ValidateRegex(regex = COUNTRY_OR_STATE)
    val country: String? = null,
)
```



### `EndCustomerDataParam`

```kotlin
data class EndCustomerDataParam(
    @ValidateLength(maxLength = 75)
    @ValidateRegex(regex = FIRST_OR_LAST_NAME)
    val firstName: String? = null,

    @ValidateLength(maxLength = 75)
    @ValidateRegex(regex = FIRST_OR_LAST_NAME)
    val lastName: String? = null,

    @ValidateLength(maxLength = 100)
    @ValidateRegex(regex = COMPANY)
    val company: String? = null,

    val billingAddress: EndCustomerBillingAddressParam,

    @ValidateLength(maxLength = 150)
    @ValidateRegex(regex = EMAIL)
    val email: String? = null,

    @ValidateLength(maxLength = 16)
    @ValidateRegex(regex = ONLY_NUMBERS)
    val phone: String? = null,
)
```



### EndCustomerBillingAddressParam

```kotlin
data class EndCustomerBillingAddressParam(
    @ValidateLength(maxLength = 100)
    @ValidateRegex(regex = ADDRESS1)
    val address1: String,

    @ValidateLength(maxLength = 100)
    @ValidateRegex(regex = ADDRESS2)
    val address2: String? = null,

    @ValidateLength(maxLength = 75)
    @ValidateRegex(regex = CITY)
    val city: String? = null,

    @ValidateLength(maxLength = 75)
    @ValidateRegex(regex = COUNTRY_OR_STATE)
    val state: String? = null,

    @ValidateLength(maxLength = 20)
    @ValidateRegex(regex = ZIP_CODE)
    val zip: String,

    @ValidateLength(maxLength = 75)
    @ValidateRegex(regex = COUNTRY_OR_STATE)
    val country: String? = null,
)
```



### `AmountsParam`

```kotlin
data class AmountsParam(
    @ValidateNumberGreaterThanZero
    val totalAmount: Double,
    val salesTax: Double? = null,
    val surcharge: Double? = null,
)
```



### PurchaseItemsParam

```kotlin
data class PurchaseItemsParam(
    @ValidateLength(maxLength = 200)
    @ValidateRegex(regex = SERVICE_DESCRIPTION)
    val serviceDescription: String? = null,

    @ValidateLength(maxLength = 75)
    @ValidateRegex(regex = CLIENT_REF_ID_OR_RPGUID)
    val clientRefId: String? = null,

    @ValidateLength(maxLength = 75)
    @ValidateRegex(regex = CLIENT_REF_ID_OR_RPGUID)
    val rpguid: String? = null,
)
```



### `ConsentCreatorParam`

```kotlin
data class ConsentCreatorParam(
    val merchantId: Int,

    @ValidateLength(maxLength = 200)
    @ValidateRegex(regex = RegexPattern.SERVICE_DESCRIPTION)
    val serviceDescription: String? = null,

    @ValidateLength(maxLength = 75)
    @ValidateRegex(regex = RegexPattern.CLIENT_REF_ID_OR_RPGUID)
    val customerReferenceId: String? = null,

    @ValidateLength(maxLength = 75)
    @ValidateRegex(regex = RegexPattern.CLIENT_REF_ID_OR_RPGUID)
    val rpguid: String? = null,
    val startDate: Date,

    @ValidateNumberGreaterThanZero
    val limitPerCharge: Double,

    @ValidateNumberGreaterThanZero
    val limitLifeTime: Double,
)
```



***



## Public methods in the Android SDK

### 1. Charge credit card

This method processes a credit card when the credit card details are entered manually. Details include the card number, expiration date, CVV, card holder name and address.

```kotlin
ChargeCreditCard().chargeCreditCard(params: ChargeCreditCardBodyParams): NetworkResource<ChargeCreditCardResult>
```

REST API equivalent: [#apicardprocrest-v1.0.0-cardsale-manual](../../../api-reference/rest-api/card-operations/process-a-card-sale.md#apicardprocrest-v1.0.0-cardsale-manual "mention")

#### **Request parameters**

* `ChargeCreditCardBodyParams`
  * `encryptedCardNumber`: [SecureData](android-sdk.md#securedata)\<String>
  * `creditCardInfo`: [CreditCardInfoParam](android-sdk.md#creditcardinfoparam)
  * `accountHolder`: [AccountHolderDataParam](android-sdk.md#accountholderdataparam)
  * `endCustomer`: [EndCustomerDataParam](android-sdk.md#endcustomerdataparam)?
  * `amounts`: [AmountsParam](android-sdk.md#amountsparam)
  * `purchaseItems`: [PurchaseItemsParam](android-sdk.md#purchaseitemsparam)
  * `merchantId`: Int

#### **Response body**

The response body will be serialized to `ChargeCreditCardResult`.

```kotlin
data class ChargeCreditCardResult internal constructor(
    @SerializedName("FunctionOk")
    override val functionOk: Boolean,

    @SerializedName("ErrCode")
    override val errorCode: Int,

    @SerializedName("ErrMsg")
    override val errorMessage: String,

    @SerializedName("RespMsg")
    override val responseMessage: String,

    @SerializedName("TxApproved")
    override val txApproved: Boolean,

    @SerializedName("TxID")
    override val txId: Int,

    @SerializedName("TxnCode")
    override val txCode: String,

    @SerializedName("AVSresult")
    val avsResult: String,

    @SerializedName("AcquirerResponseEMV")
    val acquirerResponseEmv: String?,

    @SerializedName("CVVresult")
    val cvvResult: String,

    @SerializedName("IsPartialApproval")
    val isPartialApproval: Boolean,

    @SerializedName("RequiresVoiceAuth")
    val requiresVoiceAuth: Boolean,

    @SerializedName("ResponseApprovedAmount")
    val responseApprovedAmount: Double,

    @SerializedName("ResponseAuthorizedAmount")
    val responseAuthorizedAmount: Double,

    @SerializedName("ResponseBalanceAmount")
    val responseBalanceAmount: Double,
)
```



### 2. List annual consents

A query that returns annual consent details. Depending on the query sent, a single consent or multiple consents may be returned.

```kotlin
ListAnnualConsents().listAnnualConsents(params: ListAnnualConsentsBodyParams): NetworkResource<ListAnnualConsentsResult>
```

REST API equivalent: [#apicardprocrest-v1.0.0-query-consentannual](../../../api-reference/rest-api/query.md#apicardprocrest-v1.0.0-query-consentannual "mention")

#### **Request parameters**

*   `ListAnnualConsentsBodyParams`

    * `merchantId`: Int?
    * `customerReferenceId`: String?
    * `rpguid`: String?&#x20;

    Either `customerReferenceId` or `rpguid` must be provided to get the list of consents of a specific customer.

#### **Response body**

The response body will be serialized to `ListAnnualConsentsResult`.

```kotlin
data class ListAnnualConsentsResult internal constructor(
    @SerializedName("FunctionOk")
    override val functionOk: Boolean,

    @SerializedName("ErrCode")
    override val errorCode: Int,

    @SerializedName("ErrMsg")
    override val errorMessage: String,

    @SerializedName("RespMsg")
    override val responseMessage: String,

    @SerializedName("NumRecords")
    val numRecords: Int,

    @SerializedName("Consents")
    val consents: List<AnnualConsent>,
)
```

And the `AnnualConsent` looks like the following:

```kotlin
data class AnnualConsent internal constructor(
    @SerializedName("AcctHolderFirstName")
    val accountHolderFirstName: String,

    @SerializedName("AcctHolderID")
    val accountHolderId: Int,

    @SerializedName("AcctHolderLastName")
    val accountHolderLastName: String,

    @SerializedName("AcctNo")
    val accountNumber: String,

    @SerializedName("AuthTxID")
    val authTxId: Int,

    @SerializedName("CreatedBy")
    val createdBy: String,

    @SerializedName("CreatedOn")
    var createdOn: String,

    @SerializedName("CustID")
    val customerId: Int,

    @SerializedName("CustomerRefID")
    val customerReferenceId: String,

    @SerializedName("EndDate")
    var endDate: String,

    @SerializedName("ID")
    val id: Int,

    @SerializedName("IsEnabled")
    val isEnabled: Boolean,

    @SerializedName("LimitLifeTime")
    val limitLifeTime: Double,

    @SerializedName("LimitPerCharge")
    val limitPerCharge: Double,

    @SerializedName("MerchID")
    val merchId: Int,

    @SerializedName("NumDays")
    val numDays: Int,

    @SerializedName("RPGUID")
    val rpguid: String,

    @SerializedName("ServiceDescrip")
    val serviceDescription: String,

    @SerializedName("StartDate")
    var startDate: String,
)
```



### 3. Create annual consent

This method creates an annual consent by sending the credit card details, which include: card number, expiration date, CVV, and card holder contact data. It is **not** created by swiping the card through a reader device.

```kotlin
CreateAnnualConsent().createAnnualConsent(params: CreateAnnualConsentBodyParams): NetworkResource<CreateAnnualConsentResult>
```

REST API equivalent: [#apicardprocrest-v1.0.0-consentannual-create\_man](../../../api-reference/rest-api/consent-annual/create-annual-consent.md#apicardprocrest-v1.0.0-consentannual-create_man "mention")

#### **Request parameters**

* `CreateAnnualConsentBodyParams`
  * `encryptedCardNumber`: [SecureData](android-sdk.md#securedata)\<String>
  * `creditCardInfo`: [CreditCardInfoParam](android-sdk.md#creditcardinfoparam)
  * `accountHolder`: [AccountHolderDataParam](android-sdk.md#accountholderdataparam)
  * `endCustomer`: [EndCustomerDataParam](android-sdk.md#endcustomerdataparam)?
  * `consentCreator`: [ConsentCreatorParam](android-sdk.md#consentcreatorparam)

#### **Response body**

The response body will be serialized to `CreateAnnualConsentResult`.

```kotlin
data class CreateAnnualConsentResult internal constructor(
    @SerializedName("FunctionOk")
    override val functionOk: Boolean,

    @SerializedName("ErrCode")
    override val errorCode: Int,

    @SerializedName("ErrMsg")
    override val errorMessage: String,

    @SerializedName("RespMsg")
    override val responseMessage: String,

    @SerializedName("ConsentID")
    val consentId: Int,

    @SerializedName("CreationSuccess")
    val creationSuccess: Boolean,

    @SerializedName("PreConsentAuthMessage")
    val preConsentAuthMessage: String,

    @SerializedName("PreConsentAuthSuccess")
    val preConsentAuthSuccess: Boolean,

    @SerializedName("PreConsentAuthTxID")
    val preConsentAuthTxId: Int,
)
```



### 4. Cancel annual consent

Cancels an annual consent. Credit card data is removed from the system after the cancellation is complete.

```kotlin
CancelAnnualConsent().cancelAnnualConsent(params: CancelAnnualConsentBodyParams): NetworkResource<CancelAnnualConsentResult>
```

REST API equivalent: [#apicardprocrest-v1.0.0-consentannual-cancel](../../../api-reference/rest-api/consent-annual/#apicardprocrest-v1.0.0-consentannual-cancel "mention")

#### **Request parameters**

* `CancelAnnualConsentBodyParams`
  * `consentId`: Int

#### **Response body**

The response body will be serialized to `CancelAnnualConsentResult`.

```kotlin
data class CancelAnnualConsentResult internal constructor(
    @SerializedName("FunctionOk")
    override val functionOk: Boolean,

    @SerializedName("ErrCode")
    override val errorCode: Int,

    @SerializedName("ErrMsg")
    override val errorMessage: String,

    @SerializedName("RespMsg")
    override val responseMessage: String,

    @SerializedName("CancelSuccess")
    val cancelSuccess: Boolean,

    @SerializedName("CancelledConsentID")
    val cancelledConsentId: Int,
)
```



### 5. Process payment for an annual consent

This method uses the credit card stored on file to process a payment for an existing consent.

```kotlin
ProcessPaymentAnnual().processPaymentAnnual(params: ProcessPaymentAnnualBodyParams): NetworkResource<ProcessPaymentAnnualResult>
```

REST API equivalent: [#apicardprocrest-v1.0.0-consentannual-procpayment](../../../api-reference/rest-api/consent-annual/#apicardprocrest-v1.0.0-consentannual-procpayment "mention")

#### **Request parameters**

* `ProcessPaymentAnnualBodyParams`
  * `consentId`: Int

#### **Response body**

The response body will be serialized to `ProcessPaymentAnnualResult`.

```kotlin
data class ProcessPaymentAnnualResult internal constructor(
    @SerializedName("FunctionOk")
    override val functionOk: Boolean,

    @SerializedName("ErrCode")
    override val errorCode: Int,

    @SerializedName("ErrMsg")
    override val errorMessage: String,

    @SerializedName("RespMsg")
    override val responseMessage: String,

    @SerializedName("TxApproved")
    override val txApproved: Boolean,

    @SerializedName("TxID")
    override val txId: Int,

    @SerializedName("TxnCode")
    override val txCode: String,

    @SerializedName("AVSresult")
    val avsResult: String,

    @SerializedName("AcquirerResponseEMV")
    val acquirerResponseEmv: String?,

    @SerializedName("CVVresult")
    val cvvResult: String,

    @SerializedName("IsPartialApproval")
    val isPartialApproval: Boolean,

    @SerializedName("RequiresVoiceAuth")
    val requiresVoiceAuth: Boolean,

    @SerializedName("ResponseApprovedAmount")
    val responseApprovedAmount: Double,

    @SerializedName("ResponseAuthorizedAmount")
    val responseAuthorizedAmount: Double,

    @SerializedName("ResponseBalanceAmount")
    val responseBalanceAmount: Double,
)
```



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



## Possible exceptions

### EasyPaySdkException

Exceptions that are thrown by the SDK.

<table><thead><tr><th width="342">Exception name</th><th>Suggested solution</th></tr></thead><tbody><tr><td><code>EASY_PAY_CONFIGURATION_NOT_INITIALIZED</code></td><td>Check if <code>EasyPay.init(...)</code> method has been called.</td></tr><tr><td><code>MISSED_SESSION_KEY</code></td><td>Check if correct <code>SESSION_KEY</code> has been provided in the <code>EasyPay.init(...)</code> method.</td></tr><tr><td><code>MISSED_HMAC_SECRET</code></td><td>Check if correct <code>HMAC_SECRET</code> has been provided in the <code>EasyPay.init(...)</code> method.</td></tr><tr><td><code>RSA_CERTIFICATE_NOT_FETCHED</code></td><td>RSA certificate might not be fetched yet. Check the status by calling the <code>EasyPayConfiguration.getInstance().getRsaCertificateFetchingStatus()</code> method.</td></tr><tr><td><code>RSA_CERTIFICATE_FETCH_FAILED</code></td><td>Contact Number.</td></tr><tr><td><code>RSA_CERTIFICATE_PARSING_ERROR</code></td><td>Contact Number.</td></tr></tbody></table>



### EasyPayApiException

Exceptions that are thrown by the Number API.



***



## Semantic versioning

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



