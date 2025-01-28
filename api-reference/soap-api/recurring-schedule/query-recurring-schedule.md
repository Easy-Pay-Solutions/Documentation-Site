---
description: Methods related to querying recurring schedules
---

# Query Recurring Schedule

## Query Scheduled Payments

<mark style="color:green;">`POST`</mark> /ICardProcess/RecurringSchedule\_Query

Return the recurring schedule details.

{% tabs %}
{% tab title="Request body" %}
{% include "../../../.gitbook/includes/param-sess-key.md" %}

***

{% include "../../../.gitbook/includes/param-query-recurring-schedule.md" %}
{% endtab %}

{% tab title="Response body" %}
{% include "../../../.gitbook/includes/param-ok-msg-errs.md" %}

***

{% include "../../../.gitbook/includes/param-num-records.md" %}

***

`Schedule` List\<api\_RecurringSchedLine> (array\<object>)

Fields: ID, ConsentID, MerchID, AcctHolderID, SchedNum, DueOn, PaymentNum, OfTotalPayments, PaymentAmt, OfTotalPayment,  Period, RStatus, TxID, Tries, AcctNo, LastName, RPGUID, ConsentType.
{% endtab %}
{% endtabs %}

