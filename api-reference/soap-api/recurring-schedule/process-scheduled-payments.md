---
description: Methods related to processing recurring schedules
---

# Process Scheduled Payments

## Process Scheduled Payments

<mark style="color:green;">`POST`</mark> /ICardProcess/ProcessScheduledPayments

Process the scheduled payments that are due as part of a subscription plan/recurring consent. Return approved and declined transactions. All of the due payments that are associated with the specified merchant are processed.

{% tabs %}
{% tab title="Request body" %}
***
{% endtab %}

{% tab title="Response body" %}
***

`NumProcessed` int

The total number of processed payments.

***

`NumApproved` int

The number of approved payments.

***

`NumDeclined` int

The number of declined payments.

***

`NumPartialAuths` int

The number of payments that got partial authorization.

***

`ApprovedPayments` List\<api\_RecurringPayment> (array\<object>)

Fields: ConsentID, MerchID, SchedNum, SchedID, TxID, TxApproved, IsPartialApproval, TxnCode, PaymentAmt, PaymentNum, AcctNo, SEQ, CardHolder, CardType, PaymentDate, ConsentType, ErrMsg.

***

`DeclinedPayments` List\<api\_RecurringPayment> (array\<object>)

Fields: ConsentID, MerchID, SchedNum, SchedID, TxID, TxApproved, IsPartialApproval, TxnCode, PaymentAmt, PaymentNum, AcctNo, SEQ, CardHolder, CardType, PaymentDate, ConsentType, ErrMsg.
{% endtab %}
{% endtabs %}





## Process Scheduled Payments - Selective

<mark style="color:green;">`POST`</mark> /ICardProcess/ProcessScheduledPaymentsSelective

Process the scheduled payments that are due as part of a subscription plan/recurring consent. Return approved and declined transactions. Only the payments specified by ScheduleID are processed.

{% tabs %}
{% tab title="Request body" %}
***

`SchedIDs` array\<int>

IDs of the schedules to process.
{% endtab %}

{% tab title="Response body" %}
***

`NumProcessed` int

The total number of processed payments.

***

`NumApproved` int

The number of approved payments.

***

`NumDeclined` int

The number of declined payments.

***

`NumPartialAuths` int

The number of payments that got partial authorization.

***

`ApprovedPayments` List\<api\_RecurringPayment> (array\<object>)

Fields: ConsentID, MerchID, SchedNum, SchedID, TxID, TxApproved, IsPartialApproval, TxnCode, PaymentAmt, PaymentNum, AcctNo, SEQ, CardHolder, CardType, PaymentDate, ConsentType, ErrMsg.

***

`DeclinedPayments` List\<api\_RecurringPayment> (array\<object>)

Fields: ConsentID, MerchID, SchedNum, SchedID, TxID, TxApproved, IsPartialApproval, TxnCode, PaymentAmt, PaymentNum, AcctNo, SEQ, CardHolder, CardType, PaymentDate, ConsentType, ErrMsg.
{% endtab %}
{% endtabs %}
