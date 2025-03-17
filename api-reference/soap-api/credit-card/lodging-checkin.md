---
description: Methods related to lodging checkin
---

# Lodging Checkin

## Lodging Checkin - By ConsentID

<mark style="color:green;">`POST`</mark> /ICardProcess/LodgingCheckinByConsentID

Provide the details for a lodging checkin using an existing consent.

{% tabs %}
{% tab title="Request body" %}
***

***

`CheckInDetails` [api\_LodgingCheckInDetails](../soap-object-dictionary.md#api_lodgingcheckindetails) (object)

The details for the lodging checkin.

Fields: FirstName, LastName, AuthAmount, Folio, ArrivalDate, Duration, CustomerData, ServiceDescription, ClientRefID.

***
{% endtab %}

{% tab title="Response body" %}
***

***
{% endtab %}
{% endtabs %}



