---
description: Methods related to authentication
---

# Authentication (v1)

## Authenticate

<mark style="color:green;">`POST`</mark> /ICardProcess/Authenticate

Authenticates the user. The method returns a session key that is used on subsequent method calls, the account details, and a list of merchants associated with the account.&#x20;

{% include "../../.gitbook/includes/block-reauthenticate.md" %}

{% tabs %}
{% tab title="Request body" %}
{% include "../../.gitbook/includes/param-account-code.md" %}

***

{% include "../../.gitbook/includes/param-token.md" %}
{% endtab %}

{% tab title="Response body" %}
{% include "../../.gitbook/includes/param-ok-msg-errs.md" %}

***

{% include "../../.gitbook/includes/param-sess-key.md" %}

***

`ThisUser` [api\_AuthUser](soap-object-dictionary-wip.md#api_authuser) (object)

An object describing the user account.

Fields: ID< AccountCode, AcctID, APILocationID, ExpirationDate, DateCreated, DateModified, CreatedBy, IsExpired, IsLockedOut, Alias, Description, TokenDescription

***

`MerchantList` List<[api\_MerchantInfo](soap-object-dictionary-wip.md#api_merchantinfo)> (array\<object>)

An array with basic information about all of the merchants visible to the logged-in user.

Fields: ID, Descrip, TermID, Location, Address
{% endtab %}
{% endtabs %}

{% code title="Sample response" overflow="wrap" fullWidth="false" %}
```xml
<soapenv:Envelope xmlns:soapenv="http://schemas.xmlsoap.org/soap/envelope/"
                  xmlns:ns="http://example.com/soapapi">
   <soapenv:Header/>
   <soapenv:Body>
      <ns:api_AuthResponse>
         <ns:FunctionOk>true</ns:FunctionOk>
         <ns:AuthSuccess>true</ns:AuthSuccess>
         <ns:RespMsg>SessKey Expires|4/18/2019 7:29:47 AM</ns:RespMsg>
         <ns:ErrMsg></ns:ErrMsg>
         <ns:ErrCode>0</ns:ErrCode>
         <ns:SessKey>B9F24903C3BA4770AE303032303541303032353437</ns:SessKey>
         <ns:ThisUser>
            <ns:ID>2547</ns:ID>
            <ns:AccountCode>EP9116875</ns:AccountCode>
            <ns:AcctID>205</ns:AcctID>
            <ns:APILocationID>2210</ns:APILocationID>
            <ns:ExpirationDate>2019-09-11T16:12:00-04:00</ns:ExpirationDate>
            <ns:DateCreated>2019-03-11T12:32:00-04:00</ns:DateCreated>
            <ns:DateModified>2019-03-11T12:32:00-04:00</ns:DateModified>
            <ns:CreatedBy>ADMIN : vidya Venkatraman</ns:CreatedBy>
            <ns:IsExpired>false</ns:IsExpired>
            <ns:IsLockedOut>false</ns:IsLockedOut>
            <ns:Alias>vidya_Venkatraman</ns:Alias>
            <ns:Description>EP DEV ACCT</ns:Description>
            <ns:TokenDescription>EP DEV ACCT</ns:TokenDescription>
         </ns:ThisUser>
         <ns:MerchantList>
            <ns:MerchantInfo>
               <ns:ID>1</ns:ID>
               <ns:Descrip>Test Merchant 1</ns:Descrip>
               <ns:TermID>006</ns:TermID>
               <ns:Location>Test Merchant 1</ns:Location>
               <ns:Address>45 spring street portland Maine 04101</ns:Address>
            </ns:MerchantInfo>
            <ns:MerchantInfo>
               <ns:ID>2</ns:ID>
               <ns:Descrip>Lodging Merch</ns:Descrip>
               <ns:TermID>033</ns:TermID>
               <ns:Location>Lodging Merch</ns:Location>
               <ns:Address>78 spring street portland Maine 04101</ns:Address>
            </ns:MerchantInfo>
         </ns:MerchantList>
      </ns:api_AuthResponse>
   </soapenv:Body>
</soapenv:Envelope>
```
{% endcode %}



