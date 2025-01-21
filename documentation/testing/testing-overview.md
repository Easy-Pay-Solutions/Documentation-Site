---
description: Transaction and consent verification using the Virtual Terminal
---

# Testing Overview



## Testing integration <a href="#testing-integration" id="testing-integration"></a>

After API, PayForm, or widget integration, it is important to login to our Virtual Terminal and make sure the transactions and consents appear correct. The Number Support Team can provide you with Virtual Terminal credentials.

{% hint style="info" %}
An example user name for the Virtual Terminal can look like this: **VT4914533**
{% endhint %}

<figure><img src="../../.gitbook/assets/Testing Integration.png" alt=""><figcaption><p>Virtual Terminal login screen</p></figcaption></figure>



***



## Verifying transactions <a href="#verifying-transactions" id="verifying-transactions"></a>

Once logged in, expand the _Transactions_ tab in the navigation on the left, then click on _Search_.

<figure><img src="../../.gitbook/assets/Verifying Transactions 1 (2).png" alt=""><figcaption><p>Virtual Terminal search screen</p></figcaption></figure>

This will show the list of transactions created. Select the transaction to be verified, and click on _Full Detail_ button under _Transaction Operations_. A pop up will open to show all the information about the transaction, account holder, and the end customer.

Make sure the amount, last four digits of the credit card, card type, and expiration date are correct.

<figure><img src="../../.gitbook/assets/Verifying Transactions 2.png" alt=""><figcaption><p>Virtual Terminal full transaction detail</p></figcaption></figure>



### Testing declines <a href="#testing-declines" id="testing-declines"></a>

There are scenarios where the transaction can get declined due to various reasons like insufficient funds, card not allowed, lost/stolen card, etc. In such cases, the transaction would appear as _FAILED_.

{% hint style="info" %}
You can find penny codes for testing declines in the [Global Payments Testing](global-payments-testing.md) section.
{% endhint %}

<figure><img src="../../.gitbook/assets/Verifying Transactions - Testing Declines 1 (2).png" alt=""><figcaption><p>Virtual Terminal failed transaction</p></figcaption></figure>

Clicking on _Full Detail_ can show the reason for decline as highlighted below:

<figure><img src="../../.gitbook/assets/Verifying Transactions - Testing Declines 2.png" alt=""><figcaption><p>Virtual Terminal full detail with failed <code>TxStatus</code> and <code>Flags</code></p></figcaption></figure>



### Testing partial authorizations <a href="#doing-a-partial-authorization-with-aspen" id="doing-a-partial-authorization-with-aspen"></a>

If you need to do partial authorizations, we offer an option named `AllowPartialAuth`.

{% hint style="info" %}
To turn on `AllowPartialAuth`, send a request to the Number team.
{% endhint %}

If this option is turned on, then it is possible for a transaction to be approved for the partial amount when the card has an available balance which is less than the amount being authorized.&#x20;

In this case, we will return the approved amount and the balance due. **This remaining balance could be collected in another form of payment or at a later date.**

If this option is turned on, then you can monitor the following values as part of the sale response:

* `IsPartialApproval` boolean
* `ResponseAuthorizedAmount` decimal
* `ResponseBalanceAmount` decimal
* `ResponseApprovedAmount` decimal

#### Partial auth testing data <a href="#partial-auth-testing-data" id="partial-auth-testing-data"></a>

To test a partial authorization, you can use one of these cards:

<table data-view="cards"><thead><tr><th align="center"></th><th data-hidden data-card-cover data-type="files"></th></tr></thead><tbody><tr><td align="center">4788 2500 0002 8291</td><td><a href="../../.gitbook/assets/Visa icon.png">Visa icon.png</a></td></tr><tr><td align="center">4055 0111 1111 1111</td><td><a href="../../.gitbook/assets/Visa icon.png">Visa icon.png</a></td></tr><tr><td align="center">6011 0009 9550 0000</td><td><a href="../../.gitbook/assets/Discover icon.png">Discover icon.png</a></td></tr><tr><td align="center">6011 2121 0000 0087</td><td><a href="../../.gitbook/assets/Discover icon.png">Discover icon.png</a></td></tr><tr><td align="center">5454 5454 5454 5454</td><td><a href="../../.gitbook/assets/master card icon.png">master card icon.png</a></td></tr><tr><td align="center">5405 2222 2222 2226</td><td><a href="../../.gitbook/assets/master card icon.png">master card icon.png</a></td></tr><tr><td align="center">5473 0000 0000 0007</td><td><a href="../../.gitbook/assets/master card icon.png">master card icon.png</a></td></tr><tr><td align="center">3714 4963 5398 431</td><td><a href="../../.gitbook/assets/Amex icon.png">Amex icon.png</a></td></tr></tbody></table>

{% hint style="info" %}
Using the test cards, if you enter the amount of $2.78, you should get partial approval for $2.57, and if you enter the amount of $3.26, you should get a partial approval for $1.26.
{% endhint %}



### Testing receipts <a href="#testing-receipts" id="testing-receipts"></a>

The receipt can also be printed in the Virtual Terminal by clicking the _Merchant_ or _Customer_ button.

<figure><img src="../../.gitbook/assets/Verifying Transactions - Testing Receipts 1 (1).png" alt=""><figcaption><p>Virtual Terminal search screen with receipt buttons pointed out</p></figcaption></figure>

<figure><img src="../../.gitbook/assets/Verifying Transactions - Testing Receipts 2.png" alt=""><figcaption><p>Virtual Terminal receipt pop-up (merchant copy)</p></figcaption></figure>



***



## Verifying consents <a href="#verifying-consents" id="verifying-consents"></a>

Click on the _Consent List_ menu as shown below:

<figure><img src="../../.gitbook/assets/Verifying Consents 1 (2).png" alt=""><figcaption><p>Virtual Terminal consent search screen</p></figcaption></figure>

Select the consent that needs to be verified from the grid. Click the _Full Detail_ button and make sure the consent, account holder, and end customer details look correct.

<figure><img src="../../.gitbook/assets/Verifying Consents 2.png" alt=""><figcaption><p>Virtual Terminal consent full detail</p></figcaption></figure>

To view the consent agreement, click on the _Merchant Consent_ or _Customer Consent_.

<figure><img src="../../.gitbook/assets/Verifying Consents 3.png" alt=""><figcaption><p>Consent annual receipt (merchant copy)</p></figcaption></figure>
