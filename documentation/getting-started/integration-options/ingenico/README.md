---
hidden: true
---

# Ingenico

#### Getting Started

This guide will help you quickly get started with your Ingenico card reader using our API. You will learn how to connect and configure your device, establish secure communication, and begin processing transactions.

#### **Install the Certificate**

Once the device is powered on and connected to the network, it's certificate needs to be loaded into the browser. Complete instructions are available at Download and Install certificates.

#### **Authenticate and retrieve a session key**

After you authenticate with your AccountCode and Token, the backend returns a SessKey. This key is required to prove identity on subsequent REST API methods (passed as a SessKey header). For more information, view the [authentication](https://docs.number.tech/documentation/getting-started/basics/authentication) section of the site.

#### **View the demo site and code samples**

Code examples and endpoint references are provided to help you implement authorization, card payments, saved cards, device configuration and error handling.

The sample site is located at [https://easypay1.com/ingenicodemo](https://easypay1.com/ingenicodemo). The site can also be downloaded at [ingenicodemo.zip](https://easypay1.com/ingenicodemo/ingenicodemo.zip)

