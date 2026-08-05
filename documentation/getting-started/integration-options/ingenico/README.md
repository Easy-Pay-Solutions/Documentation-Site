---
hidden: true
icon: dialpad
---

# Ingenico

#### Getting Started

This guide will help you quickly get started with your Ingenico card reader using our API. You'll learn how to connect and configure your device, establish secure communication, and begin processing transactions. If you prefer not to build an API integration, you can use our Virtual Terminal to process EMV transactions with your Ingenico card reader.

#### **Install the Certificate**

Once the device is powered on and connected to the network, its certificate needs to be loaded into the browser. Complete instructions are available at [Download and Install](certificate.md) certificates.

#### **Authenticate and retrieve a session key**

After you authenticate with your AccountCode and Token, the backend returns a SessKey. This key is required to prove identity on subsequent REST API methods (passed as a SessKey header). For more information, view the [authentication](https://docs.number.tech/documentation/getting-started/basics/authentication) section of the site.

#### **View the demo site and code samples**

Code examples and endpoint references are provided to help you implement authorization, card payments, saved cards, device configuration and error handling.

The sample site is located at [https://easypay1.com/ingenicodemo](https://easypay1.com/ingenicodemo). The site can also be downloaded at [ingenicodemo.zip](https://easypay1.com/ingenicodemo/ingenicodemo.zip)

#### Virtual Terminal

You can use our Virtual Terminal with your Ingenico device, which includes built-in support for EMV transaction processing. This eliminates the need to build your own user interface or write any code. After connecting the device to your network and installing the required certificate, contact Number to have this feature activated.

You can read more about using the Virtual Terminal in the [Virtual Terminal](https://docs.number.tech/documentation/getting-started/integration-options/virtual-terminal) guide.

