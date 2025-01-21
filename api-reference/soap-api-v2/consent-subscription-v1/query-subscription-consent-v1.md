---
description: Methods related to querying subscription consent
---

# Query Subscription Consent (v1)

## Query Subscription Consent - Full

<mark style="color:green;">`POST`</mark> /ICardProcess/ConsentSubscription\_FullDetail

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

ConsentSubscription api\_ConsentSubscriptionFullDetailResponse (object)

Fields: ID, AcctHolderID, MerchID, CustID, AcctHolderLastName, AcctHolderFirstName, AcctNo, CustRefID, RPGUID, ServiceDescrip, Email, IsEnabled, CreatedOn, CreatedBy, CreatedOrigin, CreatedByID, ModifiedOn, ModifiedBy, ModifiedOrigin, ModifiedByID, RecurType, AuthTxID, RAmtPaidSoFar, RPeriod, StartDate, EndDate, PaymentAdjustDate, OnHold, RPaymentAmt.

***

{% include "../../../.gitbook/includes/param-account-holder-full.md" %}

***

{% include "../../../.gitbook/includes/param-end-customer-full.md" %}
{% endtab %}
{% endtabs %}

