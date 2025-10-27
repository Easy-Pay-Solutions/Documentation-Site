---
description: Create a payment link via SMS or email
---

# Text to Pay

<mark style="color:orange;">post:</mark> https://easypay5.com/APIcardProcREST/v1.0.0/Other/SMSPay

This call allows you to create a tinyURL of the widget payment link that will display a message and payment form to the customer. The message and form that is displayed to the customer is easily configured by using the API call options.

This API method allows users to accomplish three typical tasks:

1. Send a SMS text with a message and Payment Link
2. Send an email with message and Payment Link
3. Acquire the Payment Link and use it internally or externally

For more details on the use of Text to Pay as well as some sample code is available on our documentation site located at [https://easypaysoftware.com/en/text-to-pay](https://easypaysoftware.com/en/text-to-pay).

{% tabs %}
{% tab title="Sample Request" %}
```clike
{
  "Msg": {
    "Person": {
      "Firstname": "EasyPay",
      "Lastname": "Tester",
      "Company": "",
      "Title": "",
      "Url": "",
      "BillIngAdress": {
        "Address1": "123 Fake St.",
        "Address2": "",
        "City": "Portland",
        "State": "ME",
        "ZIP": "04106",
        "Country": "USA"
      },
      "Email": "testing@here.com",
      "Phone": "2076885025"
    },
    "MessageType": "TEXT",
    "RefID": "52520ABC",
    "RPGUID": "4c269391-a698-4e10-a1a8-0353ee80d1a6",
    "MessageBody": "",
    "AcctHolderID": 0,
    "Amount": 50,
    "ConsentID": 0,
    "DueOn": "1/12/2025",
    "EINDEX": "100",
    "MerchID": 1,
    "TXID": 0,
    "WType": "SW",
    "RedirectURL": "https://easypay7.com/PostingApp",
    "WidgetURL": "https://easypay5.com/stdwidget",
    "ExpiresOn": "2025-10-05T00:00:00.000Z",
    "SingleUse": 0,
    "OptParam": "VISIBLE|1EE7|READONLY|0000|STYLES|0000|OPTIONS|0601|COLORS|#ffffff,#428bca,#007bff,#212121,#ffffff,#212121,#ffffff",
    "Questions": []
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

{% tab title="Body" %}
**Msg**&#x20;object <mark style="color:purple;">optional</mark>
{% endtab %}
{% endtabs %}

