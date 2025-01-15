# First Data Testing

### Test Cards <a href="#test-cards" id="test-cards"></a>

<table data-full-width="false"><thead><tr><th width="134">Card Brand</th><th width="146">Card Brand</th><th width="468">Card Number</th></tr></thead><tbody><tr><td><img src="../../.gitbook/assets/Discover icon 2.png" alt="" data-size="original"></td><td><strong>PIN Debit</strong></td><td><strong>4017 7799 9111 3335</strong></td></tr><tr><td><img src="../../.gitbook/assets/1 Visa icon.png" alt="" data-size="original"></td><td><strong>Visa</strong></td><td><strong>4761 5300 0111 1118</strong></td></tr><tr><td><img src="../../.gitbook/assets/1 Master card icon.png" alt="" data-size="original"></td><td><strong>MasterCard</strong></td><td><strong>5137 2211 1111 6668</strong></td></tr><tr><td><img src="../../.gitbook/assets/1 Discover icon.png" alt="" data-size="original"></td><td><strong>Discover</strong></td><td><strong>6011 2087 0111 7775</strong></td></tr><tr><td><img src="../../.gitbook/assets/1 Amex icon.png" alt="" data-size="original"></td><td><strong>Amex</strong></td><td><strong>3710 3008 9111 338</strong></td></tr></tbody></table>

{% hint style="info" %}
For CVV Match use:

**"123"**
{% endhint %}

{% hint style="info" %}
For AVS Match use:

**Address: 1307 Broad Hollow Road**\
**ZIP: 11747**
{% endhint %}



***



### Generating Declines <a href="#generating-declines" id="generating-declines"></a>

* Transactions below $100.00 will receive an Approved response. A specific approval code will be returned.
* Transactions above $100.00 will receive a Declined response. A specific decline code will be returned.
* The transaction amount sent in the transaction request message is used to determine which error response code will be received in your response. To request an error response code, the last three digits of the transaction amount should be the response code you wish to receive.
* For example, if you need to receive a response message with a 116 response code, then the request message could contain a transaction amount of $101.16. Likewise, if you need to receive a response message with a 318 response code, then the request message could contain a transaction amount of $403.18. A complete list of response codes can be found within Appendix A of the UMF specification in your SDK zip file.



***



### Response Codes <a href="#response-codes" id="response-codes"></a>

{% hint style="danger" %}
Table to implement:&#x20;
{% endhint %}
