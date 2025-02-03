---
description: Send payment reminders to clients through text or e-mail
---

# Payment Reminders

<figure><img src="../../.gitbook/assets/Payment Reminder 1.png" alt=""><figcaption></figcaption></figure>

As an integrator, you may wish to send a payment reminder to a client through a text or e-mail which will allow them to pay the amount due. Here's an example reminder:

> You have a payment due to Merchant XYZ of $125.00 due on 10/4/2016. Please follow the link below to make the payment. https://easypay5.com/PaymentReminder/?AT=GzNHZXXXXo=sNLs0gh3I9xMKALxwGCjQsXnFycTXV0htipN92dAbU4IIl7E9rFb6YKosbakwUOapfwtQODMdT0=\&Z=1

Once they receive the reminder, they can click the link that is sent along with the message to open a payment page. This will allow them to enter their card details and make a payment.

After the payment is submitted, a transaction receipt would be sent to the e-mail address on file.

<figure><img src="../../.gitbook/assets/transaction receipt.png" alt=""><figcaption></figcaption></figure>



## Implementation

To send a payment reminder using the REST API, use the:

{% hint style="info" %}
[#apicardprocrest-v1.0.0-other-smspay](../../api-reference/rest-api/text-to-pay.md#apicardprocrest-v1.0.0-other-smspay "mention") endpoint.&#x20;
{% endhint %}

To do the same using the SOAP API, you can use [#send-a-payment-reminder](../../api-reference/soap-api/text2pay.md#send-a-payment-reminder "mention")  method.



### Request

Both implementations use a similar body structure, and the fields are described below.

<table><thead><tr><th width="195">Field name</th><th>Description</th></tr></thead><tbody><tr><td>Person</td><td>The name, address, email, and phone number for the payee.</td></tr><tr><td>MessageType</td><td>The type of message for the payee: <em>EMAIL</em>, <em>URLONLY</em>, or <em>TEXT</em>.</td></tr><tr><td>RefID</td><td>A custom user-defined field to save with the transaction.</td></tr><tr><td>RPGUID</td><td>Another custom user-defined field to save with the transaction.</td></tr><tr><td>MessageBody</td><td><p>The message to send. <strong>Use \*\*Merch1\*\* to insert merchant's name into your message template.</strong><br><br>If the body is left empty, a default generic message will be used:<br></p><p><em>You have a Payment Due to [Merchant Name] of [Amount] due on [DueOn]. Please follow the link below to make the Payment. [Link Here]</em></p></td></tr><tr><td>AcctHolderID</td><td>Not used, please fill with 0.</td></tr><tr><td>Amount</td><td>The $ amount to collect.</td></tr><tr><td>ConsentID</td><td>Not used, please fill with 0.</td></tr><tr><td>DueOn</td><td>The payment due date in mm/dd/yyyy or yyyy/mm/dd format to display to the customer.</td></tr><tr><td>EINDEX</td><td>This is your unique Integrator Key Index for encryption. <strong>It should be provided by Number when you make an account with us</strong>, otherwise <a href="../../help/customer-support/">contact Number customer support</a>.</td></tr><tr><td>MerchID</td><td>The unique identifier for the Merchant record.</td></tr><tr><td>TXID</td><td>Not used, please fill with 0.</td></tr><tr><td>WType</td><td>This specifies which payment widget to display, including custom widgets built for your company. <a href="../../help/customer-support/">Contact Number for more information.</a></td></tr><tr><td>RedirectURL</td><td>This specifies where to redirect the user and post the results of the transaction.</td></tr><tr><td>WidgetURL</td><td>The endpoint for the widget payment form, including custom forms. <a href="../../help/customer-support/">Contact Number</a> and we will provide you with a value. You can start with <a href="https://easypay5.com/stdwidget/"><em>https://easypay5.com/stdwidget/</em></a></td></tr><tr><td>ExpiresOn</td><td>A date in yyy-mm-dd format for when the payment link should no longer be available.</td></tr><tr><td>SingleUse</td><td>Indicates whether the payment link should only accept a single payment.</td></tr><tr><td>OptParams</td><td>Parameters which control the design and behavior of the payment form including the visible fields, read-only fields, color and styling, and submission options.<br><br>See the <a data-mention href="../getting-started/integration-options/payform.md#payform-builder">#payform-builder</a> section in the PayForm guide to learn how you can generate those parameters.</td></tr></tbody></table>



### Response

If you didn't catch any exceptions and your response is not null, check the value of `FunctionOK`. If `FunctionOk` is false, it indicates an error that was handled on the Number servers. You can find more details by looking at `ErrMsg` and `ErrCode` included in the response.

**You don't have to do anything else, the reminder was sent successfully.** A friendly response message is included in `RespMsg` field, and the `PaymentURL` is also returned if you wish to store it.



&#x20;
