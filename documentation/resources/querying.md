---
description: Reference to the Number query language
---

# Querying

### Introduction

Number provides a robust query language for filtering specific records using the APIs.&#x20;

#### Example

To return all settled transaction records created in June 2024, you can use the query below:

```sql
(A=1)&&(C>='6/1/2024')&&(C<'7/1/2024')&&(B=2)
```

#### Format

Queries in the Number query language consist of the following:

{% stepper %}
{% step %}
#### Filters and values

Each letter represents a query parameter (filter). You can follow it up by&#x20;

* an equal sign "=" for equality comparison,
* ">", ">=", "<", and "<=" for comparison of numeric values and dates,
* the "_LIKE_" keyword for SQL-like string comparison.

**Use single quotes for text and date values.**&#x20;
{% endstep %}

{% step %}
#### Logical operators

You can build and join logical terms with two ampersand characters "&&" for **logical AND** or two pipe characters "||" for **logical OR**.
{% endstep %}
{% endstepper %}

{% hint style="info" %}
Refer to the variable charts below or the API reference for query composition. They list and describe all of the query parameters that you can use in each scenario.
{% endhint %}



***



### Reconciliation

Reconciliation is the process of ensuring that the transaction records in your system match those in the Number database. **This is important for maintaining accurate financial records and can be done periodically, such as once a day or week.**

When using Number's widgets, it may be desirable to perform periodic reconciliation. A typical reconciliation query might include specific parameters to filter records based on criteria like merchant ID, transaction status, and date range to avoid excessive data retrieval, which could lead to errors.

{% hint style="info" %}
For effective reconciliation, it is recommended to periodically query the database and utilize webhooks for real-time notifications to keep your records up to date .
{% endhint %}

#### Example

Here is a typical Reconciliation query

```sql
(A=2)&&(U='WID')&&(C>='6/1/2024')&&((B=1)||(B=2))
```

* `(A=2)` is used to return records created under merchant record 2
* `(U='WID')` is used to pull records with an `ORIGIN` of widget
* `(C>='6/1/2024')` is a date range to avoid returning an exceessive records&#x20;
* `((B=1)||(B=2))` is used to pull back _OPEN_ or _SETTLED_ transactions



***



### Transaction query

Obtain specific transaction records using Number's query language.&#x20;

{% code title="Query example" overflow="wrap" %}
```sql
(G=1)&&(B>'10/20/2024')
```
{% endcode %}

