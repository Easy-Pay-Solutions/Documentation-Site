# Get your business started (WIP)

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
Contact us to sign up for a Number Sandbox account:

[partners@number.tech](mailto:partners@number.tech)  /  (866) 927-9344
{% endhint %}
{% endstep %}

{% step %}
#### **Obtain API Credentials**

After account creation, retrieve your API key, HMAC secret, and any other necessary credentials from the Number Client Admin Portal. This will be essential for authenticating your API requests.
{% endstep %}

{% step %}
#### **Choose Your Integration Method**

Decide on the integration method that best suits your business needs. Options include:

* **Web Widgets**: Use Number's pre-built widgets for collecting payment information directly on your website.
* **PayForm**: Utilize the Number API for a customizable payment form that can be integrated into your site.
* **Virtual Terminal**: Use the web application for processing payments directly through a browser.
* **Mobile SDK**: If you have a mobile application, consider integrating the Number SDK for mobile payments.

{% hint style="danger" %}
Important: Only Clients who have a PCI Level One Compliance program can pass cardholder data directly through the API. All others shall use the Payform to collect cardholder data and all other functionality can be obtained using the API
{% endhint %}


{% endstep %}

{% step %}
#### **Set Up Your Development Environment**

Depending on your chosen integration method, set up your development environment. This may involve installing SDKs, libraries, or configuring your web server to handle API requests.
{% endstep %}

{% step %}
#### **Implement Payment Processing**

Develop the necessary code to handle payment processing. This includes:

* Collecting cardholder data securely.
* Making API calls to process transactions (authorizations, credits, voids, etc.).
* Handling responses and errors appropriately.
{% endstep %}

{% step %}
#### **Test Your Integration**

Before going live, thoroughly test your integration in a sandbox environment. Ensure that all payment flows work as expected and that you can handle various transaction scenarios.
{% endstep %}

{% step %}
#### Number inspection

The Number team always needs to inspect the workflow that our clients have developed prior to allowing them to go Live.
{% endstep %}

{% step %}
#### **Go Live**

Once testing is complete and you are satisfied with the implementation, switch to the production environment. Update your API keys and configurations as necessary.
{% endstep %}

{% step %}
#### **Monitor and Maintain**

After launching, continuously monitor your payment processing for any issues. Regularly check for updates from Number and maintain your integration to ensure compliance and security.
{% endstep %}
{% endstepper %}

{% hint style="info" %}
Visit the [Integration Checklist](../documentation/getting-started/integration-checklist.md) for more details.
{% endhint %}

***

### Implementation Timeline

<table><thead><tr><th width="134">Phase</th><th width="146">Duration</th><th width="469">Task</th></tr></thead><tbody><tr><td>Obtain Sandbox Credentials</td><td>1 day</td><td></td></tr><tr><td>Investigate integration Options</td><td>1-2 days</td><td></td></tr><tr><td></td><td></td><td></td></tr><tr><td>Develop a Payment Workflow</td><td>1-2 days</td><td></td></tr><tr><td>Develop your integration</td><td>1-2 weeks</td><td></td></tr><tr><td></td><td>2-3 weeks</td><td></td></tr><tr><td></td><td>1-2 weeks</td><td></td></tr><tr><td>Unit Testing</td><td>1 to 2 weeks</td><td></td></tr></tbody></table>
