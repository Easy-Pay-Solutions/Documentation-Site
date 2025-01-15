---
description: Methods related to the user account
---

# Account (v1)

## Account Profile Query

<mark style="color:green;">`POST`</mark> /ICardProcess/AccountProfileQry

Get information about the logged-in user, such as: account code, name, settlement details, account creation and modification dates.

{% tabs %}
{% tab title="Request body" %}
{% include "../../.gitbook/includes/param-sess-key.md" %}
{% endtab %}

{% tab title="Response body" %}
{% include "../../.gitbook/includes/param-ok-msg-errs.md" %}

***

`AccountProfile` [api\_AccountProfile](soap-object-dictionary-wip.md#api_accountprofile) (object)

Information about the user profile.

Fields: ID, AccountName, AccountCode, AutoSettle, AutoSchedule, AutoSettleHour, AutoSettleMinute, BatchReport, TransReport, DateCreated, DateModified, IndustryCode, TimeZone
{% endtab %}
{% endtabs %}

***

## Account Settings Query

<mark style="color:green;">`POST`</mark> /ICardProcess/AccountSettingsQry

Get individual settings and their values configured for the logged-in user.

{% tabs %}
{% tab title="Request body" %}
{% include "../../.gitbook/includes/param-sess-key.md" %}
{% endtab %}

{% tab title="Response body" %}
{% include "../../.gitbook/includes/param-ok-msg-errs.md" %}

***

`AcctSettings` List<[api\_AccountSettings](soap-object-dictionary-wip.md#api_accountsettings)> (array\<object>)

An array of values for user settings.

Fields: sKey, sValue, sOptions, sGroup
{% endtab %}
{% endtabs %}
