---
description: Methods related to voice authorization
---

# Voice (v1)

## Query Voice Settings

<mark style="color:green;">`POST`</mark> /ICardProcess/VoiceSettingsQry

Return the information provided for a voice authorization of specific transaction.

{% tabs %}
{% tab title="Request body" %}
{% include "../../.gitbook/includes/param-sess-key.md" %}

***

{% include "../../.gitbook/includes/param-txid.md" %}
{% endtab %}

{% tab title="Response body" %}
{% include "../../.gitbook/includes/param-ok-msg-errs.md" %}

***

`VoiceSettings` api\_VoiceSettingsTX (object)

Fields: PhoneNumber, BankNumber, MerchantID, CardNumber, ExpDate, ChargeAmount, AccountHolder.
{% endtab %}
{% endtabs %}

