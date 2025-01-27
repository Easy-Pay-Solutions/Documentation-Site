---
description: Methods related to ACH (Automated Clearing House) transactions
---

# ACH

## Create an ACH Transaction - Apply Credit

<mark style="color:green;">`POST`</mark> /ICardProcess/ACH\_ApplyCredit

Applies a credit to the specified ACH transaction. Credits can be applied after a transaction has been settled; open transactions should use the ACHTransaction\_Void method.

{% tabs %}
{% tab title="Request body" %}
{% include "../../.gitbook/includes/param-sess-key.md" %}

***

{% include "../../.gitbook/includes/param-consent-id.md" %}

***

{% include "../../.gitbook/includes/param-process-amount.md" %}
{% endtab %}

{% tab title="Response body" %}
{% include "../../.gitbook/includes/param-ok-msg-errs.md" %}

***

{% include "../../.gitbook/includes/param-tx-approved.md" %}

***

{% include "../../.gitbook/includes/param-txid.md" %}
{% endtab %}
{% endtabs %}

***

## Process Payment - ACH Consent Annual

<mark style="color:green;">`POST`</mark> /ICardProcess/ACHConsentAnnual\_ProcPayment

Processes the specified $ amount against the associated ACH consent.

{% tabs %}
{% tab title="Request body" %}
{% include "../../.gitbook/includes/param-sess-key.md" %}

***

`ConsentID` int

This is the the ID number that is returned after you save a card on file.

***

{% include "../../.gitbook/includes/param-process-amount.md" %}
{% endtab %}

{% tab title="Response body" %}
{% include "../../.gitbook/includes/param-ok-msg-errs.md" %}

***

{% include "../../.gitbook/includes/param-tx-approved.md" %}

***

{% include "../../.gitbook/includes/param-txid.md" %}

***

`AuthID` string

The authorization ID provided by the payment processor upon approval of the transaction.

***

`uniqueTranID` string

A unique identifier for the transaction that can be used for tracking and reconciliation purposes.
{% endtab %}
{% endtabs %}

***

## Process Payment - Alt Merchant - ACH Consent Annual

<mark style="color:green;">`POST`</mark> /ICardProcess/ACHConsentAnnual\_ProcPayment\_Alt

Processes the specified $ amount for an existing ACH consent, but the payment is transferred to a different merchant than the original one.&#x20;

The alternate merchant must be previously assigned to the account holders' account.

{% include "../../.gitbook/includes/info-alt-merchant.md" %}

{% tabs %}
{% tab title="Request body" %}
{% include "../../.gitbook/includes/param-sess-key.md" %}

***

{% include "../../.gitbook/includes/param-consent-id.md" %}

***

{% include "../../.gitbook/includes/param-process-amount.md" %}

***

{% include "../../.gitbook/includes/param-alternate-merchid.md" %}
{% endtab %}

{% tab title="Response body" %}
{% include "../../.gitbook/includes/param-ok-msg-errs.md" %}

***

{% include "../../.gitbook/includes/param-tx-approved.md" %}

***

{% include "../../.gitbook/includes/param-txid.md" %}

***

`AuthID` string

The authorization ID provided by the payment processor upon approval of the transaction.

***

`uniqueTranID` string

A unique identifier for the transaction that can be used for tracking and reconciliation purposes.
{% endtab %}
{% endtabs %}

***

## ACH Transaction Query

<mark style="color:green;">`POST`</mark> /ICardProcess/ACHTransaction\_Query

Returns the details for an ACH transaction. This query can return more than one transaction if searching for a range. Number has a robust query language \[link] that aids in search.&#x20;

{% tabs %}
{% tab title="Request body" %}
{% include "../../.gitbook/includes/param-sess-key.md" %}

***

{% include "../../.gitbook/includes/param-query.md" %}
{% endtab %}

{% tab title="Response body" %}
{% include "../../.gitbook/includes/param-ok-msg-errs.md" %}

***

{% include "../../.gitbook/includes/param-num-records.md" %}

***

