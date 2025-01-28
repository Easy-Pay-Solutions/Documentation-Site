---
title: param - query consent
---

`Query` string

A query string for obtaining specific consent records using Number's query language. Build logical terms and join them with '&&' for logical AND or '||' for logical OR. Use single quotes for text and date values. Refer to the variable chart for query composition:

* A: MERCHANT ID - The merchant record you are interested in, e.g. (A=1).
* B: START DATE - The date the consent becomes active, e.g. (B>='10/20/2024').
* C: END DATE - The date the consent expires, e.g. (C<='10/20/2024').
* D: ACCOUNT HOLDER LAST NAME - Last name of the account holder, e.g. (D LIKE '%MITH') for all names that end with 'MITH'.
* E: CREATED ON - The date the consent was created, e.g. (E<='10/20/2024').
* F: CUSTOMER REFERENCE ID - User-defined value on the consent.
* G: CONSENT TYPE - The type of consent, e.g. (G='-1').
  * -1: ALL
  * 1: ANNUAL
  * 2: ONE-TIME
  * 3: RECURRING
  * 4: SUBSCRIPTION
* H: ENABLED - Indicates whether the consent is currently enabled, e.g. (H=1).
* J: RPGUID - User-defined value on the consent.
* K: ACCOUNT HOLDER FIRST NAME - First name of the account holder, e.g. (K LIKE 'ROB%') for all names that start with 'ROB'.
* Z: CONSENT ID - The unique identifier for the consent, e.g. (Z=15875).

Example: "(G=1)&&(B>'10/20/2024')"
