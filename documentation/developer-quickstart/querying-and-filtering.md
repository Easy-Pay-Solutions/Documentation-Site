---
description: Find the information you need by querying
---

# Querying

<figure><img src="../../.gitbook/assets/Querying B .png" alt=""><figcaption></figcaption></figure>

If you need to find a specific record (transaction, consent, etc.) and you don't remember the unique ID for that record or you need to find all records matching your criteria, you can either query our **APIs** programatically or use the **Virtual Terminal** to view and filter the records from its user interface.



## REST and SOAP API

To query records, you'll need to find a relevant method in the [rest-api](../../api-reference/rest-api/ "mention") or [soap-api](../../api-reference/soap-api/ "mention") reference.

When querying, one of the most common required parameters is a `Query` string. It should consist of variables that correspond to fields on the records and logical terms built using those variables.&#x20;

**All `Query` string variable options are fully described in the API reference under specific API methods and in the** [querying.md](../resources/querying.md "mention") **reference.** You can use the variables to build logical terms, and you can build and join logical terms "&&" for a logical AND or "||" for a logical OR.

Read about Number's query language in our [querying.md](../resources/querying.md "mention") reference.

{% hint style="info" %}
Depending on the type of record you're querying (transaction, consent, ...), the variables you can use inside of a `Query` string will differ. The formatting rules do not change.
{% endhint %}

{% include "../../.gitbook/includes/warning-query-date-factor.md" %}



### Example

As an example, if want to find settled ACH transactions made in January 2025 made using Verifone card readers, you can call [#apicardprocrest-v1.0.0-query-achtransaction](../../api-reference/rest-api/query.md#apicardprocrest-v1.0.0-query-achtransaction "mention") or[#ach-transaction-query](../../api-reference/soap-api/ach.md#ach-transaction-query "mention") depending on which API you are using.

You can check the description of the `Query` string parameter or check the [querying.md](../resources/querying.md "mention") reference for [#transaction-query](../resources/querying.md#transaction-query "mention") section to find out that **variable 'B' corresponds to transaction status, variable 'C' corresponds to date created, and 'U' corresponds to the transaction origin**.

Each variable which requires an enum includes a description of valid values. **Settled transactions have a transaction status of '2', and Verifone transactions have an origin of 'SDK'.** To format the date correctly, follow the examples given for the variable.

You can combine the filters to build your `Query` string like so:

```sql
(B=2)&&(C>='1/1/2025')&&(C<='1/31/2025')&&(U='SDK')
```



***



## Virtual Terminal

You can filter consents, transactions, and other records through the Virtual Terminal user interface.&#x20;

To log into the Virtual Terminal, you need to have a user account created through the Client Admin Portal as described in the [authentication.md](authentication.md "mention") quickstart guide.

Once you're logged in, see the navigation on the left and click on _Scheduled_ to view scheduled payments, click on _Settlement_ to view settlements, or expand _Reports_ to find other reports. There, you'll be able to search and filter records using the user interface.

You can read more about using the Virtual Terminal in the [virtual-terminal.md](../getting-started/integration-options/virtual-terminal.md "mention") guide.

<figure><img src="../../.gitbook/assets/Virtual_Terminal.png" alt=""><figcaption></figcaption></figure>



