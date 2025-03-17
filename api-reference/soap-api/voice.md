---
description: Methods related to voice authorization
---

# Voice

## Query Voice Settings

<mark style="color:green;">`POST`</mark> /ICardProcess/VoiceSettingsQry

Return the information provided for a voice authorization of specific transaction.

{% tabs %}
{% tab title="Request body" %}
***
{% endtab %}

{% tab title="Response body" %}
***

`VoiceSettings` api\_VoiceSettingsTX (object)

Fields: PhoneNumber, BankNumber, MerchantID, CardNumber, ExpDate, ChargeAmount, AccountHolder.
{% endtab %}
{% endtabs %}



