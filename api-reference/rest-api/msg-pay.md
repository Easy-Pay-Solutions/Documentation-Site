---
description: Creates a payment link and sends it via SMS or email along with a message.
hidden: true
---

# Msg Pay

<mark style="color:orange;">post:</mark> https://easypay5.com/APIcardProcNumber/v1.0.0/Other/MsgPay

This call allows you to create a targeted payment link and send this along with a message to the party (or parties) of your choice.  Used in conjunction with our highly flexible [PayForm](https://docs.number.tech/documentation/getting-started/integration-options/payform) it can be used to collect a targeted amount from a specific party or to route funds for a general purpose or event. &#x20;

This API method allows users to accomplish three typical tasks:&#x20;

1. Send a SMS text with a message and Payment Link&#x20;
2. Send an email with message and Payment Link&#x20;
3. Acquire the Payment Link and use it internally or externally&#x20;

{% tabs %}
{% tab title="Sample Request" %}
```clike
{
   "MsgParams": {
    "MessageType": "SMS",
    "MessageBody": "",
    "MessageSubject": "OK Health",
    "DueOn": "1/7/2027",
    "ExpiresOn": "3/7/2027",
    "SingleUsage": 1
  },
  "InitParams": {
    "MerchID": 1,
    "WTYPE": "PF",
    "PostURL": "https://easypay7.com/swidget/JsonGet.aspx",
    "RedirectURL": "https://easypay8.com/CYWidget/",
    "REF_ID": "A97689#",
    "RPGUID": "92e1e15c-f64a-466b-8733-9b518b9f374c",
    "EndPoint": "PF",
    "EINDEX": "300",
    "Amounts": {
      "Amount": 20,
      "Surcharge": 0,
      "TotalAmt": 20
    },
    "Payer": {
      "Firstname": "John",
      "Lastname": "Doe",
      "BillingAddress": {
        "StreetAddress": "123 Elm St",
        "City": "Tulsa",
        "State": "OK",
        "ZIP": "84048",
        "Country": "USA"
      }, 
      "Email": "Jdoe@acme.net", 
      "Phone": "6078595025",
      "Company": ""
    },
    "WidOptions": {
      "eVisible": "0665",
      "eReadOnly": "0040",
      "eStyles": "0001",
      "eSubmission": "0A01",
      "eFeatures": "0000",
      "eColors": "#ffffff,#428bca,#007bff,#212121,#ffffff,#212121,#ffffff"
    }
  }
} 
```
{% endtab %}

{% tab title="Sample Response" %}
```clike
{
  "SMSPaymentResult": {
    "ErrCode": 0,
    "ErrMsg": "",
    "FunctionOk": true,
    "PaymentUrl": null,
    "RespMsg": "Text Sent Successfully to 2078995025"
  }
}
```
{% endtab %}

{% tab title="Header Parameters" %}
**SessKey** string <mark style="color:orange;">required</mark>

A unique session key used for authentication in API calls. This key is generated upon successful authentication and must be included in all subsequent requests.

Example: `A1842D663E9A4A72XXXXXXXX303541303234373138`

***

**Content-Type** string <mark style="color:orange;">required</mark>

Example: `application/json`

***

**Accept** string <mark style="color:orange;">required</mark>

Example: `application/json`
{% endtab %}
{% endtabs %}

