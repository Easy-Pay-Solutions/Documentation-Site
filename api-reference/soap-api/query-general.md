---
description: Methods related querying general information such as enum values
---

# Query General

## Query Decline Codes

<mark style="color:green;">`POST`</mark> /ICardProcess/DeclineCodeQry

Return a list of decline codes.

{% tabs %}
{% tab title="Request body" %}
{% include "../../.gitbook/includes/param-sess-key.md" %}
{% endtab %}

{% tab title="Response body" %}
{% include "../../.gitbook/includes/param-ok-msg-errs.md" %}

***

`DeclineCodes` List\<api\_DeclineCodes> (array\<object>)

Fields: DeclCode, RespMsg, RespDef, CustMsg.
{% endtab %}
{% endtabs %}

***

## Query Enums

<mark style="color:green;">`POST`</mark> /ICardProcess/Enum\_Query

Return a list of enum items in the system.

{% tabs %}
{% tab title="Request body" %}
{% include "../../.gitbook/includes/param-sess-key.md" %}

***

{% include "../../.gitbook/includes/param-query.md" %}
{% endtab %}

{% tab title="Response body" %}
{% include "../../.gitbook/includes/param-ok-msg-errs.md" %}

***

`EnumItems` List\<api\_EnumItem>

Fields: EnumText, EnumValue.
{% endtab %}
{% endtabs %}

***

## Query Lodging Enums

<mark style="color:green;">`POST`</mark> /ICardProcess/Enum\_QueryLodging

Return a list of lodging-related enum items in the system.

{% tabs %}
{% tab title="Request body" %}
{% include "../../.gitbook/includes/param-sess-key.md" %}

***

{% include "../../.gitbook/includes/param-query.md" %}
{% endtab %}

{% tab title="Response body" %}
{% include "../../.gitbook/includes/param-ok-msg-errs.md" %}

***

`EnumItems` List\<api\_EnumItem>

Fields: EnumText, EnumValue.
{% endtab %}
{% endtabs %}
