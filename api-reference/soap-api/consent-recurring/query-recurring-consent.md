---
description: Methods related to querying subscription consent
---

# Query Recurring Consent

## Query Recurring Consent

<mark style="color:green;">`POST`</mark> /ICardProcess/ConsentRecurring\_Query

Return recurring consent details.

{% tabs %}
{% tab title="Request body" %}
{% include "../../../.gitbook/includes/param-sess-key.md" %}

***

{% include "../../../.gitbook/includes/param-query-consent.md" %}
{% endtab %}

{% tab title="Response body" %}
{% include "../../../.gitbook/includes/param-ok-msg-errs.md" %}

***

{% include "../../../.gitbook/includes/param-num-records.md" %}

***

`Consents` List\<api\_ConsentRecurring> (array\<object>)

Fields: ID, AcctHolderID, MerchID, CustID, AcctHolderLastName, AcctHolderFirstName, AcctNo, CustRefID< RPGUID, ServiceDescrip, IsEnabled, CreatedOn, CreatedBy, ModifiedOn, ModifiedBy, AuthTxID, RTotalAmt, RAmtPaidSoFar, RNumPayments, RPeriod, StartDate, EndDate, RPaymentAmt, RLastPaymentAmt.
{% endtab %}
{% endtabs %}

***

## Query Recurring Consent - Full

<mark style="color:green;">`POST`</mark> /ICardProcess/ConsentRecurring\_FullDetail

Return the details for the consent, the card holder contact, and end customer information.

{% tabs %}
{% tab title="Request body" %}
{% include "../../../.gitbook/includes/param-sess-key.md" %}

***

{% include "../../../.gitbook/includes/param-consent-id.md" %}
{% endtab %}

{% tab title="Response body" %}
{% include "../../../.gitbook/includes/param-ok-msg-errs.md" %}

***

`ConsentRecurring` api\_ConsentRecurring \<object>

Fields: ID, AcctHolderID, MerchID, CustID, AcctHolderLastName, AcctHolderFirstName, AcctNo, CustRefID< RPGUID, ServiceDescrip, IsEnabled, CreatedOn, CreatedBy, ModifiedOn, ModifiedBy, AuthTxID, RTotalAmt, RAmtPaidSoFar, RNumPayments, RPeriod, StartDate, EndDate, RPaymentAmt, RLastPaymentAmt.

***

{% include "../../../.gitbook/includes/param-account-holder-full.md" %}

***

{% include "../../../.gitbook/includes/param-end-customer-full.md" %}
{% endtab %}
{% endtabs %}

