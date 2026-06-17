---
hidden: true
icon: comment-dollar
---

# Text2Pay

One Popular feature provided allows you to generate payment links which we can provide to you. In addition, we can deliver these payment links to your customers either by SMS or Email.

The API call needed to invoke this activity is shown here: [Text to Pay](https://app.gitbook.com/o/BBeFXc7fqAfKkKCdsmTJ/s/4UWkWFnnmVPzvJTdMtC0/api-reference/rest-api/text-to-pay)

***

* You can prepopulate the payment form using the cardholder’s name and address if desired.
* You can specify a Reference ID associated with the payment&#x20;
* You can set the Message type to the following:

{% tabs %}
{% tab title="TEXT " %}
For the TEXT option you can choose to create your own Message Body or allow the system to create a default message.

If you use the Text Option and leave the Custom Message Blank you will get a default message using your supplied values. \
\
![](<../../../.gitbook/assets/image (23).png>)
{% endtab %}

{% tab title="EMAIL" %}
For the Email Option you must create a custom message. To help create your message we have provided some Variable fields:&#x20;

* ||Merch1||  when we see this in your message we will replace it with the actual Merchant name
* ||PayLink||  when we see this in your message we will replace it with the payment link
* ||DueOn||  when we see this we will replace it with the Date you specify for payment due date
* ||ExpOn||  when we see this we will replace it with the Date you specify for payment link expiration Date&#x20;

Here is an example Custom Message for EMAIL using the variables above

\<b>Dear John Doe,\</b>\<br />\<br />This is a friendly reminder that you have an outstanding balance of \<br /> $26.56 for your visit on 5/5/2026 with ||Merch1||. \<br />\<br />This payment is due on ||DueOn||. You can easily review your statement and submit your payment securely through our patient Portal \<br />\<br />Or you can also safely follow the link shown here.\<br />||PayLink||\<br/>This Link Expires on ||ExpOn||\<br />\<br />\<b>Thank You\<b>\<br/>||Merch1|| Billing Dept\</b>

This will create an email as follows:\
![](<../../../.gitbook/assets/image (22).png>)
{% endtab %}

{% tab title="URLONLY" %}
In this case we will simply return the payment Url in the API return message which you can use as desired.
{% endtab %}
{% endtabs %}



