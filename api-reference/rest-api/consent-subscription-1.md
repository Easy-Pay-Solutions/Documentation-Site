---
hidden: true
---

# Consent Subscription Old

{% openapi src="../../.gitbook/assets/master-openapi-rest.yaml" path="/APIcardProcREST/v1.0.0/ConsentSubscription/Modify" method="post" %}
[master-openapi-rest.yaml](../../.gitbook/assets/master-openapi-rest.yaml)
{% endopenapi %}

**Notes**&#x20;

**In most cases you may only want to modify a single parameter such as PaymentAdjustDate or OnHold. You can supply a value of -1 or "-1" to any value which you do not want us to alter.  The following example shows how to simply remove the hold from ConsentID 21.**&#x20;

&#x20;{\
"ConsentID": 21,\
"ConsentMods": {\
&#x20;   "ExpMonth": -1,\
&#x20;   "ExpYear": -1,\
&#x20;   "Email": "-1",\
&#x20;   "Zip": "-1",\
&#x20;   "RPGUID": "-1",\
&#x20;   "CustomerRefID": "-1",\
&#x20;   "ServiceDescrip": "-1",\
&#x20;   "PaymentAmt": -1,\
&#x20;   "PaymentAdjustDate": "-1",\
&#x20;   "OnHold": false\
&#x20;  }\
}



