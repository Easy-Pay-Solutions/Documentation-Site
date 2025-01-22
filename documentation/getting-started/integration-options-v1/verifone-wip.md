---
description: Getting started with Verifone for Number
---

# Verifone (WIP)

## Introduction

The Verifone card readers are small hand-held devices. They communicate with your computer on a USB port. A chip transaction is comprised of about a dozen transmissions between the host (your computer) and the device, and then finally to the Number cloud platform.

Using the Verifone card readers offers a highly secure method of collecting cardholder data.

Cardholder data is encrypted within the device itself, and remains encrypted as it travels across the Internet to our PCI Level One Compliant processing platform.&#x20;

{% hint style="info" %}
When a merchant supports a Verfione card reader, it helps eliminate chargebacks for transactions which were run through the device.
{% endhint %}

<figure><img src="../../../.gitbook/assets/Verifone.png" alt=""><figcaption></figcaption></figure>



### PCI SSC Software Security Framework (SSF) <a href="#pci-ssc-software-security-framework-ssf" id="pci-ssc-software-security-framework-ssf"></a>

Software Security Framework is a re-working of the existing PCI standard PA DSS. The PA DSS has been retired since June 30, 2021. Number's "Aspen 3.1" is the first application to achieve the PCI Councils SSF certification, and it provides an end-to-end encrypted solution.



***



## Software options <a href="#what-we-offer" id="what-we-offer"></a>

Currently, we offer four different options for collecting payments with the Verifone card readers, all of which require a Windows OS on the host computer.

{% stepper %}
{% step %}
**Standalone desktop application (upon request)**

This application allows you to collect payments, create card-on-file and payment plans, process a card-on-file, void or credit, settle transactions, and do reporting with an option to export to a PDF.
{% endstep %}

{% step %}
**Easy Pay Verifone SDK**

This DLL provides a means of collecting payments and creating card-on-file plans. Used in conjunction with our API, you can manage all aspects of your payment requirements, all within the confines of your own custom application.
{% endstep %}

{% step %}
**Browser-based interface**

We developed a Windows service which uses Cross-Origin Resource Sharing (CORS) to communicate with the browser. As an integrator, this allows you to write simple client-side scripts within your own web applications to initiate transactions with a local Verifone.&#x20;

{% embed url="https://easypay7.com/docs/jquery_verifone.zip" %}
An example website communicating with the Verifone using jQuery.
{% endembed %}

The Win service will return a simple XML response for each transaction directly to the HTML/PHP/ASP.NET page for consumption by the host application.
{% endstep %}

{% step %}
Virt**ual Terminal**

Our Number Virtual Terminal has a built-in support for Verifone. After installing the middleware service, you can ask the Number team for this feature to be activated.&#x20;
{% endstep %}
{% endstepper %}

#### **Requirements**

There are 2 categories of integrations which require two different sets of files

1. Browser-based - install our Win service which contains all your dependencies, including the drivers and console installer;
2. Desktop-based - install our SDK, then use separate installers for drivers and a custom event log.



### Easy Pay Verifone SDK <a href="#easy-pay-verifone-sdk" id="easy-pay-verifone-sdk"></a>

For you to directly interface with the Verifone using our SDK, you will need the Verifone drivers with the custom logging package, and the SDK reference files:

<table data-card-size="large" data-view="cards"><thead><tr><th align="center" valign="middle"></th><th data-hidden data-card-target data-type="content-ref"></th></tr></thead><tbody><tr><td align="center" valign="middle">Verifone drivers and the <br>custom logging package</td><td><a href="https://easypay1.com/deploy/SetupVerifoneDrivers/Setup_USB_log_win11.zip">https://easypay1.com/deploy/SetupVerifoneDrivers/Setup_USB_log_win11.zip</a></td></tr><tr><td align="center" valign="middle">Verifone SDK reference files</td><td><a href="https://easypay1.com/deploy/VerifoneSDK/EP.Enterprise.Vx820Lib2.zip">https://easypay1.com/deploy/VerifoneSDK/EP.Enterprise.Vx820Lib2.zip</a></td></tr></tbody></table>

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

To use the SDK, you only need to directly interface to the file named _EP.Enterprise.Vx820.dll_. The other 3 files in the ZIP file with the SDK are dependencies. Make sure to extract all 4 of the files to the location of your choice.