`Transactions` List<[api\_ACHDetail](soap-object-dictionary.md#api_achdetail)> (array\<object>)

The ACH transaction details returned by the query.

Fields: ID, UniqueID, TXstamp, TXN\_DATETIME, AuthID, ValMsg, CreatedBy, CreatedOn, ChangedBy, ChangedOn, AcctType, Origin, RefTxID, REF\_ID, RPGUID, AcctHolderID, EndCustID, TxSTATUS, TxType, Credits, Amt, MerchID, UserID, ResolvedOn, SettledOn, BatchNO, BatchStatus, BatchLogID, AcctLast4, ReturnReason, CustName, FirstName, LastName, ConsentID.
{% endtab %}
{% endtabs %}

{% code title="Sample response" overflow="wrap" %}
```xml
<soapenv:Envelope xmlns:soapenv="http://schemas.xmlsoap.org/soap/envelope/"
                  xmlns:ns="http://example.com/soapapi">
   <soapenv:Header/>
   <soapenv:Body>
      <ns:api_TransactionQryResponse>
         <ns:FunctionOk>true</ns:FunctionOk>
         <ns:RespMsg>Successfully Returned Transaction Records : 1</ns:RespMsg>
         <ns:ErrMsg></ns:ErrMsg>
         <ns:ErrCode>0</ns:ErrCode>
         <ns:NumRecords>1</ns:NumRecords>
         <ns:Transactions>
            <ns:api_ACHDetail>
               <ns:ID>1405</ns:ID>
               <ns:UniqueID>167901CDE082BC57</ns:UniqueID>
               <ns:TXstamp>20240703</ns:TXstamp>
               <ns:TXN_DATETIME>2024-07-03T00:00:00-04:00</ns:TXN_DATETIME>
               <ns:AuthID>69019079</ns:AuthID>
               <ns:ValMsg>Success</ns:ValMsg>
               <ns:CreatedBy>Token 37564</ns:CreatedBy>
               <ns:CreatedOn>2024-06-30T09:37:52-04:00</ns:CreatedOn>
               <ns:ChangedBy xsi:nil="true" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"/>
               <ns:ChangedOn>0001-01-01T00:00:00-05:00</ns:ChangedOn>
               <ns:AcctType>PersonalChecking</ns:AcctType>
               <ns:Origin>API       </ns:Origin>
               <ns:RefTxID>0</ns:RefTxID>
               <ns:REF_ID>12456AA</ns:REF_ID>
               <ns:RPGUID>3d3424a6-c5f3-4c28</ns:RPGUID>
               <ns:AcctHolderID>1127</ns:AcctHolderID>
               <ns:EndCustID>35348</ns:EndCustID>
               <ns:TxSTATUS>SETTLED</ns:TxSTATUS>
               <ns:TxType>ACHDEBIT</ns:TxType>
               <ns:Credits>0.0000</ns:Credits>
               <ns:Amt>30.5000</ns:Amt>
               <ns:MerchID>1</ns:MerchID>
               <ns:UserID>0</ns:UserID>
               <ns:ResolvedOn>2024-07-05T10:06:41-04:00</ns:ResolvedOn>
               <ns:SettledOn>2024-07-05T00:00:00-04:00</ns:SettledOn>
               <ns:BatchNO>112</ns:BatchNO>
               <ns:BatchStatus>N</ns:BatchStatus>
               <ns:BatchLogID>0</ns:BatchLogID>
               <ns:AcctLast4>0277</ns:AcctLast4>
               <ns:ReturnReason></ns:ReturnReason>
               <ns:CustName>APIACH Sally</ns:CustName>
               <ns:FirstName>Sally</ns:FirstName>
               <ns:LastName>APIACH</ns:LastName>
               <ns:ConsentID>0</ns:ConsentID>
            </ns:api_ACHDetail>
         </ns:Transactions>
      </ns:api_TransactionQryResponse>
   </soapenv:Body>
</soapenv:Envelope>
```
{% endcode %}

***

## ACH Transaction Void

<mark style="color:green;">`POST`</mark> /ICardProcess/ACHTransaction\_Void

Voids an ACH transaction. The transaction can be voided before it is settled. Once a transaction has been settled, the [ACH\_ApplyCredit](ach.md#ach-apply-credit) method should be used.

{% tabs %}
{% tab title="Request body" %}
{% include "../../.gitbook/includes/param-sess-key.md" %}

***

{% include "../../.gitbook/includes/param-txid.md" %}
{% endtab %}

{% tab title="Response body" %}
{% include "../../.gitbook/includes/param-ok-msg-errs.md" %}

***

{% include "../../.gitbook/includes/param-tx-approved.md" %}

***

{% include "../../.gitbook/includes/param-txid.md" %}

***

`AuthID` string

Unique identifier for the authorization of the transaction.
{% endtab %}
{% endtabs %}
