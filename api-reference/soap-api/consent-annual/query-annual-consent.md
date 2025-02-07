---
description: Methods related to querying annual consent
---

# Query Annual Consent

## Query Annual Consent

<mark style="color:green;">`POST`</mark> /ICardProcess/ConsentAnnual\_Query

Return annual consent details.&#x20;

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

`Consents` List\<api\_ConsentAnnual> (array\<object>)

A list of relevant consent records.

Fields: ID, AcctHolderID, CustID, MerchID, CustomerRefID, RPGUID, ServiceDescrip, AcctHolderLastName, AcctHolderFirstName, IsEnabled, StartDate, EndDate, NumDays, LimitPerCharge, LimitLifeTime, AuthTxID, CreatedOn, CreatedBy, AcctNo.&#x20;
{% endtab %}
{% endtabs %}





## Query Annual Consent - Stats

<mark style="color:green;">`POST`</mark> /ICardProcess/ConsentAnnual\_Stats

Return statistics for a single consent such as the number of charges or open and settled amounts.

{% tabs %}
{% tab title="Request body" %}
{% include "../../../.gitbook/includes/param-sess-key.md" %}

***

{% include "../../../.gitbook/includes/param-consent-id.md" %}
{% endtab %}

{% tab title="Response body" %}
{% include "../../../.gitbook/includes/param-ok-msg-errs.md" %}

***

`Stats` api\_ConsentAnnualStats (object)

Fields: FirstChargeAttempt, ID, IsEnabled, LastChargeAmount, LastChargeAttempt, LastSettledAmount, LimitLifeTime, NumChargeAttempts, NumFailed, NumFailedAttempts, NumOpen, NumSettled, NumTx, RemainingInConsent, TotalDollarsOpen, TotalDollarsSettled.
{% endtab %}
{% endtabs %}





## Query Annual Consent - Full

<mark style="color:green;">`POST`</mark> /ICardProcess/ConsentAnnual\_FullDetail

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

`ConsentAnnual` api\_ConsentAnnualFullDetailResponse (object)

Fields: ID, AcctHolderID, CustID, MerchID, CustomerRefID, RPGUID, ServiceDescrip, AcctHolderLastName, AcctHolderFirstName, IsEnabled, StartDate, EndDate, NumDays, LimitPerCharge, LimitLifeTime, AuthTxID, CreatedOn, CreatedBy, AcctNo.&#x20;

***

{% include "../../../.gitbook/includes/param-account-holder-full.md" %}

***

{% include "../../../.gitbook/includes/param-end-customer-full.md" %}
{% endtab %}
{% endtabs %}



