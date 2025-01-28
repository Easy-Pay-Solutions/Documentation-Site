---
title: param - query batch log
---

`Query` string

A query string for obtaining specific batch log records using Number's query language. Build logical terms and join them with '&&' for logical AND or '||' for logical OR. Use single quotes for text and date values. Refer to the variable chart for query composition:

* A: MERCHANT ID - The merchant record you are interested in, e.g. (A=545).
* B: STATUS - The status of the batch log, e.g. (B=-1).
  * -1: ALL
  * 1: FAILED
  * 2: APPROVED
* C: CREATED ON - The date the batch log was created, e.g. (C>='3/2/2024')&&(C<='4/2/2024').
* D: BATCH LOG ID - The unique identifier for the batch log, e.g. (D=1777).
* E: BATCH NUMBER - The batch number for the batch log, e.g. (E=185).

Example: "(B=1)&&(C>='3/2/2024')&&(C<='4/2/2024')"
