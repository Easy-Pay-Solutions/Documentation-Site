# Querying

### Introduction

**Query Strings:**

Number provides a robust query language which provides a means for you to obtain specific records. For instance, Let’s say you want to return all records from merchant record 1 which were created in JUNE 2024 (update to relevant dates) and are SETTLED.

**Here is the query:**

<kbd>`(A=1)&&(C>='6/1/2024')&&(C<'7/1/2024')&&(B=2)`</kbd>

Each Letter represents a variable and the following chart shows each meaning.

***

Reconciliation: If you are using our widgets and relying on real-time posting from each widget submission it may be desirable to do periodic reconciliation (once per day week or once per week).

{% hint style="info" %}
**Note**

Do not request a query without a limiting date factor. As the account grows you may end up attempting to return an excessive number of past records which will cause an error.
{% endhint %}

Here is a typical Reconciliation query

* (A=2)&&(U='WID')&&(C>='6/1/2024')&&((B=1)||(B=2))
* (A=2) is used to return records created under merchant record 2
* (U='WID') is used to pull records with an **ORIGIN** of **WIDGET**
* (C>='6/1/2024') **Important: Please do not return exceessive records, pick a date range!**&#x20;
* ((B=1)||(B=2)) is used to pull back **OPEN** or **SETTLED** transactions



***



### Transaction Query

#### ENUMS - TXSTATUS (B) <a href="#enums-txstatus-b" id="enums-txstatus-b"></a>

<table><thead><tr><th width="167">Query Variable</th><th>Transaction Status</th><th>Example</th></tr></thead><tbody><tr><td>-1</td><td>ALL</td><td>(B=-1)</td></tr><tr><td>1</td><td>OPEN</td><td>(B=1)</td></tr><tr><td>2</td><td>SETTLED</td><td>(B=2)</td></tr><tr><td>3</td><td>FAILED</td><td>(B=3)</td></tr><tr><td>4</td><td>LOCKED</td><td>(B=4))</td></tr><tr><td>5</td><td>VOID</td><td>(B=5))</td></tr></tbody></table>

\
**TXTYPE (K)**

<table><thead><tr><th width="170">Query Variable</th><th>Transaction Type</th><th>Example</th></tr></thead><tbody><tr><td>-1</td><td>ALL</td><td>(K=-1)</td></tr><tr><td>1</td><td>CCAUTHONLY</td><td>(K=1)</td></tr><tr><td>2</td><td>CCSALE</td><td>(K=2)</td></tr><tr><td>3</td><td>CCFORCE</td><td>(K=3)</td></tr><tr><td>4</td><td>CCVOICE</td><td>(K=4)</td></tr><tr><td>5</td><td>CCADJUST</td><td>(K=5)</td></tr><tr><td>6</td><td>CCCREDIT</td><td>(K=6)</td></tr></tbody></table>

<table><thead><tr><th width="170">Query Variable</th><th>Desired Parameter</th><th>Example</th></tr></thead><tbody><tr><td>A</td><td>MERCHANT ID</td><td>(A=1) here you can choose which merchant record you are interested in</td></tr><tr><td>B</td><td>TRANSACTION STATUS</td><td>(B=1) see above explanation for TXSTATUS (B) OPEN ,SETTLED, FAILED , etc</td></tr><tr><td>C</td><td>DATE CREATED</td><td>(C>='7/5/2024 12:00:00 AM')&#x26;&#x26;(C&#x3C;'7/6/2024 12:00:00 AM')( a full day )</td></tr><tr><td>D</td><td>LAST NAME</td><td>(D LIKE '%MITH') ( return all names that end with 'MITH' such as SMITH)</td></tr><tr><td>E</td><td>TRANSACTION LOCK</td><td>for Locked transactions use (E&#x3C;>'0'), unlocked use (E='0')</td></tr><tr><td>F</td><td>BATCH LOG ID</td><td>(F=817) this is the identity reference for a batch settlement record</td></tr><tr><td>Q</td><td>CREDIT CARD</td><td>(Q='4123') will search the last 4 digits of a credit card</td></tr><tr><td>W</td><td>BATCH NUMBER</td><td>(W=762) this is the actual Batch Number for a batch settlement</td></tr><tr><td>H</td><td>ID</td><td>(H=58258) This is the transaction ID, the unique identity of the transaction</td></tr><tr><td>K</td><td>TRANSACTION TYPE</td><td>(K=2) see above explanation for TXTYPE (K) CCSALE , CCCREDIT , CCAUTHONLY , etc</td></tr><tr><td>M</td><td>CLIENT REFERENCE ID (PATIENT ID)</td><td>(M LIKE '%21DF34%') return any records which CONTAINS '21DF34' . This is a user defined field</td></tr><tr><td>N</td><td>RPGUID</td><td>(N = 'AB#6754'') return any records which equal 'AB#6754' . This is a user defined field</td></tr><tr><td>J</td><td>FIRST NAME</td><td>(J LIKE 'ROB%'') return all names that start with 'ROB' such as 'ROBERT'</td></tr><tr><td>R</td><td>APPROVAL CODE</td><td>(R='TAS625')</td></tr><tr><td>L</td><td>AMOUNT</td><td>(L=6.00)</td></tr><tr><td>P</td><td>CONSENTID</td><td>(P=15875) return transactions that were charged against a particular CARD ON FILE</td></tr><tr><td>S</td><td>CUSTOMER LAST NAME</td><td>(S='SMITH')</td></tr><tr><td>T</td><td>CUSTOMER FIRST NAME</td><td>(T='%FOSTER%')</td></tr><tr><td>U</td><td>ORIGIN</td><td>(U='WID')||(U='VT')||(U='API') transactions may originate from 'WIDGET , Virtual Terminal , or API</td></tr></tbody></table>



***



### Consent Annual/Consent General/Consent Recurring/ACHConsent Query

<table><thead><tr><th width="170">Query Variable</th><th>Query Setup</th><th>Example</th></tr></thead><tbody><tr><td>A</td><td>MERCHANT ID</td><td>(A=5)</td></tr><tr><td>B</td><td>START DATE</td><td>(B>='10/20/2024')</td></tr><tr><td>C</td><td>END DATE</td><td>(C&#x3C;='10/20/2024')</td></tr><tr><td>D</td><td>ACCOUNT HOLDER LAST NAME</td><td>(D LIKE '%SMITH%')</td></tr><tr><td>E</td><td>CREATED ON</td><td>(E&#x3C;='10/20/2024')</td></tr><tr><td>F</td><td>CUSTOMER REFERENCE ID (PATIENT ID)</td><td>(F LIKE '%213456%')</td></tr><tr><td>G</td><td>CONSENT TYPE</td><td>(G=-1) = ALL (G=1) = ANNUAL (G=2) = ONE TIME (G=3) = RECURRING (G=4) = SUBSCRIPTION</td></tr><tr><td>H</td><td>ENABLED</td><td>(H=1)</td></tr><tr><td>J</td><td>RPGUID</td><td>(J LIKE '%RPGUIDtest%')</td></tr><tr><td>K</td><td>ACCOUNT HOLDER FIRST NAME</td><td>(K LIKE '%SMITH%')</td></tr><tr><td>Z</td><td>CONSENT ID</td><td>(Z=12345)</td></tr></tbody></table>

\
\




