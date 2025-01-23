# Get your business started

At Number, we know that running a business means juggling countless tasks. That's why we've made our payment integration as simple and efficient as possible, so you can focus on what really matters—growing your business.

{% content-ref url="../documentation/developer-quickstart/" %}
[developer-quickstart](../documentation/developer-quickstart/)
{% endcontent-ref %}



***



### A few steps to get started&#x20;

To get your business started with Number, follow these general steps for implementation:

{% stepper %}
{% step %}
#### **Create a Number Account**:

Sign up for a Number Sandbox account to gain access to the platform and its features. Ensure you have all necessary business information ready for registration.

{% hint style="info" %}
Contact us to sign up for a Number Sandbox account: \
[partners@number.tech](mailto:partners@number.tech)  /  (866) 927-9344
{% endhint %}
{% endstep %}

{% step %}
#### **Obtain credentials**

After account creation, retrieve the necessary credentials from the Number Client Admin Portal. This will be essential for encryption and authentication.
{% endstep %}

{% step %}
#### **Choose your integration method**

Decide on the integration method that best suits your business needs. Options include:

* **REST API and the PayForm**: Utilize the Number API and a customizable pre-built payment form that can be integrated directly into your site.
* **Verifone**: Collect payments using Verifone card readers with our software.
* **Mobile SDK**: If you have a mobile application, use the Number SDK for in-app payments.
* **Virtual Terminal**: A web application for processing payments directly through a browser.
{% endstep %}

{% step %}
#### **Integrate our solution**

Depending on the integration method of choice, you might need to develop code to call our APIs or SDKs, or simply install some software and log in.
{% endstep %}

{% step %}
#### **Test your integration on a development environment**

Before going live, thoroughly test your integration in a sandbox environment. Ensure that all payment flows work as expected and that you can handle various transaction scenarios.
{% endstep %}

{% step %}
#### Number inspection

The Number team always inspects the workflow that our clients develop prior to going Live.
{% endstep %}

{% step %}
#### **Go live**

Once testing is complete and you are satisfied with the implementation, switch to the production environment. Update your configuration as necessary.
{% endstep %}

{% step %}
#### **Monitor and maintain**

After launching, continuously monitor your payment processing for any issues. Regularly check for updates from Number to ensure compliance and security.
{% endstep %}
{% endstepper %}

{% hint style="info" %}
You can find a detailed integration guide by visiting the [Integration Checklist](../documentation/getting-started/integration-checklist.md) section.
{% endhint %}



***



### Implementation timeline

<table><thead><tr><th width="153">Phase</th><th width="121">Sub phase</th><th width="121">Duration</th><th>Task</th></tr></thead><tbody><tr><td>Obtain Sandbox Credentials</td><td>—</td><td>1 Day</td><td><a href="../help/customer-support/">Contact the Number team</a> to obtain sandbox credentials for integration testing.</td></tr><tr><td>Investigate Integration Options</td><td>—</td><td>1-2 Days</td><td>Determine the appropriate integration method: PCI Level One clients can use a purely API integration, while others must implement a PayForm for cardholder data.</td></tr><tr><td>Develop a Payment Workflow</td><td>—</td><td>1-2 Days</td><td>Outline all interaction points for web payments, card-present transactions, back-office processes, and reporting mechanisms.</td></tr><tr><td>Develop Your Integration</td><td>Front End</td><td>1-2 weeks</td><td>Create the front-end components necessary for user interactions, ensuring a seamless payment experience.</td></tr><tr><td></td><td>EMV</td><td>1 Week</td><td>Implement EMV functionality to support chip card transactions and enhance security measures.</td></tr><tr><td></td><td>Server Side</td><td>2 - 3 Weeks</td><td>Develop the server-side logic to handle payment processing, including API calls and data management.</td></tr><tr><td></td><td>Reporting and Reconciliation</td><td>1 - 2 Weeks</td><td>Set up reporting and reconciliation processes to track transactions and ensure financial accuracy.</td></tr><tr><td>Unit Testing</td><td>—</td><td>1 - 2 Weeks</td><td>Conduct unit testing to validate the integration functionality before going live, ensuring all components work as intended.</td></tr></tbody></table>
