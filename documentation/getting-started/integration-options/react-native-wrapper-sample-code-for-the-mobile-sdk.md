---
layout:
  title:
    visible: true
  description:
    visible: false
  tableOfContents:
    visible: true
  outline:
    visible: true
  pagination:
    visible: true
---

# React Native Wrapper Sample Code for the Mobile SDK

{% embed url="https://github.com/Easy-Pay-Solutions/Mobile-SDK-ReactNative" %}
React Native Samples
{% endembed %}

The React Native Mobile SDK Wrapper provides a bridge between a React Native based application and the native Number Mobile SDK libraries. Number's [Android](android-sdk.md) and [iOS](ios-sdk.md) SDK libraries are required for use of these samples. It is highly recommended that you review the core SDK products before proceeding.

### Requirements

1. Mac OS based workstation v15 or newer
2. Xcode v16.2 or newer
3. Android Studio Ladybug Feature Drop | 2024.2.2 or newer
4. React Native CLI
5. React Native v0.77 without new architecture enabled
6. Node v18.19.0 or newer
7. npm v10.8.2 or newer

### Prerequisites

Before beginning your implementation you will need an Easy Pay account. Your account will include the following items:

1. Session Key: this authenticates you to a particular account.
2. HMAC secret: used to create a hash which proves your request is authentic.
3. RSA Certificate: to encrypt the credit card number prior to transmission.
4. A sentry.io key for logging events and errors.
5. Merchant Record or Merchant ID: Each Easy Pay account can support multiple merchant records. Each merchant record can be a separate location center which will generate a separate daily settlement report. Many of our API calls require that you specify which MERCHID when executing a particular function.

### Installation Instructions

#### Step 1: Setup your Environment

