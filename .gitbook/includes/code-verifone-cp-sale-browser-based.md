---
title: code - verifone cp sale browser-based
---

{% tabs %}
{% tab title="JavaScript" %}
{% code overflow="wrap" lineNumbers="true" %}
```javascript
// Initiates CHIP transaction
function initiateEMVTransaction() {
    // // You must either supply a session key for Live credit card authorizations or modify your eptools profile to point to a particular account
    // You may modify your stored profile at c:\ProgramData\EasyPay\Eptools\eptools\profiles
    const sessKey = getSessKey(); //  your server application can pass this down to your client script 
    
    // Each account can have multiple merchant records. Normally this can be '1' for default if you only have one merchant on account.
    const merchID = getMerchId();
    
    // Note: any 'address' field should be an object consisting of:
    // 'Address1', 'Address2', 'City', 'State', 'ZIP', and 'Country'
    
    // The account holder and end customer JSONs should consist of:
    // 'Firstname', 'Lastname', 'address' (see above), 'Email', and 'Phone'
    const acctHolderJson = getAcctHolderJson();
    const endCustJson = getEndCustJson();
    
    // Purchase details should consist of the following fields:
    // 'REFID' and 'RPGUID' (your custom defined values), and 'ServiceDesc'
    const purchDetailsJson = getPurchDetailsJson();

    // The amount needs to be stripped from '$' and ',' symbols
    let amount = getAmount();
    amount = amount.replace('$', "").replace(',', ""); 

    const url = `https://localhost:8031/VerifoneSVC/service/GetEmvJson?SessKey=${sessKey}&AcctHolderJson=${acctHolderJson}&EndCustJson=${endCustJson}&PurchDetailsJson=${purchDetailsJson}&MerchID=${merchID}&Amount=${amount}`;

    // Make the call to the service and do basic error/success handling
    $.ajax({
        type: "GET",
        url: url,
        success: function (data) {
            // Hex to byte array, then UTF text, and alert the XML object
            alert(stringFromUTF8Array(hexToBytes(data)));
        },
        error: function (xhr, status, error) {
            console.error("Verifone Middleware Error", {
                statusCode: xhr.status,
                statusText: xhr.statusText,
                error: error
            });
            alert(`Verifone Middleware Error: ${error}`);
        }
    });
}
```
{% endcode %}
{% endtab %}
{% endtabs %}
