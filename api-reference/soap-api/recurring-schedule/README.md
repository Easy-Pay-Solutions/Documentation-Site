---
description: Methods related to modifying recurring schedules
---

# Recurring Schedule

## Modify Recurring Schedule

<mark style="color:green;">`POST`</mark> /ICardProcess/RecurringSchedule\_Modify

Modifies the schedule of a specific recurring consent.

{% tabs %}
{% tab title="Request body" %}
{% include "../../../.gitbook/includes/param-sess-key.md" %}

***

{% include "../../../.gitbook/includes/param-scheduleid.md" %}

***

`PaymentAmount` decimal

Payment $ amount of the rescheduled recurring consent.

***

`DueDate` string

Due date of the rescheduled recurring consent.
{% endtab %}

{% tab title="Response body" %}
{% include "../../../.gitbook/includes/param-ok-msg-errs.md" %}

***

{% include "../../../.gitbook/includes/param-scheduled-payment.md" %}
{% endtab %}
{% endtabs %}





## Cancel Recurring Schedule

<mark style="color:green;">`POST`</mark> /ICardProcess/RecurringSchedule\_Cancel

Cancel a specific payment that is part of the recurring schedule.

{% tabs %}
{% tab title="Request body" %}
{% include "../../../.gitbook/includes/param-sess-key.md" %}

***

{% include "../../../.gitbook/includes/param-scheduleid.md" %}
{% endtab %}

{% tab title="Response body" %}
{% include "../../../.gitbook/includes/param-ok-msg-errs.md" %}

***

{% include "../../../.gitbook/includes/param-scheduled-payment.md" %}
{% endtab %}
{% endtabs %}



