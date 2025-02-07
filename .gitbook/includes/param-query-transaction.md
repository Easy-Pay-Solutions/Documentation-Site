---
title: param - query transaction
---

`Query` string

A query string for obtaining specific consent records using Number's query language. Build logical terms and join them with '&&' for logical AND or '||' for logical OR. Use single quotes for text and date values. Refer to the variable chart for query composition:

* A: MERCHANT ID - The merchant record you are interested in, e.g. (A=1).
* B: TRANSACTION STATUS - The status of the transaction, e.g. (B=1).
  * -1: ALL
  * 1: OPEN
  * 2: SETTLED
  * 3: FAILED
  * 4: LOCKED
  * 5: VOID
* C: DATE CREATED - The date the transaction was created, e.g. (C>='7/5/2024 12:00:00 AM').
* D: LAST NAME - Last name of the account holder, e.g. (D LIKE '%MITH') for all names that end with 'MITH'.
* E: TRANSACTION LOCK - Lock status of the transaction, e.g. (E<>'0') for locked transactions.
* F: BATCH LOG ID - Reference to a batch settlement record, e.g. (F=817).
* H: TRANSACTION ID - The unique identifier for the transaction, e.g. (H=58258).
* J: FIRST NAME - First name of the account holder, e.g. (J LIKE 'ROB%') for all names that start with 'ROB'.
* K: TRANSACTION TYPE - The type of transaction, e.g. (K=-1).
  * -1: ALL
  * 1: CCAUTHONLY
  * 2: CCSALE
  * 3: CCFORCE
  * 4: CCVOICE
  * 5: CCADJUST
  * 6: CCCREDIT
* L: AMOUNT - The $ amount of the transaction, e.g. (L>100.00).
* M: CLIENT REFERENCE ID - User-defined value on the transaction.
* N: RPGUID - User-defined value on the transaction.
* P: CONSENT ID - The Consent ID of card on file the transactions were charged against, e.g. (P=15875).
* Q: CREDIT CARD LAST 4 - The last 4 digits of a credit card, e.g. (Q='4123').
* R: APPROVAL CODE - The approval code for the transaction, e.g. (R='TAS626').
* S: CUSTOMER LAST NAME - The last name of the customer, e.g. (S='SMITH').
* T: CUSTOMER FIRST NAME - The first name of the customer, e.g. (T='FOSTER').
* U: ORIGIN - The origin of the transaction, e.g. (U='API').
  * "API": REST / SOAP API
  * "WID": Widget
  * "VT": Virtual Terminal
  * "MOBL": Mobile SDK
  * "SDK": Verifone
  * "AUTO": Automatically scheduled from a payment plan
* W: BATCH NUMBER - The batch number for the batch settlement, e.g. (W=762).

Example: "(B=3)&&(E=1)&&(C>'2024-09-01')"
