---
description: Getting started with Virtual Terminal for Number
---

# Virtual Terminal (WIP)

<figure><img src="../../../.gitbook/assets/epvt0 full width (2).png" alt=""><figcaption></figcaption></figure>



## Introduction

The Virtual Terminal (VT) is a web application that provides all types of credit card processing functionality. The VT is the fastest way to start trying out our payment services.&#x20;

{% embed url="https://easypay5.com/VT" %}

When you log in to the Virtual Terminal, you are brought to the home screen. The number of open transactions and scheduled payments due display at the top of the screen. Your default merchant and user roles are listed just below, along with the expiration date of your password.&#x20;

<figure><img src="../../../.gitbook/assets/epvt1 docs.png" alt=""><figcaption></figcaption></figure>



***



## Payments

Instructions on how to manage various payments using the Virtual Terminal.&#x20;

Before you start, you may want to read about using your Verifone device with the Virtual Terminal in the [verifone-v1.md](verifone-v1.md "mention") guide.



### Non-EMV Payments

Click the _Credit Cards_ tab on the left side of the screen, then _Sale_.

When you swipe the credit card through your USB reader, the card information will automatically populate securely into the required fields. After swiping, enter the $ amount to be charged. You may also manually enter the information on your keyboard.

{% include "../../../.gitbook/includes/info-same-as-cardholder.md" %}

A patient / guest ID or a service description can also be added here and searched for later. The ID will also print on the **receipt**, and the service description will print on the **settlement report**.



### EMV Payments

Click the _Credit Cards_ tab on the left side of the screen, then on _Sale-EMV_.&#x20;

You will click _Insert Chip_ or _Manual Card Entry_.&#x20;

Clicking on _Insert Chip_ will prompt the end-user or customer to insert or tap their card for contactless payments. For _Manual Card Entry_, the end user must enter the full card number, expiration date, and CVV code by pressing the green enter button on the Verifone after each entry.&#x20;

{% include "../../../.gitbook/includes/info-same-as-cardholder.md" %}

{% include "../../../.gitbook/includes/block-cardholder-data-on-receipt-and-batch-report.md" %}



***



## Create consents

All consent types allow a card to be charged without the card or customer being present. Consents can be created by swiping the card or manually entering the information.

A consent receipt is always created by the system for your customer to sign. We encourage your office to get signatures for consents whenever possible.

An email address can be added to the consent so your customer will receive a receipt when the consent has been used.&#x20;

{% include "../../../.gitbook/includes/info-same-as-cardholder.md" %}

{% include "../../../.gitbook/includes/block-cardholder-data-on-receipt-and-batch-report.md" %}



### Annual and one-time

<figure><img src="../../../.gitbook/assets/epvt2.png" alt=""><figcaption></figcaption></figure>

Creating annual and one-time consents allows your office to charge a card at a later date. **This can be useful in situations where you expect a balance to be due after services have been provided.**

Annual consents require that a max charge be determined as a limit per transaction. This can be any $ amount determined by your office.&#x20;

An annual consent can be used multiple times, and a one-time consent can only be used once.&#x20;

{% hint style="info" %}
Both annual and one-time consents are valid until the card expires or 365 days have passed.
{% endhint %}

An email address can be added to the consent so your customer will receive a receipt when the consent has been used.&#x20;

{% include "../../../.gitbook/includes/info-same-as-cardholder.md" %}

{% include "../../../.gitbook/includes/block-cardholder-data-on-receipt-and-batch-report.md" %}



### Fixed recurring

<figure><img src="../../../.gitbook/assets/epvt3.png" alt=""><figcaption></figcaption></figure>

Creating a fixed recurring consent allows your office to set up a payment plan with your customer.  **This can be useful in situations where your customer has an outstanding balance due.**

{% hint style="info" %}
Fixed recurring consents can be setup for any length of time.
{% endhint %}

An email address can be added to the consent so your customer will receive a receipt

{% include "../../../.gitbook/includes/info-same-as-cardholder.md" %}

{% include "../../../.gitbook/includes/block-cardholder-data-on-receipt-and-batch-report.md" %}



### Subscription

<figure><img src="../../../.gitbook/assets/epvt4.png" alt=""><figcaption></figcaption></figure>

Creating a subscription consent allows your office to set up a re-occurring payment indefinitely. **This can be useful in situations where your customer makes a regular donation or payment to your organization.**&#x20;

{% hint style="info" %}
The subscription consent end date is always automatically set to the card expiration date.
{% endhint %}

