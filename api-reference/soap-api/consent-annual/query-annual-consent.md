---
description: Methods related to querying annual consent
---

# Query Annual Consent

## Query Annual Consent

<mark style="color:green;">`POST`</mark> /ICardProcess/ConsentAnnual\_Query

Return annual consent details.&#x20;

{% tabs %}
{% tab title="Request body" %}
***
{% endtab %}

{% tab title="Response body" %}
***

***

`Consents` List<[api\_ConsentAnnual](../soap-object-dictionary.md#api_consentannual)> (array\<object>)

A list of relevant consent records.

Fields: ID, AcctHolderID, CustID, MerchID, CustomerRefID, RPGUID, ServiceDescrip, AcctHolderLastName, AcctHolderFirstName, IsEnabled, StartDate, EndDate, NumDays, LimitPerCharge, LimitLifeTime, AuthTxID, CreatedOn, CreatedBy, AcctNo.&#x20;
{% endtab %}
{% endtabs %}





## Query Annual Consent - Stats

<mark style="color:green;">`POST`</mark> /ICardProcess/ConsentAnnual\_Stats

Return statistics for a single consent such as the number of charges or open and settled amounts.

{% tabs %}
{% tab title="Request body" %}
***
{% endtab %}

{% tab title="Response body" %}
***

`Stats` [api\_ConsentAnnualStats](../soap-object-dictionary.md#api_consentannualstats) (object)

Fields: ID, IsEnabled, NumChargeAttempts, NumFailedAttempts, FirstChargeAttempt, LastChargeAttempt, TotalDollarsSettled, TotalDollarsOpen, LastSettledAmount, LastChargeAmount, RemainingInConsent, NumTx, NumSettled, NumFailed, NumOpen, LimitLifeTime.
{% endtab %}
{% endtabs %}





## Query Annual Consent - Full

<mark style="color:green;">`POST`</mark> /ICardProcess/ConsentAnnual\_FullDetail

Return the details for the consent, the card holder contact, and end customer information.

{% tabs %}
{% tab title="Request body" %}
***
{% endtab %}

{% tab title="Response body" %}
***

`ConsentAnnual` api\_ConsentAnnualFullDetailResponse (object)

Fields: ID, AcctHolderID, CustID, MerchID, CustomerRefID, RPGUID, ServiceDescrip, AcctHolderLastName, AcctHolderFirstName, IsEnabled, StartDate, EndDate, NumDays, LimitPerCharge, LimitLifeTime, AuthTxID, CreatedOn, CreatedBy, AcctNo.&#x20;

***

***
{% endtab %}
{% endtabs %}