<table><thead><tr><th width="114">Variable</th><th width="153">Parameter</th><th>Description</th></tr></thead><tbody><tr><td>A</td><td>MERCHANT ID</td><td>The merchant record you are interested in, e.g. <code>(A=1)</code>.</td></tr><tr><td>B</td><td>TRANSACTION STATUS</td><td>The status of the transaction, e.g. <code>(B=1)</code>. <br><br>* -1: <em>ALL</em> <br>* 1: <em>OPEN</em> <br>* 2: <em>SETTLED</em> <br>* 3: <em>FAILED</em> <br>* 4: <em>LOCKED</em> <br>* 5: <em>VOID</em></td></tr><tr><td>C</td><td>DATE CREATED</td><td>The date the transaction was created, e.g. <code>(C>='7/5/2024 12:00:00 AM')</code>.</td></tr><tr><td>D</td><td>LAST NAME</td><td>Last name of the account holder, e.g. <code>(D LIKE '%MITH')</code> for all names that end with '<em>MITH</em>'.</td></tr><tr><td>E</td><td>TRANSACTION LOCK</td><td>Lock status of the transaction, e.g. <code>(E&#x3C;>'0')</code> for locked transactions.</td></tr><tr><td>F</td><td>BATCH LOG ID</td><td>Reference to a batch settlement record, e.g. <code>(F=817)</code>.</td></tr><tr><td>H</td><td>TRANSACTION ID</td><td>The unique identifier for the transaction, e.g. <code>(H=58258)</code>.</td></tr><tr><td>J</td><td>FIRST NAME</td><td>First name of the account holder, e.g. <code>(J LIKE 'ROB%')</code> for all names that start with '<em>ROB</em>'.</td></tr><tr><td>K</td><td>TRANSACTION TYPE</td><td>The type of transaction, e.g. <code>(K=-1)</code>. <br><br>* -1: <em>ALL</em> <br>* 1: <em>CCAUTHONLY</em> <br>* 2: <em>CCSALE</em> <br>* 3: <em>CCFORCE</em> <br>* 4: <em>CCVOICE</em> <br>* 5: <em>CCADJUST</em> <br>* 6: <em>CCCREDIT</em></td></tr><tr><td>L</td><td>AMOUNT</td><td>The $ amount of the transaction, e.g. <code>(L>100.00)</code>.</td></tr><tr><td>M</td><td>CLIENT REFERENCE ID (PATIENT ID)</td><td>User-defined value on the transaction.</td></tr><tr><td>N</td><td>RPGUID</td><td>User-defined value on the transaction.</td></tr><tr><td>P</td><td>CONSENT ID</td><td>The consent ID of card on file the transactions were charged against, e.g. <code>(P=15875)</code>.</td></tr><tr><td>Q</td><td>CREDIT CARD LAST 4</td><td>The last 4 digits of a credit card, e.g. <code>(Q='4123')</code>.</td></tr><tr><td>R</td><td>APPROVAL CODE</td><td>The approval code for the transaction, e.g. <code>(R='TAS626')</code>.</td></tr><tr><td>S</td><td>CUSTOMER LAST NAME</td><td>The last name of the customer, e.g. <code>(S='SMITH')</code>.</td></tr><tr><td>T</td><td>CUSTOMER FIRST NAME</td><td>The first name of the customer, e.g. <code>(T='FOSTER')</code>.</td></tr><tr><td>U</td><td>ORIGIN</td><td>The origin of the transaction, e.g. <code>(U='API')</code>. <br><br>* "<em>API</em>": REST API <br>* "<em>WID</em>": Widget <br>* "<em>VT</em>": Virtual Terminal <br>* "<em>MOBL</em>": Mobile SDK <br>* "<em>SDK</em>": Verifone <br>* "<em>AUTO</em>": Automatically scheduled from a payment plan</td></tr><tr><td>W</td><td>BATCH NUMBER</td><td>The batch number for the batch settlement, e.g. <code>(W=762)</code>.</td></tr></tbody></table>



***



### Consent query

Obtain specific consent records using Number's query language

{% code title="Query example" overflow="wrap" %}
```sql
(G=1)&&(B>'10/20/2024')
```
{% endcode %}

<table><thead><tr><th width="113">Variable</th><th width="154">Parameter</th><th>Description</th></tr></thead><tbody><tr><td>A</td><td>MERCHANT ID</td><td>The merchant record you are interested in, e.g. <code>(A=1)</code>.</td></tr><tr><td>B</td><td>START DATE</td><td>The date the consent becomes active, e.g. <code>(B>='10/20/2024')</code>.</td></tr><tr><td>C</td><td>END DATE</td><td>The date the consent expires, e.g. <code>(C&#x3C;='10/20/2024')</code>.</td></tr><tr><td>D</td><td>ACCOUNT HOLDER LAST NAME</td><td>Last name of the account holder, e.g. <code>(D LIKE '%MITH')</code> for all names that end with '<em>MITH</em>'.</td></tr><tr><td>E</td><td>CREATED ON</td><td>The date the consent was created, e.g. <code>(E&#x3C;='10/20/2024')</code>.</td></tr><tr><td>F</td><td>CUSTOMER REFERENCE ID (PATIENT ID)</td><td>User-defined value on the consent.</td></tr><tr><td>G</td><td>CONSENT TYPE</td><td>The type of consent, e.g. <code>(G='-1')</code>. <br><br>* -1: <em>ALL</em> <br>* 1: <em>ANNUAL</em> <br>* 2: <em>ONE-TIME</em> <br>* 3: <em>RECURRING</em> <br>* 4: <em>SUBSCRIPTION</em></td></tr><tr><td>H</td><td>ENABLED</td><td>Indicates whether the consent is currently enabled, e.g. <code>(H=1)</code>.</td></tr><tr><td>J</td><td>RPGUID</td><td>User-defined value on the consent.</td></tr><tr><td>K</td><td>ACCOUNT HOLDER FIRST NAME</td><td>First name of the account holder, e.g. <code>(K LIKE 'ROB%')</code> for all names that start with '<em>ROB</em>'.</td></tr><tr><td>Z</td><td>CONSENT ID</td><td>The unique identifier for the consent, e.g. <code>(Z=15875)</code>.</td></tr></tbody></table>



***



### Recurring schedule query <a href="#recurring-schedule-query" id="recurring-schedule-query"></a>

Obtain specific recurring schedule records using Number's query language.

{% code title="Query example" overflow="wrap" %}
```sql
(H=3)&&(C>='10/20/2024')
```
{% endcode %}

<table><thead><tr><th width="111">Variable</th><th width="146">Parameter</th><th>Description</th></tr></thead><tbody><tr><td>A</td><td>CONSENT ID</td><td>The unique identifier for the consent associated with the recurring schedule, e.g. <code>(A=545)</code>.</td></tr><tr><td>B</td><td>STATUS</td><td>The status of the recurring schedule, e.g. <code>(B=-1)</code>. <br><br>* -1: <em>ALL</em> <br>* 1: <em>SCHEDULED</em> <br>* 2: <em>PAID</em> <br>* 3: <em>FAILED</em> <br>* 4: <em>CANCELLED</em></td></tr><tr><td>C</td><td>DUE DATE</td><td>The date the next payment is due, e.g. <code>(C='10/20/2024')</code>.</td></tr><tr><td>D</td><td>ACCOUNT HOLDER LAST NAME</td><td>Last name of the account holder, e.g. <code>(D LIKE '%MITH')</code> for all names that end with '<em>MITH</em>'.</td></tr><tr><td>E</td><td>MERCHANT ID</td><td>The unique identifier for the merchant associated with the recurring schedule, e.g. <code>(E=1)</code>.</td></tr><tr><td>F</td><td>ACCOUNT NUMBER LAST 4</td><td>The last 4 digits of the account number associated with the recurring schedule, e.g. <code>(F='1234')</code>.</td></tr><tr><td>G</td><td>SCHEDULE ID</td><td>The unique identifier for the recurring schedule, e.g. <code>(G=12)</code>.</td></tr><tr><td>H</td><td>TYPE</td><td>The type of recurring schedule, e.g. <code>(H=-1)</code>. <br><br>* -1: <em>ALL</em> <br>* 3: <em>RECURRING</em> <br>* 4: <em>SUBSCRIPTION</em></td></tr></tbody></table>



***



### Batch log query <a href="#batch-log-query" id="batch-log-query"></a>

Obtain specific batch log records using Number's query language.

<table><thead><tr><th width="114">Variable</th><th width="159">Parameter</th><th>Description</th></tr></thead><tbody><tr><td>A</td><td>MERCHANT ID</td><td>The merchant record you are interested in, e.g. <code>(A=545)</code>.</td></tr><tr><td>B</td><td>STATUS</td><td>The status of the batch log, e.g. <code>(B=-1)</code>. <br><br>* -1: <em>ALL</em> <br>* 1: <em>FAILED</em> <br>* 2: <em>APPROVED</em></td></tr><tr><td>C</td><td>CREATED ON</td><td>The date the batch log was created, e.g. <code>(C>='3/2/2024')&#x26;&#x26;(C&#x3C;='4/2/2024')</code>.</td></tr><tr><td>D</td><td>BATCH LOG ID</td><td>The unique identifier for the batch log, e.g. <code>(D=1777)</code>.</td></tr><tr><td>E</td><td>BATCH NUMBER</td><td>The batch number for the batch log, e.g. <code>(E=185)</code>.</td></tr></tbody></table>



