---
title: param - lodging details
---

`LodgingDetails` [api\_LodgingDetails](../../api-reference/soap-api-v2/soap-object-dictionary-wip.md#api_lodgingdetails) (object)

Fields: FirstName, LastName, IsAuthOnly, ConsentID4Auth, Folio, ArrivalDate, DepartureDate, Duration, ChangeDescriptor[^1], ChargeAmount, ExtraChargeAmount, ExtraChargesCode[^2], SaleCode[^3], StayID, CustomerData

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
