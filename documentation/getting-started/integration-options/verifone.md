---
description: Getting started with Verifone for Number
---

# Verifone

The Verifone card readers are small hand-held devices. They communicate with your computer on a USB port. A chip transaction is comprised of about a dozen transmissions between the host (your computer) and the device, and then finally to the Number cloud platform.

Using the Verifone card readers offers a highly secure method of collecting cardholder data.

Cardholder data is encrypted within the device itself, and remains encrypted as it travels across the Internet to our PCI Level One Compliant processing platform.&#x20;

{% hint style="info" %}
When a merchant supports a Verifone card reader, it helps eliminate chargebacks for transactions which were run through the device.
{% endhint %}

<figure><img src="../../../.gitbook/assets/Verifone (1).png" alt=""><figcaption></figcaption></figure>



### PCI SSC SSF <a href="#pci-ssc-software-security-framework-ssf" id="pci-ssc-software-security-framework-ssf"></a>

Software Security Framework (SSF) is a re-working of the existing PCI standard PA DSS. The PA DSS has been retired since June 30, 2021. Number's "Aspen 3.1" is the first application to achieve the PCI Councils SSF certification, and it provides an end-to-end encrypted solution.

<figure><img src="../../../.gitbook/assets/Card Present Data transfer B.png" alt=""><figcaption></figcaption></figure>



***



## Software options <a href="#what-we-offer" id="what-we-offer"></a>

Currently, we offer three different options for collecting payments with the Verifone card readers, all of which require a Windows OS on the host computer.

{% stepper %}
{% step %}
**Standalone desktop application (upon request)**

This application has automatic updates and allows you to collect payments, create card-on-file and payment plans, process a card-on-file, void or credit, settle transactions, and do reporting with an option to export to a PDF.
{% endstep %}

{% step %}
**Browser-based interface**

We developed a Windows service which uses Cross-Origin Resource Sharing (CORS) to communicate with the browser. The Win service will return a simple XML response for each transaction directly to the HTML/PHP/ASP.NET page for consumption by the host application.

As an integrator, this allows you to write simple client-side scripts within your own web applications to initiate transactions with a local Verifone. **You can also use this service with the Virtual Terminal to avoid writing any code.**
{% endstep %}

{% step %}
**Number Verifone SDK**

This Managed Code DLL provides a means of connecting your custom windows application to the Verifone device. Used in conjunction with our API, you can manage all aspects of your payment requirements, all within the confines of your own custom application.
{% endstep %}
{% endstepper %}



#### **Requirements**

There are 2 categories of integrations which require two different sets of files

1. Browser-based - install our Win service which contains all your dependencies, including the drivers and console installer.
2. Desktop-based - install our SDK, then use separate installers for drivers and a custom event log.



## Desktop application <a href="#easy-pay-verifone-sdk" id="easy-pay-verifone-sdk"></a>

<figure><img src="../../../.gitbook/assets/Number Desktop Application.png" alt=""><figcaption></figcaption></figure>

If you wish to use the standalone desktop application for Verifone, [contact Number ](../../../help/customer-support/)for installation files and instructions.



## Browser-based installation <a href="#browser-based-installation" id="browser-based-installation"></a>

For any browser-based Implementation using the Verifone, you will need to install the local win service. This includes our Virtual Terminal application as well as your own custom web applications.

<figure><img src="../../../.gitbook/assets/Number VX Module.jpg" alt=""><figcaption></figcaption></figure>

To Begin: Download the compressed archive:

{% include "../../../.gitbook/includes/link-verifone-windows-service.md" %}

**To install the Win service:**

{% stepper %}
{% step %}
Connect your device to a free USB port.
{% endstep %}

{% step %}
Allow the device to initialize.
{% endstep %}

{% step %}
Extract the above archive to a location of your choice.
{% endstep %}

{% step %}
Locate the EXE file and right click on it to choose _Run as administrator_.
{% endstep %}

{% step %}
Wait for the application to finish, then reboot computer.
{% endstep %}
{% endstepper %}

The above installation package does the following:

1. Installs USB drivers for the Verifone.
2. Creates a custom event log with Windows named _EPmiddleware_.
3. Installs a certificate which encrypts data between the browser and the Windows service.
4. Installs the _EasyPay Verifone MiddleWare E2E 1041 Service_ which listens on port 8031.

