---
description: >-
  Configuring your PayForm for integrated payments via the Apple and Google
  digital wallets
icon: cc-apple-pay
---

# Apple Pay / Google Pay

In order to add Apple Pay / Google Pay functionality to your PayForm, you'll need to modify your [request](../../../../api-reference/rest-api/payform.md) as follows:

**InitParams.EndPoint remains the same:**

{% code overflow="wrap" %}
```jsonc
"EndPoint": "PayForm/PF.aspx"
```
{% endcode %}

**WidOptions.eFeatures should be updated to the code "0004":**

{% code overflow="wrap" lineNumbers="true" %}
```json
"WidOptions": {
      "eVisible": "2EFF",
      "eReadOnly": "0000",
      "eStyles": "0001",
      "eSubmission": "0210",
      "eFeatures": "0004", /* this code must be present */
      "eColors": "#ffffff,#428bca,#007bff,#212121,#ffffff,#212121,#ffffff"
}
```
{% endcode %}

#### Considerations&#x20;

1. **Notify us prior to submitting test transactions:** Notify the Number team when you are ready to test. We will configure your account to prepare it for your test submissions.
2. **PayForm appearance/size:** If our PayForm determines that Apple Pay or Google Pay can be used during the cardholder's browser session, you will notice one or both additional buttons displayed (see below). The PayForm will grow vertically as appropriate to accomodate the additional pay buttons.

<figure><img src="../../../../.gitbook/assets/applepayss.png" alt=""><figcaption></figcaption></figure>

3. **Domain:** If you plan to display our widget within an iframe, we will need to get your domain approved (Apple Pay only).  Contact the Number tech team to accomplish this. We will have you publish a small text file on your web server which Apple will discover.
4. **SandBox:** In order to get approvals in the sandbox (Apple Pay only) you will need:\
   \- A Sandbox Apple ID (different from your real Apple ID)\
   \- An iPhone or iPad that supports Apple Pay.\
   \- The device must be signed into iCloud with the sandbox account, not your normal Apple ID.

#### Step-by-step: How to get test cards into your Apple Pay Wallet

1. **Create a Sandbox Apple ID** \
   Go to Apple’s developer site → _Account_ → _Users and Access_ → _Sandbox Testers_. Create a new tester account (email must be unique and not tied to an existing Apple ID).
2. **Sign out of your real Apple ID on your device**\
   Settings → Your Name → _Sign Out_.
3. **Sign in with the Sandbox Apple ID**\
   Settings → Sign in → use the sandbox credentials.
4. **Open the Wallet app**\
   Once the device is in sandbox mode, you can begin to add Sandbox test cards to your **Apple Pay Wallet (**&#x74;ap **Add Card)**.&#x20;
5. **This link has valid test cards you can put in your wallet:**\
   [Sandbox Testing - Apple Pay - Apple Developer](https://developer.apple.com/apple-pay/sandbox-testing/)
6. **Use the cards only in sandbox-supported apps/sites**\
   They will not work in production environments. Real cards are required for production testing.



## Google Pay Considerations&#x20;

To test Google Pay in our PayForm you need to do the following:

1. Notify us that you are ready to test (we will modify your test account)
2. Make sure you are logged in to your google account
3. Open your Number PayForm using your test account. The Google Sandbox Wallet should become available automatically.

The sandbox test cards provided by Google often do not pass CVV match requirements. You may want to leave that option out of the submission options while you test.&#x20;

Once you are ready to Pay you will see a message which indicates that no actual funds will be charged in the TEST ENVIRONMENT.&#x20;



<figure><img src="../../../../.gitbook/assets/image (20).png" alt=""><figcaption></figcaption></figure>

&#x20;
