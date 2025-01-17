# Testing overview

***



### Testing Integration <a href="#testing-integration" id="testing-integration"></a>

After the API or Widget integration, it is important for our developers to login to our Easy Pay Virtual Terminal and make sure the TRANSACTIONS or CONSENTS created using the API or Widget appears correct. The Easy Pay Support Team can help with the Virtual Terminal Credentials.

{% hint style="info" %}
Virtual Terminal User Name Example: **VT4914533**
{% endhint %}

<figure><img src="../../.gitbook/assets/Testing Integration.png" alt=""><figcaption><p>Exhibit 1: Virtual Terminal Login Screen</p></figcaption></figure>



***



### Verifying Transactions <a href="#verifying-transactions" id="verifying-transactions"></a>

Once logged in, click on the search menu

<figure><img src="../../.gitbook/assets/Verifying Transactions 1 (2).png" alt=""><figcaption><p>Exhibit 2: Virtual Terminal Search Screen</p></figcaption></figure>

This will show the list of transactions created. Select the transaction that needs to be verified. Click on “Full Detail” button. A pop up opens that shows all the transaction information from: AcctHolder, EndCustomer, BIN details, DateCreated, etc.

Make sure the amount, last four digits of the credit card, card type, and expiration date appears correct.

<figure><img src="../../.gitbook/assets/Verifying Transactions 2.png" alt=""><figcaption><p>Exhibit 3: Virtual Terminal Full Transaction Detail</p></figcaption></figure>

#### Testing Declines <a href="#testing-declines" id="testing-declines"></a>

There are scenarios where the Transaction can get Declined due to various reasons like Insufficient funds, Card Not Allowed, Lost/Stolen Card, etc. These can be simulated in the Test Scennario using the Penny Codes. In such cases the Transaction would appear as Status-Failed as shown below:

<figure><img src="../../.gitbook/assets/Verifying Transactions - Testing Declines 1 (2).png" alt=""><figcaption><p>Exhibit 4: Virtual Terminal Search Screen with Failed Transaction Status</p></figcaption></figure>

Clicking on Full Detail can show the reason for Decline as highlighted below:

<figure><img src="../../.gitbook/assets/Verifying Transactions - Testing Declines 2.png" alt=""><figcaption><p>Exhibit 5: Virtual Terminal Full Detail with Failed TxStatus and Flags</p></figcaption></figure>

#### Doing a Partial Authorization With ASPEN <a href="#doing-a-partial-authorization-with-aspen" id="doing-a-partial-authorization-with-aspen"></a>

If you need to do partial authorizations we offer an option named:

**AllowPartialAuth**

If this option is turned on (by request only), then it is possible for a transaction to be approved for the partial amount when the card has an available balance which is less than the amount being authorized. In this case we will return the approved amount and the balance due. This remaining balance could potentially be collected in another form of payment or at a later date.

If this option is turned on, then you can monitor the following values which are part of the sale response.

* `IsPartialApproval` Flag
* `ResponseAuthorizedAmount` DecimalValue
* `ResponseBalanceAmount` DecimalValue
* `ResponseApprovedAmount` DecimalValue

#### Partial Auth Testing Data <a href="#partial-auth-testing-data" id="partial-auth-testing-data"></a>

To test a partial authorization you will do the following:

Use one of these cards:

<table><thead><tr><th width="153"></th><th></th></tr></thead><tbody><tr><td><img src="../../.gitbook/assets/Visa icon.png" alt="" data-size="original"></td><td><strong>VI 4788 2500 0002 8291</strong></td></tr><tr><td><img src="../../.gitbook/assets/Visa icon.png" alt="" data-size="original"></td><td><strong>VI 4055 0111 1111 1111</strong></td></tr><tr><td><img src="../../.gitbook/assets/Discover icon.png" alt="" data-size="original"></td><td><strong>DS 6011 0009 9550 0000</strong></td></tr><tr><td><img src="../../.gitbook/assets/Discover icon.png" alt="" data-size="original"></td><td><strong>DS 6011 0009 9550 0000</strong></td></tr><tr><td><img src="../../.gitbook/assets/master card icon.png" alt="" data-size="original"></td><td><strong>MC 5454 5454 5454 5454</strong></td></tr><tr><td><img src="../../.gitbook/assets/master card icon.png" alt="" data-size="original"></td><td><strong>MC 5405 2222 2222 2226</strong></td></tr><tr><td><img src="../../.gitbook/assets/master card icon.png" alt="" data-size="original"></td><td><strong>MC 5473 0000 0000 0007</strong></td></tr><tr><td><img src="../../.gitbook/assets/Amex icon.png" alt="" data-size="original"></td><td><strong>AE 3714 4963 5398 431</strong></td></tr></tbody></table>

{% hint style="info" %}
Enter the following amount ( 2.78 ) . .should get partial approval for (2.57 )
{% endhint %}

{% hint style="info" %}
Enter the following amount ( 3.26 ) . . should get partial approval for ( 1.26 )
{% endhint %}

#### Testing Receipts <a href="#testing-receipts" id="testing-receipts"></a>

The receipt can also be printed in the Virtual Terminal by clicking the MERCHANT or CUSTOMER button as shown in below images:

<figure><img src="../../.gitbook/assets/Verifying Transactions - Testing Receipts 1 (1).png" alt=""><figcaption><p>Exhibit 6: Virtual Terminal Search Screen with Receipts buttons pointed out</p></figcaption></figure>

<figure><img src="../../.gitbook/assets/Verifying Transactions - Testing Receipts 2.png" alt=""><figcaption><p>Exhibit 7: Virtual Terminal Receipt Pop-up (Merchant Copy)</p></figcaption></figure>



***



## Verifying Consents <a href="#verifying-consents" id="verifying-consents"></a>

Click on Consent List Menu as shown below:

<figure><img src="../../.gitbook/assets/Verifying Consents 1 (2).png" alt=""><figcaption><p>Exhibit 8: Virtual Terminal Consent Search Screen</p></figcaption></figure>

Select the Consent that needs to be verified from the Grid. Click Full Detail button and make sure the Consent, AcctHolder, and EndCustomer details looks correct.

<figure><img src="../../.gitbook/assets/Verifying Consents 2.png" alt=""><figcaption><p>Exhibit 9: Virtual Terminal Consent Full Detail</p></figcaption></figure>

To view the Consent Agreement click on the Merchant or Customer Consent and the pop-up would appear with the Agreement as shown below:

<figure><img src="../../.gitbook/assets/Verifying Consents 3.png" alt=""><figcaption><p>Exhibit 10: Consent Annual Receipt (Merchant Copy)</p></figcaption></figure>
