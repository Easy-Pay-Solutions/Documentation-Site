---
title: param - query recurring schedule
---

`Query` string

A query string for obtaining specific recurring schedule records using Number's query language. Build logical terms and join them with '&&' for logical AND or '||' for logical OR. Use single quotes for text and date values. Refer to the variable chart for query composition:

* A: CONSENT ID - The unique identifier for the consent associated with the recurring schedule, e.g. (A=545).
* B: STATUS - The status of the recurring schedule, e.g. (B=-1).
  * -1: ALL
  * 1: SCHEDULED
  * 2: PAID
  * 3: FAILED
  * 4: CANCELLED
* C: DUE DATE - The date the next payment is due, e.g. (C='10/20/2024').
* D: ACCOUNT HOLDER LAST NAME - Last name of the account holder, e.g. (D LIKE '%MITH') for all names that end with 'MITH'.
* E: MERCHANT ID - The unique identifier for the merchant associated with the recurring schedule, e.g. (E=1).
* F: ACCOUNT NUMBER LAST 4 - The last 4 digits of the account number associated with the recurring schedule, e.g. (F='1234').
* G: SCHEDULE ID - The unique identifier for the recurring schedule, e.g. (G=12).
* H: TYPE - The type of recurring schedule, e.g. (H=-1).
  * -1: ALL
  * 3: RECURRING
  * 4: SUBSCRIPTION

Example: "(H=3)&&(C>='10/20/2024')"
