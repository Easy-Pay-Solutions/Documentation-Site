# Integration Checklist (WIP)

#### **Create a Number account and obtain credentials: 1-2 days**

Sign up for a Number Sandbox account to gain access to the platform and its features. Ensure you have all necessary business information ready for registration.

{% hint style="info" %}
Contact us to sign up for a Number Sandbox account: \
[partners@number.tech](mailto:partners@number.tech)  /  (866) 927-9344
{% endhint %}

After account creation, retrieve the necessary credentials from the Number Client Admin Portal. This will be essential for encryption and authentication.

#### **Choose your integration methods: 1-2 days**

Decide on [integration options](integration-options/) that best suit your business needs. Options include:

* **REST API and the PayForm**: Utilize the Number API and a customizable pre-built payment form that can be integrated directly into your site.
* **Verifone**: Collect payments using Verifone card readers with our software.
* **Mobile SDK**: If you have a mobile application, use the Number SDK for in-app payments.
* **Virtual Terminal**: A web application for processing payments directly through a browser.

For example: PCI Level One clients can use a purely API integration, while others would need to implement a PayForm for collecting cardholder data through their website.

#### Develop a payment workflow: 1-2 days

Outline all interaction points in your current workflow where payments might be collected.

Define your requirements for various types of payment processes and equipment (card readers, web payments, card-present transactions, back-office processes, and reporting mechanisms).

#### Develop the frontend components: 1-2 weeks

Create the frontend components necessary for user interaction.

#### Develop the EMV integration (optional): 1 week

If you want to support Verifone card chip readers, you'll need to implement EMV functionality to support chip card transactions and enhance security measures.

#### Develop the backend integration: 2-3 weeks

Write the server-side logic to handle payment processing, invoking our services.\
\
Develop data management, coupling your users with the payment activities by storing consent or transaction IDs, and optionally storing transaction amounts for reconciliation.

#### Develop the processes for logging, reporting, and reconciliation: 1 week

Setup logging according to our guides. Consult us to set up reporting and reconciliation processes. They will allow you to track transactions and ensure financial accuracy.

#### **Test your integration on a development environment: 1-2 weeks**

Before going live, thoroughly test your integration in a sandbox environment. Ensure that all payment flows work as expected and that you can handle various transaction scenarios.\
\
Conduct unit testing to validate the integration functionality before going live, ensuring all components work as intended.

#### Number inspection

The Number team always inspects the workflow that our clients develop prior to going live.

#### **Go live: 1 day**

Once testing is complete and you are satisfied with the implementation, switch to the production environment. Update your configuration as necessary.
