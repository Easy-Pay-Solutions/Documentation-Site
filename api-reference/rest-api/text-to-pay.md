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

The method name is **SMSPayment**: api\_SMSPaymentResponse SMSPayment(string SessKey, api\_SMSPayment PaymentObject);

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

{% tab title="Sample Code" %}


In order to use this method you will need to populate the following object:

```csharp
public class api_SMSPayment
{
        public api_Person Person { get; set; }
        public string MessageType { get; set; }
        public string RefID { get; set; }
        public string RPGUID { get; set; }
        public string MessageBody { get; set; }
        public int AcctHolderID { get; set; }
        public decimal Amount { get; set; }
        public int ConsentID { get; set; }
        public DateTime DueOn { get; set; }
        public string EINDEX { get; set; }
        public int MerchID { get; set; }
        public int TXID { get; set; }
        public string WType { get; set; }
        public string RedirectURL { get; set; }
        public string WidgetURL { get; set; }
        public string ExpiresOn { get; set; }
        public bool SingleUse { get; set; }
        public string OptParam { get; set; }

        public List <api_Question> Questions { get; set; }

        public api_SMSPayment()
        {
            Person = new api_Person();
            Questions = new List <api_Question>();

        }
    }

```

\
Below is a list of the members and a brief explanation:

1. **Person**\
   Use this object to populate the name, address, email and phone number for the Payee.
2. **MessageType**\
   This will be EMAIL or URLONLY or TEXT.
3. **RefID**\
   Your user defined field.
4. **RPGUID**\
   Another User Defined Field
5. **MessageBody**\
   If you send an empty string then a generic message will be sent as follows:
   * _You have a Payment Due to \[Merchant Name] of \[Amount] due on \[DueOn]. Please follow the link below to make the Payment. \[Link Here]_
   * If you send your own message the payment link will appear just below your message.
   * _If you want the proper Merchant name to show up in your custom message then place the following in your message:_ **\*\*Merch1\*\***
   * _We will replace that text with the proper merchant's name._
6. **AcctHolderID**\
   (not used please fill with Zero)
7. **Amount**\
   This is the payment amount you need to collect
8. **ConsentID**\
   (not used please fill with Zero)
9. **DueOn**\
   Payment due date
10. **EINDEX**\
    This is your Integrator Key Index for encryption (example 100 or 200 or 302)
11. **MerchID**\
    Your integer index for the merchant record for the account
12. **TXID**\
    (not used please fill with Zero)
13. **WType**\
    This specifies which payment widget to display (example SMSPN);
14. **RedirectURL**\
    This specifies where we will post the results of the transaction
15. **WidgetURL**\
    Here is the endpoint for the widget transaction. EasyPay will guide you here but you can start with this: [https://easypay5.com/stdwidget/](https://easypay5.com/stdwidget/)
16. **ExpiresOn**\
    This will allow you to provide a date for when the payment link should no longer be available
17. **SingleUse**\
    Provide a true or false indicating whether the payment link should only accept a single payment
18. **OptParams**\
    Here we can supply parameters which control the design and behavior of the payment form
{% endtab %}
{% endtabs %}

