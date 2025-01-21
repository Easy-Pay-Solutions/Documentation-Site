---
description: Methods related to lodging sales
---

# Lodging Sale (v1)

## Lodging Sale - Card Present

<mark style="color:green;">`POST`</mark> /ICardProcess/LodgingSale\_CardPres

Process a lodging reservation that authorizes the card prior to guest checkin and arrival. This version of the LodgingSale uses a credit card reader device to send card track data to the provider.

{% tabs %}
{% tab title="Request body" %}
{% include "../../../.gitbook/includes/param-sess-key.md" %}

***

{% include "../../../.gitbook/includes/param-track.md" %}

***

{% include "../../../.gitbook/includes/param-account-holder.md" %}

***

{% include "../../../.gitbook/includes/param-end-customer.md" %}

***

{% include "../../../.gitbook/includes/param-lodging-details.md" %}

***

{% include "../../../.gitbook/includes/param-merchid.md" %}
{% endtab %}

{% tab title="Response body" %}
{% include "../../../.gitbook/includes/param-ok-msg-errs.md" %}

***

{% include "../../../.gitbook/includes/param-tx-approved.md" %}

***

{% include "../../../.gitbook/includes/param-txid.md" %}

***

{% include "../../../.gitbook/includes/param-txncode.md" %}

***

{% include "../../../.gitbook/includes/param-avsr.md" %}

***

{% include "../../../.gitbook/includes/param-cvvr.md" %}

***

{% include "../../../.gitbook/includes/params-acquirer-opts-voice-opts-auth-balance.md" %}
{% endtab %}
{% endtabs %}

***

## Lodging Sale - Manual

<mark style="color:green;">`POST`</mark> /ICardProcess/LodgingSale\_Manual

Process a lodging reservation that authorizes the card prior to guest checkin and arrival. This version of the LodgingSale uses manual card entry to transmit the credit card data.

{% tabs %}
{% tab title="Request body" %}
{% include "../../../.gitbook/includes/param-sess-key.md" %}

***

{% include "../../../.gitbook/includes/param-credit-card-info.md" %}

***

{% include "../../../.gitbook/includes/param-account-holder.md" %}

***

{% include "../../../.gitbook/includes/param-end-customer.md" %}

***

`LodgingDetails` [api\_LodgingDetails](../soap-object-dictionary-wip.md#api_lodgingdetails) (object)

Fields: FirstName, LastName, IsAuthOnly, ConsentID4Auth, Folio, ArrivalDate, DepartureDate, Duration, ChangeDescriptor[^1], ChargeAmount, ExtraChargeAmount, ExtraChargesCode[^2], SaleCode[^3], StayID, CustomerData

***

{% include "../../../.gitbook/includes/param-merchid.md" %}
{% endtab %}

{% tab title="Response body" %}
{% include "../../../.gitbook/includes/param-ok-msg-errs.md" %}

***

{% include "../../../.gitbook/includes/param-tx-approved.md" %}

***

{% include "../../../.gitbook/includes/param-txid.md" %}

***

{% include "../../../.gitbook/includes/param-txncode.md" %}

***

{% include "../../../.gitbook/includes/param-avsr.md" %}

***

{% include "../../../.gitbook/includes/param-cvvr.md" %}

***

{% include "../../../.gitbook/includes/params-acquirer-opts-voice-opts-auth-balance.md" %}
{% endtab %}
{% endtabs %}

***

## Lodging Sale - By Consent

<mark style="color:green;">`POST`</mark> /ICardProcess/LodgingSale\_ByConsent

Process a lodging reservation using an existing consent instead of processing a new credit card.

{% tabs %}
{% tab title="Request body" %}
{% include "../../../.gitbook/includes/param-sess-key.md" %}

***

{% include "../../../.gitbook/includes/param-consent-id.md" %}

***

{% include "../../../.gitbook/includes/param-lodging-details.md" %}

***

{% include "../../../.gitbook/includes/param-merchid.md" %}
{% endtab %}

{% tab title="Response body" %}
{% include "../../../.gitbook/includes/param-ok-msg-errs.md" %}

***

{% include "../../../.gitbook/includes/param-tx-approved.md" %}

***

{% include "../../../.gitbook/includes/param-txid.md" %}

***

{% include "../../../.gitbook/includes/param-txncode.md" %}

***

{% include "../../../.gitbook/includes/param-avsr.md" %}

***

{% include "../../../.gitbook/includes/param-cvvr.md" %}

***

{% include "../../../.gitbook/includes/params-acquirer-opts-voice-opts-auth-balance.md" %}
{% endtab %}
{% endtabs %}

***

## Lodging Sale - By Consent (Explicit)

<mark style="color:green;">`POST`</mark> /ICardProcess/LodgingSale\_ByConsent\_Exp

Process a lodging reservation using an existing consent and specify the data entry person.&#x20;

{% tabs %}
{% tab title="Request body" %}
{% include "../../../.gitbook/includes/param-sess-key.md" %}

***

{% include "../../../.gitbook/includes/param-consent-id.md" %}

***

{% include "../../../.gitbook/includes/param-lodging-details.md" %}

***

`UserOperator` string

Identity of the data entry person.

***

{% include "../../../.gitbook/includes/param-merchid.md" %}
{% endtab %}

{% tab title="Response body" %}
{% include "../../../.gitbook/includes/param-ok-msg-errs.md" %}

***

{% include "../../../.gitbook/includes/param-tx-approved.md" %}

***

{% include "../../../.gitbook/includes/param-txid.md" %}

***

{% include "../../../.gitbook/includes/param-txncode.md" %}

***

{% include "../../../.gitbook/includes/param-avsr.md" %}

***

{% include "../../../.gitbook/includes/param-cvvr.md" %}

***

{% include "../../../.gitbook/includes/params-acquirer-opts-voice-opts-auth-balance.md" %}
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
