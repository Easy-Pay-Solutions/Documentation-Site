---
hidden: true
---

# Apple Pay / Google Pay

In order to add Apple Pay / Google Pay functionality to your PayForm you modify your request as follows:

**No Apple Pay:**

{% code overflow="wrap" %}
```
"EndPoint": "PayForm/PF.aspx",
```
{% endcode %}

**With Apple Pay:**

{% code overflow="wrap" %}
```
 "EndPoint": "PayForm/PFA.aspx",
```
{% endcode %}

#### Considerations&#x20;

**1) Notify us that you are ready to Test**  ( we will modify your test account )

***

**2) Size** - If our PayForm determines that Apple Pay can be used during the browser session you will notice the following buttons appear:

<figure><img src="../../../../.gitbook/assets/applepayss.png" alt=""><figcaption></figcaption></figure>

(PayForm will grow vertically depending on what is detected.)

***

**3) Domain -** If you plan to display our widget within an IFRAME we will need to get your Domain approved.\
\
Contact our tech team to accomplish this. We will have you publish a small text file on your server.\
\
Next we send a request to Apple which allows them to verify the text file exists so that they can trust your domain ( as a parent page )

***

**4) SandBox -** In order to get approvals in the sandbox you will need:\
\- A Sandbox Apple ID (different from your real Apple ID)\
\- An iPhone or iPad that supports Apple Pay.\
\- The device must be signed into iCloud with the sandbox account, not your normal Apple ID.\
\
Note :  you can log in to our Sandbox ApplePay ID if you wish:\
Username : MacSand@number.tech\
Password : All6cowswentswimming!

***

#### Step-by-step: How to get test cards into your Wallet

1. **Create a Sandbox Apple ID ( or use ours )**\
   Go to Apple’s developer site → _Account_ → _Users and Access_ → _Sandbox Testers_. Create a new tester account (email must be unique and not tied to an existing Apple ID).
2. **Sign out of your real Apple ID on your device**\
   Settings → Your Name → _Sign Out_.
3. **Sign in with the Sandbox Apple ID**\
   Settings → Sign in → use the sandbox credentials.
4. **Open the Wallet app**\
   Once the device is in sandbox mode, **Apple Pay will automatically offer test cards** when you tap **Add Card**. You’ll see region‑appropriate test Visa, Mastercard, Amex, etc. You do _not_ enter card numbers manually - Apple provides them.
5. **Use the cards only in sandbox-supported apps/sites**\
   They will not work in production environments. Real cards are required for production testing.
6. **This link has valid test cards you can put in your wallet:**\
   [Sandbox Testing - Apple Pay - Apple Developer](https://developer.apple.com/apple-pay/sandbox-testing/)
