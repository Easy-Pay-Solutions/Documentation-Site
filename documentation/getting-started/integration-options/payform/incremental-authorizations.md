# Incremental Authorizations

You may wish to configure your PayForm to collect an Initial _Authorization Only_.

This Authorization can be Reversed or Incrementally increased during your workflow and eventually finalized and sent for settlement.  In order to Specify _Authorization Only_ adjust your [request](../../../../api-reference/rest-api/payform.md) as follows

{% code overflow="wrap" %}
```
"eFeatures": "0001",
```
{% endcode %}

This tells the PayForm that any dollar amount authorized will stay in a PENDING state awaiting any changes or Incremental increases you specify using our API.  &#x20;

Use this [REST API call](../../../../api-reference/rest-api/authentication-1.md) to execute incremental Auths or Finalize the transaction.&#x20;

