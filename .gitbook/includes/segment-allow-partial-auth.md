---
title: segment - allow partial auth
---

If you need to do partial authorizations, we offer an option named `AllowPartialAuth`.

{% hint style="info" %}
To turn on `AllowPartialAuth`, send a request to the Number team.
{% endhint %}

If this option is turned on, then it's possible for a transaction to be approved for the partial amount when the card has an available balance which is less than the amount being authorized.

In this case, we will return the approved amount and the balance due. **This remaining balanance could be collected in another form of payment or at a later date.**

with partial authorization turned on, you can monitor the following values as part of the sale response:

* `IsPartialApproval` boolean
* `ResponseAuthorizedAmount` decimal
* `ResponseBalanceAmount` decimal
* `ResponseApprovedAmount` decimal
