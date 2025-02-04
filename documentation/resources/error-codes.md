---
description: Links to error code reference
---

# Error Codes

## Transaction response codes

When using our services, you might end up with a transaction that was declined. This is usually signaled by a response with a `TxApproved` value of false and a decline code in the `ErrCode` field. You can then display the `RespMsg` to the user to explain the error.

If you want to be able to tell when a specific type of error occurs, you can use our decline code reference and handle them accordingly.



### Global Payments decline codes

These codes are used when processing transactions through the Global Payments system. For Global Payments transaction decline codes, see[#decline-codes](../testing/global-payments-testing.md#decline-codes "mention").



### First Data decline codes

These codes are relevant when dealing with transactions processed by First Data. For First Data transaction decline codes, see [#response-codes](../testing/first-data-testing.md#response-codes "mention").



### ACH decline codes

These codes are specifically for Automated Clearing House (ACH) transactions. For ACH decline codes, see [#complete-list-of-return-codes](../testing/ach-testing.md#complete-list-of-return-codes "mention").

