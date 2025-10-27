---
description: Generate a transaction receipt
---

# Receipt

<mark style="color:orange;">post:</mark> https://easypay5.com/APIcardProcREST/v1.0.0/Receipt/ReceiptGenerate

Use this call to request receipt details in HTML format for a particular TXID (Transaction ID). This method works for card on file documents as well as transaction receipts. You will need the TXID (Transaction ID) as well as a receipt type and a targeted recipient ( Customer or Merchant ).

The following will provide a customer receipt for TXID 123:

{ "REFID": 123, "ReceiptType": 1 (Sales Receipt) "Recipient": 1 (Customer Copy) }

Important you must replace all Unicode characters to consume clean HTML

Example : CleanHtml = Regex.Replace(my, @"\[^\u0000-\u007F]+", string.Empty);

{% tabs %}
{% tab title="Sample Request" %}
```clike
{
  "REFID": 158,
  "ReceiptType": 1,
  "Recipient": 1
}
```
{% endtab %}

{% tab title="Sample Response" %}
```clike
{
  "ReceiptGenerateResult": {
    "ErrCode": 0,
    "ErrMsg": "",
    "FunctionOk": true,
    "ReceiptHtml": "html",
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
**REFID** integer <mark style="color:purple;">optional</mark>

The unique reference identifier for the transaction

Example: `158`

***

**ReceiptType** integer · enum <mark style="color:purple;">optional</mark>

The type of receipt

* 1: Transaction
* 2: Void
* 3: Refund
* 4: Annual Consent
* 5: Recurring Consent
* 6: Subscription
* 7: ACH Transaction
* 8: ACH Void
* 9: ACH Refund

Example: `2`

***

**Recipient** integer · enum <mark style="color:purple;">optional</mark>

The targeted recipient type

* 1: Merchant
* 2: Customer
* 3: Both

Example: `1`
{% endtab %}
{% endtabs %}