<table data-header-hidden><thead><tr><th width="117"></th><th></th></tr></thead><tbody><tr><td><img src="../../../.gitbook/assets/Icon_File2 (1).png" alt=""></td><td>EP.Enterprise.Vx820Lib.dll</td></tr><tr><td><img src="../../../.gitbook/assets/Icon_File2 (1).png" alt=""></td><td>EP.Vx820.Common.dll</td></tr><tr><td><img src="../../../.gitbook/assets/Icon_File1.png" alt=""></td><td>EP.Enterprise.Vx820Lib.dll.config</td></tr><tr><td><img src="../../../.gitbook/assets/Icon_File2 (1).png" alt=""></td><td>DPayments.DPaymentsSDK.dll</td></tr></tbody></table>



### Browser based Installation <a href="#browser-based-installation" id="browser-based-installation"></a>

Before you start, download the Windows service to your machine.

{% embed url="https://easypay1.com/deploy/MiddleWare/EPVerifoneSetup_E2E_1041.zip" %}

To install the Win service:

{% stepper %}
{% step %}
Connect your device to free USB port.
{% endstep %}

{% step %}
Allow device to initialize.
{% endstep %}

{% step %}
Extract the above archive to location of your choice.
{% endstep %}

{% step %}
Locate the EXE file and right click on the EXE to choose _Run as administrator_.
{% endstep %}

{% step %}
Wait for the application to finish, then reboot computer.
{% endstep %}
{% endstepper %}

The above install package does the following

1. Installs USB drivers for the Verifone.
2. Creates a custom event log with Windows named _EPmiddleware_.
3. Installs a certificate which encrypts data between the browser and the Windows service.
4. Install the Windows service which listens on port 8031.

With this, your website will be able to issue commands to the Windows service. You can see [our example website](https://easypay7.com/JqueryVerifone/) communicating with Verifone.

You can also download the entire site here:

{% file src="../../../.gitbook/assets/jquery_verifone.zip" %}

#### Virtual Terminal

Our Virtual Terminal has a built-in support for Verifone. All you need to do is install the service and contact Number for this feature to be activated.



***



## Custom Windows event ;og

Once the installation program has completed, you will notice a new Windows event log has been registered named _EPmiddleWare_. This log is relevant for both the SDK and browser-based middleware.

This event log stores information about processed transactions as well as any errors encountered, and serves as a powerful troubleshooting component.

{% hint style="info" %}
With the Verifone Windows event log installed, a merchant can export the log and send it to Number if any unexpected behavior is encountered.
{% endhint %}

<figure><img src="../../../.gitbook/assets/Verifone screenshot 3.png" alt=""><figcaption></figcaption></figure>



***



## Verifone power settings

Both the middleware service and the SDK will attempt to maintain a continuous connection to the Verifone device. If your hardware is suspended or enters sleep, this can cause issues. To avoid these, please make sure to modify your USB power settings.

#### Windows 10 and Windows 11

For Windows 10, you'll need to go to Control Panel > Power Options > Edit Plan Settings.

On Windows 11, open Control Panel > Hardware and Sound > Power Options > Edit Plan Settings.

Go to _Advanced power settings_ and change the _USB settings_ to disable _USB selective suspend_ for your active power plan.

{% hint style="danger" %}
When using the Verifone, **make sure to run the power plan with the modified settings**. Battery saver and custom plans have separate settings, they will not be affected.
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



***



## End-To-End Encryption <a href="#end-to-end-encryption" id="end-to-end-encryption"></a>

<figure><img src="../../../.gitbook/assets/End to end encyption.png" alt=""><figcaption></figcaption></figure>



***

## Number EMV Integration Options with End to end Encryption

### Number VxModule

<figure><img src="../../../.gitbook/assets/Number .Net Application.png" alt=""><figcaption></figcaption></figure>

### Number Browser Integration

<figure><img src="../../../.gitbook/assets/Number Browser Integration.png" alt=""><figcaption></figcaption></figure>

### Number Desktop Application / with Automatic Updates

<figure><img src="../../../.gitbook/assets/Number Desktop Application.png" alt=""><figcaption></figcaption></figure>
