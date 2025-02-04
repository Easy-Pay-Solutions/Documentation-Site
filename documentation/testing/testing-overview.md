---
description: Transaction and consent verification using the Virtual Terminal.
---

# Testing Overview



## Testing integration <a href="#testing-integration" id="testing-integration"></a>

After API, PayForm, or widget integration, it is important to login to our Virtual Terminal and make sure the transactions and consents appear correct. The Number Support Team can provide you with Virtual Terminal credentials.

{% hint style="info" %}
An example user name for the Virtual Terminal can look like this: **VT4914533**
{% endhint %}

For more information about the Virtual Terminal, see the [virtual-terminal.md](../getting-started/integration-options/virtual-terminal.md "mention") guide. You can access Virtual Terminal using the link below.

{% include "../../.gitbook/includes/link-virtual-terminal.md" %}

<figure><img src="../../.gitbook/assets/Testing 1.png" alt=""><figcaption></figcaption></figure>



***



## Verifying transactions <a href="#verifying-transactions" id="verifying-transactions"></a>

Once logged in, expand the _Transactions_ tab in the navigation on the left, then click on _Search_.

<figure><img src="../../.gitbook/assets/Testing 2.png" alt=""><figcaption></figcaption></figure>

This will show the list of transactions created. Select the transaction to be verified, and click on _Full Detail_ button under _Transaction Operations_. A pop up will open to show all the information about the transaction, account holder, and the end customer.

Make sure the amount, last four digits of the credit card, card type, and expiration date are correct.

<figure><img src="../../.gitbook/assets/Testing 3 (1).png" alt=""><figcaption></figcaption></figure>



### Testing declines <a href="#testing-declines" id="testing-declines"></a>

There are scenarios where the transaction can get declined due to various reasons like insufficient funds, card not allowed, lost/stolen card, etc. In such cases, the transaction would appear as _FAILED_.

{% hint style="info" %}
You can find penny codes for testing declines in the [global-payments-testing.md](global-payments-testing.md "mention") section.
{% endhint %}

You can click _Full Detail_ to try to find out the reason for decline by checking `TxStatus`, `Flags,` and other values.



### Testing partial auth <a href="#doing-a-partial-authorization-with-aspen" id="doing-a-partial-authorization-with-aspen"></a>

{% include "../../.gitbook/includes/segment-allow-partial-auth.md" %}

#### Partial auth testing data <a href="#partial-auth-testing-data" id="partial-auth-testing-data"></a>

To test a partial authorization, you can use one of these cards:

<table data-view="cards"><thead><tr><th></th><th data-hidden data-card-cover data-type="files"></th></tr></thead><tbody><tr><td><strong>4788 2500 0002 8291</strong></td><td><a href="../../.gitbook/assets/Visa icon.png">Visa icon.png</a></td></tr><tr><td><strong>4055 0111 1111 1111</strong></td><td><a href="../../.gitbook/assets/Visa icon.png">Visa icon.png</a></td></tr><tr><td><strong>6011 0009 9550 0000</strong></td><td><a href="../../.gitbook/assets/Discover icon.png">Discover icon.png</a></td></tr><tr><td><strong>6011 2121 0000 0087</strong></td><td><a href="../../.gitbook/assets/Discover icon.png">Discover icon.png</a></td></tr><tr><td><strong>5454 5454 5454 5454</strong></td><td><a href="../../.gitbook/assets/master card icon.png">master card icon.png</a></td></tr><tr><td><strong>5405 2222 2222 2226</strong></td><td><a href="../../.gitbook/assets/master card icon.png">master card icon.png</a></td></tr><tr><td><strong>5473 0000 0000 0007</strong></td><td><a href="../../.gitbook/assets/master card icon.png">master card icon.png</a></td></tr><tr><td><strong>3714 4963 5398 431</strong></td><td><a href="../../.gitbook/assets/Amex icon.png">Amex icon.png</a></td></tr></tbody></table>

{% hint style="info" %}
Using the test cards, if you enter the amount of $2.78, you should get partial approval for $2.57, and if you enter the amount of $3.26, you should get a partial approval for $1.26.
{% endhint %}



### Testing receipts <a href="#testing-receipts" id="testing-receipts"></a>

The receipt can also be printed in the Virtual Terminal by expanding the _Receipts_ dropdown and clicking the _Merchant_ or _Customer_ button.

<figure><img src="../../.gitbook/assets/Testing 4.png" alt=""><figcaption></figcaption></figure>



***



## Verifying consents <a href="#verifying-consents" id="verifying-consents"></a>

Click on the _Reports_ menu and choose _Consents._

Select the consent that needs to be verified from the grid. Click the _Full Detail_ button and make sure the consent, account holder, and end customer details look correct.

<figure><img src="../../.gitbook/assets/Testing 5.png" alt=""><figcaption></figcaption></figure>

To view the consent agreement, click on the _Merchant Consent_ or _Customer Consent_.

<figure><img src="../../.gitbook/assets/Testing 6.png" alt=""><figcaption></figcaption></figure>



