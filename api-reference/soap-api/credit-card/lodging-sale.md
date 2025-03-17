---
description: Methods related to lodging sales
---

# Lodging Sale

## Lodging Sale - Card Present

<mark style="color:green;">`POST`</mark> /ICardProcess/LodgingSale\_CardPres

Process a lodging reservation that authorizes the card prior to guest checkin and arrival. This version of the LodgingSale uses a credit card reader device to send card track data to the provider.

{% tabs %}
{% tab title="Request body" %}
***

***

***

***

***
{% endtab %}

{% tab title="Response body" %}
***

***

***

***

***

***
{% endtab %}
{% endtabs %}





## Lodging Sale - Manual

<mark style="color:green;">`POST`</mark> /ICardProcess/LodgingSale\_Manual

Process a lodging reservation that authorizes the card prior to guest checkin and arrival. This version of the LodgingSale uses manual card entry to transmit the credit card data.

{% tabs %}
{% tab title="Request body" %}
***

***

***

***

`LodgingDetails` [api\_LodgingDetails](../soap-object-dictionary.md#api_lodgingdetails) (object)

Fields: FirstName, LastName, IsAuthOnly, ConsentID4Auth, Folio, ArrivalDate, DepartureDate, Duration, ChangeDescriptor[^1], ChargeAmount, ExtraChargeAmount, ExtraChargesCode[^2], SaleCode[^3], StayID, CustomerData

***
{% endtab %}

{% tab title="Response body" %}
***

***

***

***

***

***
{% endtab %}
{% endtabs %}





## Lodging Sale - By Consent

<mark style="color:green;">`POST`</mark> /ICardProcess/LodgingSale\_ByConsent

Process a lodging reservation using an existing consent instead of processing a new credit card.

{% tabs %}
{% tab title="Request body" %}
***

***

***
{% endtab %}

{% tab title="Response body" %}
***

***

***

***

***

***
{% endtab %}
{% endtabs %}





## Lodging Sale - By Consent (Explicit)

<mark style="color:green;">`POST`</mark> /ICardProcess/LodgingSale\_ByConsent\_Exp

Process a lodging reservation using an existing consent and specify the data entry person.&#x20;

{% tabs %}
{% tab title="Request body" %}
***

***

***

`UserOperator` string

Identity of the data entry person.

***
{% endtab %}

{% tab title="Response body" %}
***

***

***

***

***

***
{% endtab %}
{% endtabs %}





[^1]: Values:\
    \- 0 (cdHealthClub)\
    \- 1 (cdLodging)\
    \- 2 (cdRestaurant)\
    \- 3 (cdGiftShop)\
    \- 4 (cdHairSalon)\
    \- 5 (cdConventionFees)\
    \- 6 (cdTennisClub)\
    \- 7 (cdGolfShop)

[^2]: Values:\
    \- 0 (ecNone)\
    \- 2 (ecRestaurant)\
    \- 3 (ecGiftShop)\
    \- 4 (ecMiniBar)\
    \- 5 (ecTelephone)\
    \- 6 (ecOther)\
    \- 7 (ecLaundry)

[^3]: Values:\
    \- 0 (scNotSet)\
    \- 1 (scSale)\
    \- 2 (scNoShow)\
    \- 3 (scDeposit)\
    \- 4 (scDelayedCharge)\
    \- 5 (scExpressService)\
    \- 6 (scAssuredReservation)
