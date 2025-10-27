---
description: Generate a receipt for an international transaction
---

# International

<mark style="color:orange;">post:</mark> https://easypay5.com/APIcardProcREST/v1.0.0/Intl/ReceiptGenerate

REFID will be the transaction ID\
ReceiptType will always be 23 for International\
Merchant copy use Recipient = 1\
Customer Copy use Recipient = 2\
For Dual Receipt use Recipient = 3

**Consuming the Response**\
The member named ReceiptHtml holds the receipt data\
Important you must replace all Unicode characters to consume clean HTML\
Example : CleanHtml = Regex.Replace(my, @"\[^\u0000-\u007F]+", string.Empty);

{% tabs %}
{% tab title="Sample Request" %}
```clike
{
  "REFID": "5eef4782-5be1-11ef-bbc1-46647bd59a7a",
  "ReceiptType": 23,
  "Recipient": 1
}
```
{% endtab %}

{% tab title="Sample Response" %}
```clike
{
  "Intl_ReceiptGenerateResult": {
    "ErrCode": 0,
    "ErrMsg": "",
    "FunctionOk": true,
    "ReceiptHtml": "HTML",
    "RespMsg": "Successfully Returned Transaction Receipt Markup"
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
**REFID** string <mark style="color:purple;">optional</mark>

The transaction ID

Example: `5eef4782-5be1-11ef-bbc1-46647bd59a7a`

***

**ReceiptType** integer <mark style="color:purple;">optional</mark>

The type of receipt, 23 for international

Example: `23`

***

**Recipient** integer · enum <mark style="color:purple;">optional</mark>

The targeted recipient type

* 1: Merchant
* 2: Customer
* 3: Both

Example: `1`
{% endtab %}
{% endtabs %}

