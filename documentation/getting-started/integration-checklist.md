---
description: The comprehensive checklist to integrating with Number
---

# Integration Checklist

Integrating payment processing into your system can be a daunting task. To help you on this journey, we've prepared a checklist which describes all the steps required from creating a Number account to going live, including the design, development, and testing.



{% stepper %}
{% step %}
**Create a Number account and obtain credentials: 1-2 days**

Sign up for a Number Sandbox account to gain access to the platform and its features. Ensure you have all necessary business information ready for registration.

{% hint style="info" %}
Contact us to sign up for a Number Sandbox account: \
[partners@number.tech](mailto:partners@number.tech)  /  (866) 927-9344
{% endhint %}

After account creation, retrieve the necessary credentials from the Number Client Admin Portal. This will be essential for encryption and authentication.
{% endstep %}

{% step %}
**Choose your integration methods: 1-2 days**

Read about the [integration-options](integration-options/ "mention") and decide which one best suit your business needs. Options include:

* **REST API and the PayForm**: Utilize the Number API and a customizable pre-built payment form that can be integrated directly into your site.
* **Verifone**: Collect payments using Verifone card readers with our software.
* **Mobile SDK**: If you have a mobile application, use the Number SDK for in-app payments.
* **Virtual Terminal**: A web application for processing payments directly through a browser.

{% hint style="info" %}
You can find guides that will help you learn how to navigate each integration method on the [integration-options](integration-options/ "mention") page.
{% endhint %}

For example: PCI Level 1 clients can use a purely API integration, while others would need to implement a PayForm for collecting cardholder data directly through their website.&#x20;
{% endstep %}

{% step %}
**Develop a payment workflow: 1-2 days**

Outline all interaction points in your current workflow where payments might be collected.

Define your requirements for various types of payment processes and equipment (card readers, web payments, card-present transactions, back-office processes, and reporting mechanisms).
{% endstep %}

{% step %}
**Develop the frontend components: 1-2 weeks**

{% hint style="info" %}
If you are using the mobile SDKs or the Virtual Terminal, you can skip this step as you won't need to develop any additional frontend or UI components.
{% endhint %}

Create the frontend components necessary for user interaction.
{% endstep %}

{% step %}
**Develop the EMV integration: 1 week**

{% hint style="info" %}
Unless you want to use Verifone card readers or other card readers, you can skip this step as you won't need the EMV integration.
{% endhint %}

Implement EMV functionality provided by our Windows service or SDK to support chip card transactions. Read the [verifone.md](integration-options/verifone.md "mention") guide to learn how to use these services.
{% endstep %}

{% step %}
**Develop the backend integration: 2-3 weeks**

{% hint style="info" %}
Depending on the scope of your integration, it might take less time.\
Also, you can skip this step if you only plan on only using the Virtual Terminal.&#x20;
{% endhint %}

Write the server-side logic to handle payment processing, invoking our services.\
\
Develop data management, coupling your users with the payment activities by storing consent or transaction IDs, and optionally storing transaction amounts for reconciliation.
{% endstep %}

{% step %}
**Develop the processes for logging, reporting, and reconciliation: 1 week**

Set up basic logging where applicable. Consult us to set up reporting and reconciliation processes. They will allow you to track transactions and ensure financial accuracy.
{% endstep %}

{% step %}
**Test your integration on a development environment: 1-2 weeks**

Before going live, thoroughly test your integration in a sandbox environment. Ensure that all payment flows work as expected and that you can handle various transaction scenarios. You can read more about using the sandbox in the [testing](../testing/ "mention") section.\
\
Conduct unit testing to validate the integration functionality before going live, ensuring all components work as intended.
{% endstep %}

{% step %}
N**umber inspection: 1-2 meetings**

The Number team always inspects the workflow that our clients develop prior to going live.
{% endstep %}

{% step %}
**Go live: 1 day**

Once testing is complete and you are satisfied with the implementation, switch to the production environment. Update your configuration as necessary.
{% endstep %}

{% step %}
**Monitor and maintain: continuous**

Once you go live, monitor your integration to make sure there are no problems. Work on improvements and fixes as required.
{% endstep %}
{% endstepper %}



