---
description: Methods related to creating and modifying recurring consent
---

# Consent Recurring

## Create Recurring Consent

<mark style="color:green;">`POST`</mark> /ICardProcess/ConsentRecurring\_Create

Creates a recurring consent. Depending upon user account settings, this also authorize the card for $0.

{% tabs %}
{% tab title="Request body" %}
***

`ccCardInfo` api\_CardInfo2 (object)

Fields: AccountNumber, ExpMonth, ExpYear, CSV, Track

***

`ConsentCreator` api\_ConsentRecurringCreator (object)

Fields: MerchID, CustomerRefID, ServiceDescrip, RPGUID, StartDate, NumPayments, TotalAmount, Period

***

***
{% endtab %}

{% tab title="Response body" %}
***

***

***

`MySched` List\<api\_SchedLine> (array\<object>)

Fields: SchedID, paymentNo, paymentAmt, paymentDate, Remaining
{% endtab %}
{% endtabs %}





## Modify Recurring Consent

<mark style="color:green;">`POST`</mark> /ICardProcess/ConsentRecurring\_Modify

Update the payment amounts, expiration, and customer reference information for a recurring consent. Does not alter the credit card saved with the consent.

{% tabs %}
{% tab title="Request body" %}
***

***

`ConsentMods` api\_ConsentRecurringEditor (object)

Fields: ExpMonth, ExpYear, Email, Zip, CustomerRefID, ServiceDescrip, RPGUID
{% endtab %}

{% tab title="Response body" %}
***
{% endtab %}
{% endtabs %}





## Cancel Recurring Consent

<mark style="color:green;">`POST`</mark> /ICardProcess/ConsentRecurring\_Cancel

Cancel a recurring consent and remove credit card data from the system.

{% tabs %}
{% tab title="Request body" %}
***


{% endtab %}

{% tab title="Response body" %}
***
{% endtab %}
{% endtabs %}



