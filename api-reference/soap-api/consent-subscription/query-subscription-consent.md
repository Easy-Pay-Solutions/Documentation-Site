---
description: Methods related to querying subscription consent
---

# Query Subscription Consent

## Query Subscription Consent - Full

<mark style="color:green;">`POST`</mark> /ICardProcess/ConsentSubscription\_FullDetail

Return the details for the consent, the card holder contact, and end customer information.

{% tabs %}
{% tab title="Request body" %}
***
{% endtab %}

{% tab title="Response body" %}
***

ConsentSubscription api\_ConsentSubscriptionFullDetailResponse (object)

Fields: ID, AcctHolderID, MerchID, CustID, AcctHolderLastName, AcctHolderFirstName, AcctNo, CustRefID, RPGUID, ServiceDescrip, Email, IsEnabled, CreatedOn, CreatedBy, CreatedOrigin, CreatedByID, ModifiedOn, ModifiedBy, ModifiedOrigin, ModifiedByID, RecurType, AuthTxID, RAmtPaidSoFar, RPeriod, StartDate, EndDate, PaymentAdjustDate, OnHold, RPaymentAmt.

***

***
{% endtab %}
{% endtabs %}



