---
description: Methods related querying general information such as enum values
---

# Query General

## Query Decline Codes

<mark style="color:green;">`POST`</mark> /ICardProcess/DeclineCodeQry

Return a list of decline codes.

{% tabs %}
{% tab title="Request body" %}

{% tab title="Response body" %}
***

`DeclineCodes` List\<api\_DeclineCodes> (array\<object>)

Fields: DeclCode, RespMsg, RespDef, CustMsg.
{% endtab %}
{% endtabs %}





## Query Enums

<mark style="color:green;">`POST`</mark> /ICardProcess/Enum\_Query

Return a list of enum items in the system.

{% tabs %}
{% tab title="Request body" %}
***

`Query` string

The enumeration type to query.

Values:\
\- "ACHSttatus"\
\- "ACHType"\
\- "AConsentType"\
\- "BatchSettleMode"\
\- "BatchSettleStatus"\
\- "ConsentType"\
\- "IntAction"\
\- "IntlAction"\
\- "IntlResult"\
\- "IntlStatus"\
\- "Period"\
\- "ReceiptType"\
\- "Recipient"\
\- "RecurSchedStatus"\
\- "TxStatus"\
\- "TxType"
{% endtab %}

{% tab title="Response body" %}
***

`EnumItems` List\<api\_EnumItem>

Fields: EnumText, EnumValue.
{% endtab %}
{% endtabs %}





## Query Lodging Enums

<mark style="color:green;">`POST`</mark> /ICardProcess/Enum\_QueryLodging

Return a list of lodging-related enum items in the system.

{% tabs %}
{% tab title="Request body" %}
***

`Query` string

The enumeration type to query, specific to lodging.
{% endtab %}

{% tab title="Response body" %}
***

`EnumItems` List\<api\_EnumItem>

Fields: EnumText, EnumValue.
{% endtab %}
{% endtabs %}