Make sure you have completed the [React Native - Environment Setup](https://reactnative.dev/docs/environment-setup) instructions until the "Creating a new application" step before proceeding.

#### Step 2: Install Components

**For iOS**

From the project's _root folder_, run npm install. This will load the node\_modules packages that are listed in the package.json file. Change directories to the ios folder and run pod install.

```
# in a terminal window
  npm install

  cd ios
  pod install
```

#### **Configure Keys**

In the app.tsx file, these values are passed to the `EasyPayModule.configureSecrets` method:

```swift
EasyPayModule.configureSecrets("YOUR_API_KEY", "YOUR_HMAC_SECRET", "SENTRY_DSN", true)
```

### Start Your Application

First, you will need to start the **Metro Server**, the JavaScript bundler that ships with React Native. To start Metro, run the following command from the _root_ of your React Native project:

```
# using npm
  npm start

# OR using Yarn
  yarn start
```

### **Run the App**

Let Metro Bundler run in its _own_ terminal. Open a _new_ terminal from the _root_ of your React Native project. Run the following command to start your Android or iOS app:

```
# using npm
  npm run android

# OR using Yarn
  yarn android
```

```
# using npm
  npm run ios

# OR using Yarn
  yarn ios
```

If everything is set up correctly, you should see your new app running in your Android Emulator or iOS Simulator.  This is one way to run your app — you can also run it directly from within Android Studio and Xcode respectively. To launch the wrapper in XCode, click on the EasyPayRN.xcworkspace file.

### Certificates

When API traffic originates from unknown networks or mobile devices, we mandate that any credit card numbers be encrypted prior to transmission to Number. We will provide an RSA 2048 certificate which is used by Number's Android and iOS SDKs to automatically encrypt the card data.

During the initialization, the process of downloading the certificate is starting. Proceeding with any call before downloading has finished will result in an error  `RsaCertificateError.failedToLoadCertificateData`.

To test the certificate download, call:&#x20;

```swift
EasyPayModule.loadCertificate()
```

### Using the Widgets

Number's prebuilt payment UI components allow you to collect and process credit card information in a secure way.

#### **Managing Cards**

For managing saved cards without making a payment, the following initializer should be used:

```swift
await EasyPayModule.manageAndSelect(config, user, payment, address)
```

```javascript
 # testing from App.tsx
  const testManageAndSelect = async () => {
    try {
      const config = {
        rpguid: "3d3424a6-c5f3-4c28",
        customerReferenceId: "12456",
        merchantId: "1"
      };
      const user = {
        endCustomerFirstName: "Simple",
        endCustomerLastName: "Simon",
      }
      const payment = {
        limitPerCharge: "1000.0",
        limitLifetime: "10000.0",
        // cardId: 123 // optional
      }
      const address = {
        endCustomerAddress1: "A1",
        endCustomerAddress2: "",
        endCustomerCity: "Newark",
        endCustomerState: "AZ",
        endCustomerZip: "90210",
      }
      await EasyPayModule.manageAndSelect(config, user, payment, address)
    } 
   catch (error) {
     console.log(error)
   }
  }
```

The config and payment objects are used for passing additional payment details not visible for the end user. Either customerReferenceId or rpguid must be provided to get the list of consents of a specific customer. In case of of incorrect initialization data, `CardSelectionViewControllerInitError` will be thrown.

**Collecting Payments**

For managing saved cards and collecting a payment, following initializer should be used:

```swift
await EasyPayModule.pay (config, user, payment, address)
```

```javascript
# testing from App.tsx
  const testManageAndPay = async () => {
    try {
      const config = {
        rpguid: "3d3424a6-c5f3-4c28",
        customerReferenceId: "12456",
        merchantId: "1"
      };
      const user = {
        endCustomerFirstName: "Simple",
        endCustomerLastName: "Simon",
      }
      const payment = {
        amount: "25.99",
        limitPerCharge: "1000.0",
        limitLifetime: "10000.0",
        // cardId: 123 // optional
      }
      const address = {
        endCustomerAddress1: "A1",
        endCustomerAddress2: "",
        endCustomerCity: "Newark",
        endCustomerState: "AZ",
        endCustomerZip: "90210",
      }
      await EasyPayModule.pay (config, user, payment, address)
    } 
    catch (error) {
      console.log(error)
    }
  }
```

### Event Emitters

Communication between the Number SDK widgets and the React Native wrapper is handled via event emitters. These event emitters allow you to respond to user events such as a payment being processed. The EasyPayModule.swift file contains functions that map to the iOS SDK's `CardPaymentDelegate` and `CardSelectionDelegate` protocols. These functions send events that are received in the wrapper's Javascript code.

```swift
//MARK: - CardSelectionDelegate

func didSelectCard(consentId: String) {
  RNEventEmitter.emitter.sendEvent(
    withName: "onCardSelected",
    body: ["consentId": consentId])

}

func didDeleteCard(consentId: Int, success: Bool) {
  if success {
    RNEventEmitter.emitter.sendEvent(
      withName: "onCardDeleted",
      body: ["consentId": consentId])
  }
}

func didSaveCard(
  consentId: Int?,
  expMonth: Int?,
  expYear: Int?,
  last4digits: String?,
  success: Bool
) {
  if !success {
    return
  }
  guard let cid = consentId else { return }
  var body: [String: Any] = ["consentId": cid]

  if let month = expMonth {
    body["expMonth"] = month
  }
  if let year = expYear {
    body["expYear"] = year
  }
  if let digits = last4digits {
    body["last4digits"] = digits
  }

  RNEventEmitter.emitter.sendEvent(
    withName: "onCardSaved",
    body: body)
}

//MARK: - CardPaymentDelegate

func didPayWithCard(
  consentId: Int?,
  paymentData: PaymentData?,
  success: Bool
) {
  if !success {
    return
  }

  //guard let cid = consentId else { return }
  var cid = 0
  if consentId != nil {
    cid = consentId ?? 0
  }

  let body: [String: Any?] = [
    "consentId": cid,
    "functionOk": paymentData?.functionOk == true,
    "txApproved": paymentData?.txApproved == true,
    "responseMessage": paymentData?.responseMessage,
    "errorMessage": paymentData?.errorMessage,
    "errorCode": paymentData?.errorCode,
    "txnCode": paymentData?.txnCode,
    "avsResult": paymentData?.avsResult,
    "cvvResult": paymentData?.cvvResult,
    "acquirerResponseEMV": paymentData?.acquirerResponseEMV,
    "txId": paymentData?.txId,
    "requiresVoiceAuth": paymentData?.requiresVoiceAuth == true,
    "isPartialApproval": paymentData?.isPartialApproval == true,
    "responseAuthorizedAmount": paymentData?.responseAuthorizedAmount,
    "responseApprovedAmount": paymentData?.responseApprovedAmount,
  ]

  RNEventEmitter.emitter.sendEvent(
    withName: "onCardPaid",
    body: body.compactMapValues({ $0 }))

}

```

On the react native side, configure event listeners to respond to the raised events:

```javascript
# testing from App.tsx

    // iOS Events
    const selectionListener = nativeEventEmitter.addListener('onCardSelected', (data: {
        consentId: String;
    }) => {
        console.log('Card Selected', data.consentId);
    });
    const deleteListener = nativeEventEmitter.addListener('onCardDeleted', (data: {
        consentId: String;
    }) => {
        console.log('Card Deleted', data.consentId);
    });
    const saveListener = nativeEventEmitter.addListener('onCardSaved', (data: {
        consentId: String;
    }) => {
        console.log('Card Saved', data.consentId);
        /* See also:
          consentId
          expMonth
          expYear
          last4Digits
        */
    });
    const paidListener = nativeEventEmitter.addListener('onCardPaid', (data: {
        consentId: string;
        functionOk: boolean;
        txApproved: boolean;
        responseMessage: string;
        errorMessage: string;
        errorCode: int;
        txnCode: string;
        avsResult: string;
        cvvResult: string;
        acquirerResponseEMV: string;
        txId: int;
        requiresVoiceAuth: boolean;
        isPartialApproval: boolean;
        responseAuthorizedAmount: number;
        responseApprovedAmount: number;

    }) => {

        console.log('functionOK', data.functionOk);
        console.log('Consent ID', data.consentId);
        console.log('Transaction ID', data.txId);
    });

    // Android Events
    const manageErrorListener = nativeEventEmitter.addListener('onManageError', (data: {
        error: String;
    }) => {
        console.log('Manage error', data.error);
    });

    const manageResultListener = nativeEventEmitter.addListener('onManageResult', (data: {
        selectedConsentId ? : number;
    }) => {
        console.log('Selected Consent Id', data.selectedConsentId);      
    });

    const paymentErrorListener = nativeEventEmitter.addListener('onPaymentError', (data: {
        error: String;
    }) => {
        console.log('Payment error', data.error);
    });
    const paymentCancelListener = nativeEventEmitter.addListener('onPaymentCancelled', () => {
        console.log('Payment cancelled');
    });
    const paymentResultListener = nativeEventEmitter.addListener('onPaymentResult', (result: {
        data: {
            errorMessage: string;
            responseMessage: string;
            txApproved: boolean;
            txId: number;
            txCode: string;
            avsResult: string;
            acquirerResponseEmv: string;
            cvvResult: string;
            isPartialApproval: boolean;
            requiresVoiceAuth: boolean;
            responseApprovedAmount: number;
            responseAuthorizedAmount: number;
            responseBalanceAmount: number;
        };
    }) => {        
        console.log('Payment result', result.data);
    });
```