Your website can now issue commands to the Win Service as is demonstrated using the sample site:&#x20;

{% embed url="https://easypay1.com/JqueryVerifone/" %}
[https://easypay1.com/JqueryVerifone/](https://easypay1.com/JqueryVerifone/)
{% endembed %}

You can download the entire site here:

{% embed url="https://easypay1.com/docs/jquery_verifone.zip" %}
https://easypay1.com/docs/jquery\_verifone.zip
{% endembed %}

{% hint style="warning" %}
To run the Verifone demo website, you must have the Verifone Windows service installed.
{% endhint %}

### Virtual Terminal

You can use our Virtual Terminal together with the Windows service. It has built-in support for Verifone. This way, you won't have to build your own UI or write any code. After installing the service, [contact Number](../../../help/customer-support/) to have this feature activated.

You can read more about using the Virtual Terminal in the [virtual-terminal.md](virtual-terminal.md "mention") guide.



### Requesting a transaction from your custom web application

You will find a script file named EasyPayVerifone.js which has provided the following functionality:

1. EMV sale only
2. EMV sale and save card
3. Manual sale (keyed entry) sale only
4. Manual sale and save card
5. EMV save card only
6. Reset the Middleware and Verifone

#### Verifone EMV sale only

Here's an simplified example of how you can invoke the service for a sale:

{% include "../../../.gitbook/includes/code-verifone-cp-sale-browser-based.md" %}

#### Verifone EMV annual consent only

Here's an simplified example of how you can invoke the service to collect annual consent:

{% include "../../../.gitbook/includes/code-verifone-cp-annual-consent-browser-based.md" %}

#### Verifone EMV sale combo

To make a chip sale and store the card on file, follow the previous examples and replace the URL using the template below:

<pre class="language-javascript" data-overflow="wrap"><code class="lang-javascript"><strong>const url = `https://localhost:8031/VerifoneSVC/service/GetEmvComboJson?SessKey=${sessKey}&#x26;AcctHolderJson=${acctHolderJson}&#x26;EndCustJson=${endCustJson}&#x26;PurchDetailsJson=${purchdetailsJson}&#x26;MerchID=${merchID}&#x26;Amount=${amount}&#x26;SaveCard=true`
</strong></code></pre>

#### Verifone manual sale only

To make a manual sale, follow the previous examples and replace the URL using the template below:

{% code overflow="wrap" %}
```javascript
const url = `https://localhost:8031/VerifoneSVC/service/GetManualJson?SessKey=${sessKey}&AcctHolderJson=${acctHolderJson}&EndCustJson=${endCustJson}&PurchDetailsJson=${purchDetailsJson}&MerchID=${merchID}&Amount=${amount}`;
```
{% endcode %}

#### Verifone manual sale combo

To make a manual sale and store the card on file, follow the previous examples and replace the URL using the template below:

{% code overflow="wrap" %}
```javascript
const url = `https://localhost:8031/VerifoneSVC/service/GetManualComboJson?SessKey=${sessKey}&AcctHolderJson=${acctHolderJson}&EndCustJson=${endCustJson}&PurchDetailsJson=${purchDetailsJson}&MerchID=${merchID}&Amount=${amount}&SaveCard=true`;
```
{% endcode %}



### Resetting the device

The red button on the Verifone can be used to cancel the current operation and set up for _Ready_ state in most cases. See the `resetVerifone` and `unlockVerifone` functions.

{% code overflow="wrap" lineNumbers="true" %}
```javascript
//  Sends a reset command to the Verifone device
function resetVerifone() {
    $.ajax({
        type: "GET",
        url: "https://localhost:8031/VerifoneSVC/service/GetCard?Option=10",

        success: function (data) {
            var responseArray = data.split("|"); // parse response
            
            // example of showing the results and 
            // clearing the message after a timeout
            $('#StatusLabel').html(responseArray[1]); 
            setTimeout("$('#StatusLabel').html('')", 3000);
        },
        error: function (xhr, status, error) {
            console.error("Verifone Middleware Error", {
                statusCode: xhr.status,
                statusText: xhr.statusText,
                error: error
            });
            alert(`Verifone Middleware Error: ${error}`);
        }
    });
}

// Sends an unlock command to the Verifone device
function unlockVerifone() {
    $.ajax({
        type: "GET",
        url: "https://localhost:8031/VerifoneSVC/service/GetCard?Option=911",

        success: function (data) {
            var responseArray = data.split("|"); // parse response
            
            // example of showing the results and 
            // clearing the message after a timeout
            $('#StatusLabel').html(responseArray[1]);
            setTimeout("$('#StatusLabel').html('')", 3000);

        },
        error: function (xhr, status, error) {
            console.error("Verifone Middleware Error", {
                statusCode: xhr.status,
                statusText: xhr.statusText,
                error: error
            });
            alert(`Verifone Middleware Error: ${error}`);
        }
    });
}

```
{% endcode %}

The `resetVerifone` function will send a reset command to the Verifone device. This can be used to put the device back into _Ready_ state.

The `unlockVerifone` function will release the middleware from its current wait state or workflow and also send a reset command to the device.&#x20;

{% hint style="warning" %}
If you continue to receive a _Busy_ response from the middleware, but you don't believe that waiting will yield productive results, you may use the `unlockVerifone` function to return the device to _Ready_ state.
{% endhint %}



### Middleware response types

For browser type Verifone operations, the middleware provides a response object in XML format. This object can be de-serialized or can be consumed as XML. Currently, there are two response object types:

1. `WidgetArgs` - sale response when **requesting an authorization for a non-zero dollar amount**, with the option to save the card;
2. `WidgetArgs2` - consent response when **requesting to only save the card**.



### Consuming the sale response

It is important to consume the `WidgetArgs` response in a particular order, starting with `TxEventTyp`.

{% include "../../../.gitbook/includes/info-verifone-friendly-response.md" %}

{% code title="Response example" overflow="wrap" %}
```xml
<?xml version="1.0" encoding="utf-16"?>
<WidgetArgs xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xmlns:xsd="http://www.w3.org/2001/XMLSchema">
    <TxEventTyp>TxApproved</TxEventTyp>
    <ApprovedAmt>20</ApprovedAmt>
    <IsPartialApproval>false</IsPartialApproval>
    <RespMsg>APPROVED 801193</RespMsg>
    <ErrMsg />
    <TxnCode>801193</TxnCode>
    <TxID>19969</TxID>
    <ErrCode>0</ErrCode>
    <Mask>4663xxxxxxxx2741</Mask>
    <cardType>Visa</cardType>
    <ConsentResult>
        <ConsentCreated>true</ConsentCreated>
        <ConsentRequested>true</ConsentRequested>
        <ErrMsg />
        <ErrCode>0</ErrCode>
        <ConsentID>7849</ConsentID>
        <CardLast4>2741</CardLast4>
        <ExpDate>0528</ExpDate>
    </ConsentResult>
</WidgetArgs>
```
{% endcode %}

***

`TxEventTyp` string

The type of event that occurred during the transaction, indicating success or failure.

Values: TxApproved, TxDecline, TxReversed, PreSaleDeviceCode, PostSaleDeviceCode, TimeOut, AspenError, AuthFail, FunctionFail, Exception.

***

Here are actions to take for each possible value of `TxEventTyp`:

{% stepper %}
{% step %}
**TxApproved**

The sale was approved by the issuer. You should examine and store these values:

* `TxID` - the unique ID of the transaction; needed to refund or void the transaction.
* `TxnCode` - the transaction approval code.
* `ApprovedAmt` - the $ amount charged to the card.
{% endstep %}

{% step %}
**TxDecline**

The sale was declined by the issuer. You should examine and store these values:

* `TxID` - the unique ID of the declined transaction.
* `TxnCode` - the transaction decline code.
{% endstep %}

{% step %}
**TxReversed**

The issuer approved the transaction, however, during the final interaction with the chip, the device required the transaction to be declined, and the transaction was voided (reversed).
{% endstep %}

{% step %}
**PreSaleDeviceCode**

An error occurred within the device prior to the transaction getting submitted to the issuer. Examine `ErrCode` and `ErrMsg` for more information.
{% endstep %}

{% step %}
**PostSaleDeviceCode**

An error occurred within the device after the transaction was submitted to the issuer. Examine `ErrCode` and `ErrMsg` for more information.
{% endstep %}

{% step %}
**Timeout**

The user waited too long to insert the card or interact with the device. Examine `ErrCode` and `ErrMsg` for more information.
{% endstep %}

{% step %}
**AspenError**

An error occurred on Number Aspen Cloud processing servers. Examine `ErrCode` and `ErrMsg` for more information.
{% endstep %}

{% step %}
**AuthFail**

When doing a save card only operation, the issuer declined to verify the card details when executing a $0 authorization. The card will not be saved. You should examine:

* `TxID` - the unique ID of the declined transaction.
* `TxnCode` - the transaction decline code.
{% endstep %}

{% step %}
**FunctionFail**

Returned when you supply improper or out of range values in the request, or when you execute a Verifone command while the previous action has not yet completed. Examine `ErrCode` and `ErrMsg` for more information.
{% endstep %}

{% step %}
**Exception**

An error was encountered in the local Windows service. Examine `ErrCode` and `ErrMsg` for more information.
{% endstep %}
{% endstepper %}



### Consuming the consent response

It is important to consume the `WidgetArgs2` response in a particular order, starting with `ConsentEventTyp`.

{% include "../../../.gitbook/includes/info-verifone-friendly-response.md" %}

{% code title="Response example" overflow="wrap" %}
```xml
<?xml version="1.0" encoding="utf-16"?>
<WidgetArgs2 xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xmlns:xsd="http://www.w3.org/2001/XMLSchema">
    <ConsEventTyp>ConsentSuccess</ConsEventTyp>
    <AuthSuccess>true</AuthSuccess>
    <AuthMsg>APPROVED 632641|CVV||AVS|0</AuthMsg>
    <AuthTxID>16809</AuthTxID>
    <RespMsg>Success : Created Consent ID : 001270</RespMsg>
    <ErrMsg />
    <ConsentID>1270</TxnCode>
    <ErrCode>0</ErrCode>
    <Mask>4663xxxxxxxx2741</Mask>
    <cardType>Visa</cardType>
</WidgetArgs>
```
{% endcode %}

***

`ConsentEventTyp` string

The type of event that occurred during the save card on file operation, indicating success or failure.

Values: ConsentSuccess, ConsentFailed, PreConDeviceCode, PostConDeviceCode, TimeOut, AspenError, AuthFail, FunctionFail, Exception.

***

Here are actions to take for each possible value of `ConsentEventTyp`:

{% stepper %}
{% step %}
**ConsentSuccess**

The consent was created and card was saved successfully. You should examine and store `ConsentID` to be able to charge the customer later.
{% endstep %}

{% step %}
**ConsentFailed**

The consent was not created. Examine `ErrCode` and `ErrMsg` for more information.
{% endstep %}

{% step %}
**PreConDeviceCode**

An error occurred within the device prior to the card being submitted. Examine `ErrCode` and `ErrMsg` for more information.
{% endstep %}

{% step %}
**PostConDeviceCode**

An error occurred within the device after the data was submitted. Examine `ErrCode` and `ErrMsg` for more information.
{% endstep %}

{% step %}
**Timeout**

The user waited too long to insert the card or interact with the device. Examine `ErrCode` and `ErrMsg` for more information.
{% endstep %}

{% step %}
**AspenError**

An error occurred on Number Aspen Cloud processing servers. Examine `ErrCode` and `ErrMsg` for more information.
{% endstep %}

{% step %}
**AuthFail**

When doing a save card only operation, the issuer declined to verify the card details when executing a $0 authorization. The card will not be saved.
{% endstep %}

{% step %}
**FunctionFail**

Returned when you supply improper or out of range values in the request, or when you execute a Verifone command while the previous action has not yet completed. Examine `ErrCode` and `ErrMsg` for more information.
{% endstep %}

{% step %}
**Exception**

An error was encountered in the local Windows service. Examine `ErrCode` and `ErrMsg` for more information.
{% endstep %}
{% endstepper %}



***



## Number Verifone SDK <a href="#easy-pay-verifone-sdk" id="easy-pay-verifone-sdk"></a>

<figure><img src="../../../.gitbook/assets/Number .Net Application.png" alt=""><figcaption></figcaption></figure>

For you to directly interface with the Verifone using our SDK, you will need the Verifone drivers with the custom logging package, and the SDK reference files:

{% include "../../../.gitbook/includes/link-verifone-usb-log.md" %}

{% include "../../../.gitbook/includes/link-verifone-sdk.md" %}

When installed, the first component will provide USB drivers and create a virtual COM 9 port. In addition, it will add a unique event log to the existing windows event log collection.&#x20;

To install the first component, please do the following:

{% stepper %}
{% step %}
Connect your Verifone to the USB port which you plan to utilize.
{% endstep %}

{% step %}
Wait until the device is fully initialized.
{% endstep %}

{% step %}
Download and extract the ZIP file named _Setup\_USB\_log.zip_ to the location of your choice.
{% endstep %}

{% step %}
Right click the EXE named _Setup\_USB\_log.exe_ and choose _Run as administrator_.
{% endstep %}

{% step %}
After installation, there should be a new windows event log named _EPmiddleWare_.
{% endstep %}
{% endstepper %}

<figure><img src="../../../.gitbook/assets/Verifone screenshot 2.png" alt=""><figcaption></figcaption></figure>

To use the SDK, you only need to directly interface to the file named _EP.Enterprise.Vx820.dll_. The other files are dependencies. Make sure to extract all 4 of the files to the location of your choice.

<table data-header-hidden><thead><tr><th width="117"></th><th></th></tr></thead><tbody><tr><td><img src="../../../.gitbook/assets/Icon_File2 (1).png" alt=""></td><td>EP.Enterprise.Vx820Lib.dll</td></tr><tr><td><img src="../../../.gitbook/assets/Icon_File2 (1).png" alt=""></td><td>EP.Vx820.Common.dll</td></tr><tr><td><img src="../../../.gitbook/assets/Icon_File1.png" alt=""></td><td>EP.Enterprise.Vx820Lib.dll.config</td></tr><tr><td><img src="../../../.gitbook/assets/Icon_File2 (1).png" alt=""></td><td>DPayments.DPaymentsSDK.dll</td></tr></tbody></table>

[Contact us](../../../help/customer-support/) for further instructions on how to use the SDK.



***



## Custom Windows event log

After installing all the dependencies for either the SDK or the browser-based approach,, you will notice a new Windows event log has been registered named _EPmiddleWare_.&#x20;

This event log stores information about processed transactions as well as any errors encountered, and serves as a powerful troubleshooting component.

{% hint style="info" %}
With the Verifone Windows event log installed, a merchant can export the log and send it to Number if any unexpected behavior is encountered.
{% endhint %}

<figure><img src="../../../.gitbook/assets/event viewer verifone enhanced.png" alt=""><figcaption></figcaption></figure>



***



## Verifone power settings

Both the middleware service and the SDK will attempt to maintain a continuous connection to the Verifone device. If your hardware is suspended or enters sleep, this can cause issues. To avoid these, please make sure to modify your USB power settings.

#### Windows 10 and Windows 11

For Windows 10, you'll need to go to Control Panel > Power Options > Edit Plan Settings.

On Windows 11, open Control Panel > Hardware and Sound > Power Options > Edit Plan Settings.

Go to _Advanced power settings_ and change the _USB settings_ to disable _USB selective suspend_ for your active power plan.

{% hint style="danger" %}
When using the Verifone, **make sure that your machine is running the power plan with the modified settings**. All power plans have separate power settings.
{% endhint %}

<figure><img src="../../../.gitbook/assets/Verifone screenshot 6.png" alt=""><figcaption></figcaption></figure>

<figure><img src="../../../.gitbook/assets/Verifone screenshot 7.png" alt=""><figcaption></figcaption></figure>

{% hint style="warning" %}
If you don't see the USB power settings on your machine, you might need to expose them.

1. Run the Command Prompt as an administrator.
2. Type the command below you into the elevated command prompt, and press Enter:

{% code overflow="wrap" %}
```
REG ADD HKLM\SYSTEM\CurrentControlSet\Control\Power\PowerSettings\2a737441-1930-4402-8d77-b2bebba308a3\48e6b7a6-50f5-4782-a5d4-53bb8f07e226 /v Attributes /t REG_DWORD /d 2 /f
```
{% endcode %}

3. After running the command, reboot your computer, then reopen your advanced power settings following the steps listed above.
{% endhint %}



