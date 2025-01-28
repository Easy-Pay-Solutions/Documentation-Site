# Payment Reminder (v1)

## Introduction

As an integrator, you may wish to send a payment reminder to a client through a text or e-mail.&#x20;

Here's an example reminder:

> You have a payment due to Merchant XYZ of $125.00 due on 10/4/2016. Please follow the link below to make the payment.&#x20;
>
> https://easypay5.com/PaymentReminder/?AT=GzNHZXXXXo=sNLs0gh3I9xMKALxwGCjQsXnFycTXV0htipN92dAbU4IIl7E9rFb6YKosbakwUOapfwtQODMdT0=\&Z=1

Once they receive the reminder, they can click the link that is sent along with the message to open a payment page. This will allow them to enter their card details and make a payment.

<figure><img src="../../.gitbook/assets/image (5).png" alt=""><figcaption></figcaption></figure>

After the payment is submitted, a transaction receipt would be sent to the e-mail address on file.

<figure><img src="../../.gitbook/assets/image (6).png" alt=""><figcaption></figcaption></figure>



## Implementation

To send a payment reminder using the REST API, use the [#apicardprocrest-v1.0.0-other-smspay](../../api-reference/rest-api/text-to-pay.md#apicardprocrest-v1.0.0-other-smspay "mention") endpoint.
