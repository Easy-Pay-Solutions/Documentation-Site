---
description: Methods related to batch transactions
---

# Batch

## Query Batch Log

<mark style="color:green;">`POST`</mark> /ICardProcess/Batch\_Log\_Query

Return batch processing details. Batches are used for settling open transactions.

{% tabs %}
{% tab title="Request body" %}
***
{% endtab %}

{% tab title="Response body" %}
***

***

`BatchLogs` array<[api\_batchSettleLog](soap-object-dictionary.md#api_batchsettlelog)> (array\<object>)

Fields: ID, BatchNO, BatchAmt, BatchRecs, TxLOCK, CreatedOn, FinishedOn, CreatedBy, MerchID, SettleResp, Code, BatchOpen, BatchClose, Released.
{% endtab %}
{% endtabs %}