Subscription payments can be processed manually or automatically depending on your preference. You can change the payment amount as well as the scheduled dates for your subscription consent.&#x20;

To alter the schedule, you will modify the _Payment Adjust Date_. **The system will discard the previously scheduled payment plan and calculate a new one.** Only those scheduled payments for today and beyond will get processed, and it will not attempt to process payments for dates in the past.&#x20;

You can also place a subscription on hold. **This will pause all processing until the hold is released.** Once released, payments will resume for all present and future payments as calculated using your dates and amounts.



***



## Consent list

The consent list is where you will manage your consents after they have been created.  The query filter can be used to search your consent list.

<figure><img src="../../../.gitbook/assets/epvt5.png" alt=""><figcaption></figcaption></figure>

In the _Consent Operations_ box right above the table, there are several options available to help you manage your consents.

{% stepper %}
{% step %}
#### **Edit**

The edit screen allows you to add or change the email address associated with consent, update the billing zip code and expiration date, add or change the reference ID and service description.
{% endstep %}

{% step %}
#### **Receipts**

Allows you to reprint the consent agreement.
{% endstep %}

{% step %}
#### Full Detail

Displays all of the information associated with the consent.
{% endstep %}

{% step %}
#### Cancel Consent

This option will open a dialog box to confirm you want to cancel the consent.
{% endstep %}

{% step %}
#### List Transactions

Lists transactions that have been processed on the selected consent.
{% endstep %}

{% step %}
#### Edit Schedule

This option will open a dialog box that lists the payment schedule for a fixed recurring consent. We recommend using this to postpone a payment or two.&#x20;

{% hint style="warning" %}
If your customer wants to change the schedule completely, it is recommended that you cancel the existing consent and create a new one.
{% endhint %}
{% endstep %}

{% step %}
#### Charge

Use when you want to charge an amount to annual and one-time consents.

<figure><img src="../../../.gitbook/assets/epvt6 left-align (1).png" alt=""><figcaption></figcaption></figure>
{% endstep %}

{% step %}
#### Process

Run fixed recurring consents and subscriptions.&#x20;

{% hint style="success" %}
Scheduled payments can also be run automatically on the day they are due. [Contact Number](../../../help/customer-support/) and we'll turn this feature on up for you.
{% endhint %}

Filter the consents you want to run by date range and consent type. Once you have the consents you want to charge filtered, you can click _Process All to **process all payments due**_. You can also individually select consents and run them by clicking _Process Selected_.&#x20;

The option to reschedule or cancel a payment are also available on this screen.
{% endstep %}

{% step %}
#### Failed Payments

If a customer’s card is declined, you will receive a notification report.
{% endstep %}

{% step %}
#### Payment History

This displays a history of payments run on a particular consent through the _Scheduled Payments_ option.
{% endstep %}
{% endstepper %}



***



## <mark style="background-color:orange;">Transaction list</mark>

The transaction list is where you will view and manage the transactions.

<figure><img src="../../../.gitbook/assets/epvt7.png" alt=""><figcaption></figcaption></figure>

{% stepper %}
{% step %}
#### Search

Search your database, create reports based on results, void, credit, and reprint receipts.
{% endstep %}

{% step %}
#### Query filter

Filter transactions based on the merchant the transaction was processed under, the date range, transaction status, and transaction type.&#x20;

<table><thead><tr><th valign="top">TxStatus</th><th valign="top">TxType</th></tr></thead><tbody><tr><td valign="top"><em>OPEN</em> - An authorized transaction that has not been settled.</td><td valign="top"><em>CCAUTHONLY</em> - Authorization only, not a live transaction.</td></tr><tr><td valign="top"><em>SETTLED</em> - A finalized transaction sent for deposit to your account.</td><td valign="top"> <em>CCSALE</em> - An authorized transaction.</td></tr><tr><td valign="top"><em>FAILED</em> - Transaction did not receive an authorization.</td><td valign="top"><em>CCFORCE</em> - Number Support team use only.</td></tr><tr><td valign="top"><em>LOCKED</em> - Transaction has an error.</td><td valign="top"><em>CCVOICE</em> - Transaction authorized by voice authorization operator.</td></tr><tr><td valign="top"><em>VOID</em> - Transaction was voided.</td><td valign="top"><em>CCADJUST</em> - A credit issued through administrative adjustment. Number Support team use only.</td></tr><tr><td valign="top"><em>HOST</em> - Transactions with surcharge or a convenience fee.</td><td valign="top"><em>CCCREDIT</em> - A credit transaction refunded to customer card.</td></tr></tbody></table>
{% endstep %}

