---
description: Learn to make credit card sales with Number
---

# Credit Card Sale (WIP)

## Card present sales

To make credit card present sales using Number, you have several options:

{% stepper %}
{% step %}
**Integration with a Verifone card reader**

You can use Verifone card readers, which are secure devices that connect to your computer via USB. They encrypt cardholder data during transmission to ensure security.
{% endstep %}

{% step %}
#### Any USB card reader through the Virtual Terminal

When you have a USB card reader connected to your machine, you can log into the Virtual Terminal to make card present sales.&#x20;
{% endstep %}

{% step %}
#### Any USB card reader through our custom desktop application

We have a custom desktop application which can be convenient in an office setting to collect card present payments. It offers much of the same functionality as the Virtual Terminal.
{% endstep %}

{% step %}
#### A custom integration with our REST API or SOAP API

Both our REST API and SOAP API offer methods for handling card present transactions.

If you have your own PCI level one compliance program, you may use our APIs and write your own custom code calling our APIs to collect card present payments. You can read more about PCI compliance in our short [#pci-compliance](../getting-started/integration-options/#pci-compliance "mention") guide.
{% endstep %}
{% endstepper %}

### <mark style="background-color:orange;">Verifone integration</mark>

To use Number with your Verifone card reader, see our [verifone.md](../getting-started/integration-options/verifone.md "mention") integration guide. There are a few approaches to integration, but we recommend to download and install our Win service.



### <mark style="background-color:orange;">Virtual Terminal</mark>

When you expand _Credit Cards_ in the navigation on the left, you'll have options for a sale, an EMV sale, authorization, forced auth, and adjustments.

To learn more about using the Virtual Terminal, see the [virtual-terminal.md](../getting-started/integration-options/virtual-terminal.md "mention") user guide.



### <mark style="background-color:orange;">Custom desktop application</mark>

Read more in the [integration-options](../getting-started/integration-options/ "mention") guide or [contact Number](../../help/customer-support/) to get access.



### <mark style="background-color:orange;">REST API or SOAP API integration</mark>



{% include "../../.gitbook/includes/warning-pci-compliant-only.md" %}

You can use the following API operations:

* For the REST API, use [#apicardprocrest-v1.0.0-cardsale-cardpresent](../../api-reference/rest-api/card-operations/process-a-card-sale.md#apicardprocrest-v1.0.0-cardsale-cardpresent "mention")
* For the SOAP API, use [#card-present-sales](credit-card-sale-wip.md#card-present-sales "mention").









***



## <mark style="background-color:orange;">Manual card sales</mark>

To make manual credit card sales using Number, you have the following options:

1. **Manual Card Sale via API**:
   * You can process a manual card sale using the`/ICardProcess/CreditCardSale_Manual`API endpoint. This requires sending a POST request with the necessary credit card information, including the account number, expiration date, CVV, and account holder details 1 .
   * **Request Parameters**:
     * `SessKey`: A unique session key for authentication.
     * `ccCardInfo`: Contains the credit card details (AccountNumber, ExpMonth, ExpYear, CSV).
     * `AcctHolder`: Information about the account holder 2 1 .
2. **Using the Android SDK**:
   * If you are developing an Android application, you can utilize the Number Android SDK to charge credit cards manually. The method`ChargeCreditCard().chargeCreditCard(params: ChargeCreditCardBodyParams)`allows you to process credit card transactions by entering the card details manually 3 .
   * **Request Parameters**:
     * `encryptedCardNumber`: Securely handle the card number.
     * `creditCardInfo`: Include details like expiration date and CVV.
     * `accountHolder`: Information about the cardholder 3 .
3. **Virtual Terminal**:
   * The Virtual Terminal is a web application that allows you to manually enter credit card details and process transactions through your browser. This option is suitable for businesses that need to process payments without a physical terminal 4 5 .

#### Steps to Implement:

* **Choose Your Method**: Decide whether to use the API, Android SDK, or Virtual Terminal based on your application needs.
* **Set Up Authentication**: Ensure you have a valid`SessKey`for API calls or integrate the SDK properly in your application.
* **Send Transaction Data**: For API, format your request body with the required parameters and send it to the specified endpoint. For the SDK, use the provided methods to handle transactions.
* **Test Your Integration**: Use a sandbox environment to test your implementation before going live 5 .

For detailed implementation instructions, refer to the specific documentation for each method.
