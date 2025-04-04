---
description: Methods related to all types of consent
---

# Consent General

## Query Consent

<mark style="color:green;">`POST`</mark> /ICardProcess/ConsentGeneral\_Query

Return consent details.

{% tabs %}
{% tab title="Request body" %}
***
{% endtab %}

{% tab title="Response body" %}
***

***
{% endtab %}
{% endtabs %}





## Query Expiring Cards - Before/In Days

<mark style="color:green;">`POST`</mark> /ICardProcess/ConsentsExpiringCards

Find expired cards and cards expiring before/in the specified number of days used on consents.&#x20;

{% tabs %}
{% tab title="Request body" %}
***

`NumDays` int

Number of days in the future to look for expiring cards.
{% endtab %}

{% tab title="Response body" %}
***

***
{% endtab %}
{% endtabs %}





## Query Expiring Cards - In Date Range

<mark style="color:green;">`POST`</mark> /ICardProcess/ConsentsExpiringCards\_01

Find expired cards and cards expiring during the specified range of dates used on consents.&#x20;

{% tabs %}
{% tab title="Request body" %}
***

`StartDate` string

Start date of the consent expiring cards range.

***

`EndDate` string

End date of the consent expiring cards range.
{% endtab %}

{% tab title="Response body" %}
***

***
{% endtab %}
{% endtabs %}

