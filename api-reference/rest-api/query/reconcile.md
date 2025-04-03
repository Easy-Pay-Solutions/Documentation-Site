---
description: >-
  The reconcile query is designed to be called at a specific periodic interval,
  perhaps once per day. We will return all the unique transaction IDs
  encountered during that interval.  This can be called
---

# Reconcile

IMPORTANT: Do not call this method more than once a day. Excessive queries can cause your endpoint to be blocked. The max date range for this method is 31 days. The max records returned is 20,000. If you notice that the NumRecords returned equals 20000 then this means you have maxed out your query and you should use a smaller date range.

{% openapi src="../../../.gitbook/assets/master-openapi-rest.yaml" path="/APIcardProcREST/v1.0.0/Query/Reconcile" method="post" %}
[master-openapi-rest.yaml](../../../.gitbook/assets/master-openapi-rest.yaml)
{% endopenapi %}
