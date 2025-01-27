---
description: Methods related to lodging checkin
---

# Lodging Checkin

## Lodging Checkin - By ConsentID

<mark style="color:green;">`POST`</mark> /ICardProcess/LodgingCheckinByConsentID

Provide the details for a lodging checkin using an existing consent.

{% tabs %}
{% tab title="Request body" %}
{% include "../../../.gitbook/includes/param-sess-key.md" %}

***

{% include "../../../.gitbook/includes/param-consent-id.md" %}

***

`CheckInDetails` [api\_LodgingCheckInDetails](../soap-object-dictionary.md#api_lodgingcheckindetails) (object)

The details for the lodging checkin.

Fields: FirstName, LastName, AuthAmount, Folio, ArrivalDate, Duration, CustomerData, ServiceDescription, ClientRefID.

***

{% include "../../../.gitbook/includes/param-merchid.md" %}
{% endtab %}

{% tab title="Response body" %}
{% include "../../../.gitbook/includes/param-ok-msg-errs.md" %}

***

{% include "../../../.gitbook/includes/param-tx-approved.md" %}

***

{% include "../../../.gitbook/includes/param-txid.md" %}
{% endtab %}
{% endtabs %}