{% step %}
#### Search type

Find the search value in a specific field.

<table><thead><tr><th valign="top">Search type</th></tr></thead><tbody><tr><td valign="top"><code>Acct LastName</code> - Last name of the cardholder.</td></tr><tr><td valign="top"><code>Acct FirstName</code> - First name of the cardholder.</td></tr><tr><td valign="top"><code>Cust LastName</code> - Last name of the customer (if different than cardholder).</td></tr><tr><td valign="top"><code>Cust FirstName</code> - First name of the customer (if different than cardholder).</td></tr><tr><td valign="top"><code>RefID</code> - The custom user-defined value entered at the time of transaction.</td></tr><tr><td valign="top"><code>Amount</code> - The $ amount of the transaction.</td></tr></tbody></table>
{% endstep %}

{% step %}
#### Search filter

Further narrow your search with customer specific information.
{% endstep %}

{% step %}
#### Void

Voids can be performed the same day as the transaction before settlement.&#x20;

{% hint style="warning" %}
Transactions under _HOST_ with a surcharge can only be voided within 20 minutes of the transaction's approval.
{% endhint %}
{% endstep %}

{% step %}
#### Credit

Credits (refunds) can be processed after settlement.
{% endstep %}

{% step %}
#### **Full Detail**&#x20;

Displays all the transaction details.
{% endstep %}

{% step %}
#### Receipts

Reprint the receipts.
{% endstep %}
{% endstepper %}



***



## Settlements

View and manage the settlements.

{% stepper %}
{% step %}
#### Settlements

Manually settle transactions.&#x20;

Select the appropriate merchant account.&#x20;

Select individual transactions, and click _Settle Selected_. Click _Settle All_ to settle all open transactions, or click _Preview Batch_ to see what will be settled.

<figure><img src="../../../.gitbook/assets/epvt8.png" alt=""><figcaption></figcaption></figure>
{% endstep %}

{% step %}
#### Batch History

Displays a list of your settlements and allows for reprinting of batch reports.

<figure><img src="../../../.gitbook/assets/epvt9.png" alt=""><figcaption></figcaption></figure>
{% endstep %}
{% endstepper %}



***



## Miscellaneous

In the upper right-hand corner of the screen, there is a menu of miscellaneous operations.

{% stepper %}
{% step %}
#### My Settings

Update your name, email, cellphone number, and change your password
{% endstep %}

{% step %}
#### Logout

Log out and end your session with the Virtual Terminal. An open session will automatically log the user out after 15 minutes of inactivity.

{% hint style="danger" %}
**Remember to always logout or lock your computer when walking away from your workstation.**&#x20;
{% endhint %}
{% endstep %}

{% step %}
#### Contact Us

Displays our support phone number and allows you to send us a secure email.
{% endstep %}
{% endstepper %}



***



## Lockouts

In order to protect our client’s information, it is necessary for us to lockout users who cannot provide correct credentials. **A lockout will occur if incorrect credentials are entered 6 times in a row.**&#x20;

There are two types of lockouts:&#x20;

* **User lockout** occurs when a user entered their **password** incorrectly for 6 successive attempts.&#x20;
* **Endpoint lockout** causes your entire office to be locked out because the **username** entered was unknown to our system, and used for 6 successive attempts.&#x20;

{% hint style="info" %}
If you are experiencing problems authenticating, contact your administrator to reset your credentials. **We recommend to do this before the 6th attempt which could cause a lockout.**
{% endhint %}



If you do experience a **user lockout**, you will need to follow these steps to continue:

{% stepper %}
{% step %}
#### Get new credentials

Obtain new or updated credentials from your administrator
{% endstep %}

{% step %}
#### Reset the terminal

Visit the [reset page](https://easypay5.com/reset) to clear any cookies that have been set on your terminal.
{% endstep %}

{% step %}
#### Try using your new credentials

Login with the new or updated credentials.
{% endstep %}
{% endstepper %}

If you do experience an **endpoint lockout**, you will first need to need to call the [Number support team](../../../help/customer-support/) to get the lock removed, then follow the instructions for a user lockout.&#x20;



### Expired Passwords&#x20;

As an additional security precaution, passwords expire after 4 months. You can see your password expiration date every time you log into the Virtual Terminal. &#x20;

You may choose to change your password as often as you wish, however you must change your password every 4 months at a minimum. **Entering an expired password 6 times in succession will cause a user lockout as described above.**

&#x20;
