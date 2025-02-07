---
title: params - purchase
---

`PurchType` PurchaseType (enum)

The type of purchase.

Values:\
\- notSet = 0\
\- CPSwipe = 1\
\- ManKey = 2\
\- CPSwipeFBTrack1 = 3\
\- CPSwipeFBTrack2 = 4\
\- EMVchip = 5

***

`Track` string

The data on the magnetic strip of the credit card on card present transactions.

***

`EmvTags` string

***

`CardInfo` [api\_CardInfo](../../api-reference/soap-api/soap-object-dictionary.md#api_cardinfo) (object)

The details on the card used for the transaction.

Fields: AccountNumber, ExpMonth, ExpYear, CSV

***

`EMVRecTags` [api\_EmvReceipt](../../api-reference/soap-api/soap-object-dictionary.md#api_emvreceipt) (object)

EMV record tags associated with the transaction.

Fields: AID, TSI, TVR, AC, ARC

***

`IsAuthOnly` boolean
