---
description: Methods related to Text2Pay
---

# Text to Pay

## Send a Payment Reminder

<mark style="color:green;">`POST`</mark> /ICardProcess/SMSPayment

Send a payment reminder to the client through a text or e-mail.&#x20;

{% hint style="info" %}
Once the client receives the reminder, they can click a link to open a payment widget and to make a payment. Once the payment is submitted, a transaction receipt would be e-mailed to the e-mail address that is on file.
{% endhint %}

{% tabs %}
{% tab title="Request body" %}
{% include "../../.gitbook/includes/param-sess-key.md" %}

***

`PaymentObject` api\_SMSPayment (object)

Fields: Person, Email, Phone, MessageType, RefID, RPGUID, MessageBody, AcctHolderID, Amount, AcctHolderID, Amount, ConsentID, DueOn, EINDEX, MerchID, TXID, WType, RedirectURL, ExpiresOn, SingleUse, OptParam, WidgetURL
{% endtab %}

{% tab title="Response body" %}
{% include "../../.gitbook/includes/param-ok-msg-errs.md" %}

***

`PaymentUrl` string

The payment URL that was generated and send alongside the reminder.
{% endtab %}
{% endtabs %}

