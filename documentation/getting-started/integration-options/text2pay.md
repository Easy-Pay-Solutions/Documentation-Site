---
icon: comment-dollar
---

# Text2Pay

One Popular feature provided allows you to generate payment links at will using our API. then deliver them to your Cardholders either by SMS or Email.

The API call needed to invoke this activity is shown here: [Text to Pay](https://app.gitbook.com/o/BBeFXc7fqAfKkKCdsmTJ/s/4UWkWFnnmVPzvJTdMtC0/api-reference/rest-api/text-to-pay)

This singular API call allows you to configure the payment form in terms of visible fields  , readonly fields and other stylings and behaviors as well as deliver it with a custom message to your cardholders. You can prepopulate the form with information such as name and address and PatientID. You can pass Background information or other Reference data which we will associate with the transaction when once authorized.&#x20;

#### Field Descriptions&#x20;

MessageType: ( TEXT,EMAIL,URLONLY )\
RefID: ( user defined field )&#x20;\
RPGUID: ( user defined field )

_MessageBody:_ (here you can create a custom message to send via text or email)&#x20;\
&#xNAN;_&#x41;cctHolderID:_ ( NOT USED )&#x20;\
&#xNAN;_&#x41;mount:_ ( payment amount )&#x20;\
&#xNAN;_&#x43;onsentID:_ ( NOT USED )&#x20;\
&#xNAN;_&#x44;ueOn:_ ( can be shown in message to indicate when payment is due  )\
&#xNAN;_&#x45;INDEX:_ ( can be used to indicate encrypted webhook )&#x20;\
&#xNAN;_&#x4D;erchID:_ ( Must provide a valid Merchant record index for the Account used )&#x20;\
&#xNAN;_&#x54;XID:_ (NOT USED)&#x20;\
&#xNAN;_&#x57;Type:_  ( use SW here )&#x20;\
&#xNAN;_&#x52;edirectURL:_  ( we can redirect to your site and pass realtime info after authorization )&#x20;\
&#xNAN;_&#x57;idgetURL:_ ( we will provide you the proper address fror your payment form )\
&#xNAN;_&#x45;xpiresOn:_ ( we can display the link expiration date within your message)&#x20;\
&#xNAN;_&#x53;ingleUse:_ ( enter a 1 to restrict the link to be used more than one time for payment )&#x20;\
&#xNAN;_&#x4F;ptParam:_ (this provides a means for us to configure and style the payment form)\
&#xNAN;_&#x51;uestions:_ ( NOT USED )&#x20;

#### Defining your Form&#x20;

The OPTPARAM field defines the payment form in terms of visible fields , readonly fields  , styles  and behavior.  We use a specific tool to generate this value found here  [https://easypay8.com/byowidget/](https://easypay8.com/byowidget/) .  You may select the options you desire then press GENERATE OPTPARAMS.  We are always glad to assist you with defining your form as this is a very important part of collecting payments. &#x20;

#### Sending a Custom TEXT Message&#x20;

here you can use the _MessageBody Field_ &#x20;

When sending a TEXT/SMS  , it is best to keep the message short and sweet. it is for this reason we have a DEFAULT message which you can use by simply leaving this field empty.&#x20;

we will simply pull a few details from your request such as&#x20;

MERCHANT NAME , AMOUNT , PAYMENT DUE DATE , LINK EXPIRATION

**The resulting text message will read as Follows**&#x20;

<sup>_You have a Payment Due to ( Merchant Name ) of (Amount) due on ( Due Date ) .  Follow the link below to make payment (Payment Link) This Link Expires on ( Exp Date )_</sup>&#x20;

If you decide to create your own message we will append the following to your message&#x20;

<sup>_Follow the link below to make payment (Payment Link) This Link Expires on ( Exp Date )_</sup>&#x20;

#### Sending a Custom EMAIL Message&#x20;

For the Email Option you must create a custom message. To help create your message we have provided some Variable fields: Please include the "||" characters.&#x20;

* ||Merch1||  when we see this in your message we will replace it with the actual Merchant name
* ||PayLink||  when we see this in your message we will replace it with the payment link
* ||DueOn||  when we see this we will replace it with the Date you specify for payment due date
* ||ExpOn||  when we see this we will replace it with the Date you specify for payment link expiration Date&#x20;

Here is an example Custom Message for EMAIL using the variables above

\<b>Dear John Doe,\</b>\<br />\<br />This is a friendly reminder that you have an outstanding balance of \<br /> $26.56 for your visit on 5/5/2026 with ||Merch1||. \<br />\<br />This payment is due on ||DueOn||. You can easily review your statement and submit your payment securely through our patient Portal \<br />\<br />Or you can also safely follow the link shown here.\<br />||PayLink||\<br/>This Link Expires on ||ExpOn||\<br />\<br />\<b>Thank You\<b>\<br/>||Merch1|| Billing Dept\</b>

&#x20; Here is the resulting email Message&#x20;

<figure><img src="../../../.gitbook/assets/image (24).png" alt=""><figcaption></figcaption></figure>



