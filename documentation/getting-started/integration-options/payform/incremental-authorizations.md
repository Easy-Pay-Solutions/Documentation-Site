# Incremental Authorizations

You may wish to configure your PayForm to collect an Initial _Authorization Only_.

This Authorization can be Reversed or Incrementally increased during your workflow and eventually finalized and sent for settlement.  In order to Specify _Authorization Only_ adjust your [request](../../../../api-reference/rest-api/payform.md) as follows

{% code overflow="wrap" %}
```
"eFeatures": "0008",
```
{% endcode %}

This tells the PayForm that any dollar amount authorized will stay in a PENDING state awaiting any changes or Incremental increases you specify using our API.\
\
Be VERY CAREFUL when setting this feature value because transactions collected here will rely on you to FINALIZE them using the API. If you do an Authorization Only for a dollar value, the merchant WILL NOT collect the funds until you FINALIZE the transaction.

Use this [REST API call](../../../../api-reference/rest-api/authentication-1.md) to execute incremental Auths or Finalize the transaction.&#x20;

