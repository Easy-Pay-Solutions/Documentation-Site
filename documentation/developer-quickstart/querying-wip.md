---
description: Find the information you need by querying
---

# Querying (WIP)

If you need to find a specific transaction or consent and you don't remember the specific ID or you need to find all records matching your criteria, you can either programatically query our **APIs** or the **Virtual Terminal** to view and filter the records from a user interface.



### REST and SOAP API

Before you write your query, you'll need to find a relevant method in the [rest-api](../../api-reference/rest-api/ "mention") or [soap-api](../../api-reference/soap-api/ "mention") reference.

When querying, one of the required parameters is a `Query` string. You can read about Number's query language in our [querying.md](../resources/querying.md "mention") reference. All variable options are also listed and fully described in the API reference.

You can use the variables described in the documentation to build logical terms, and you can build and join logical terms "&&" for a logical AND or "||" for a logical OR.

{% hint style="info" %}
Depending on the type of record you're querying (transaction, consent, ...), the variables you can use inside of a `Query` string will differ. The formatting rules do not change and stay consistent between them.
{% endhint %}

{% include "../../.gitbook/includes/warning-query-date-factor.md" %}



#### Example

As an example, if want to find settled ACH transactions made in January 2025 made using the Verifone card readers, you can call [#apicardprocrest-v1.0.0-query-achtransaction](../../api-reference/rest-api/query.md#apicardprocrest-v1.0.0-query-achtransaction "mention") or[#ach-transaction-query](../../api-reference/soap-api/ach.md#ach-transaction-query "mention") depending on which API you are using.

You can check the description of the `Query` string parameter or check the [querying.md](../resources/querying.md "mention") reference for [#transaction-query](../resources/querying.md#transaction-query "mention") to find out that **variable 'B' corresponds to transaction status, variable 'C' corresponds to date created, and 'U' corresponds to the transaction origin**.

Each variable which requires an enum includes a description of valid values. **Settled transactions have a transaction status of '2', and Verifone transactions have an origin of 'SDK'.** To format the date correctly, follow the examples given for the variable.

You can combine the filters to build your `Query` string like so:

```sql
(B=2)&&(C>='1/1/2025')&&(C<='1/31/2025')&&(U='SDK')
```



&#x20;
