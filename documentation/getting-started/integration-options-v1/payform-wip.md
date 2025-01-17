---
description: Getting started with PayForm for Number
---

# PayForm (WIP)



## Introduction

The PayForm is designed to be a highly flexible and secure payment form for your users.&#x20;

Collecting a payment or saving a card on file is a two-step process: a call is made to our REST API to initialize the payment parameters, and a payment link is generated.

You get to control all of the operational and design parameters of the PayForm such as:

* Form styling,
* Field visibility and read-only parameters,
* Initial data (cardholder names, $ amounts, etc.),
* User-defined data (PatientID, ReferenceID, etc.),
* Defined methods for receiving a real-time update after transactions are authorized.

You can then present the PayForm in one of two ways:&#x20;

* As an iFrame on your website,&#x20;
* As a direct link to the PayForm.

**To generate a PayForm, you can make a call to our REST API based on request body generated on the PayForm builder website.**



***



## PayForm builder

It might be difficult to prepare a PayForm request by yourself at first. To make it easy to get started, we've prepared a form which can do that for you.

{% embed url="https://easypay8.com/byopayform/" %}



### Transaction types

There are three operation types you can choose from:

* Collecting an instant card payment,
* Saving cardholder data to be charged later (card-on-file),
* Both saving the cardholder data (card-on-file) and an instant card payment.

This choice wil also determine some of the required fields and submission options for you.



### Visible and read-only fields

There is a number of fields you can have added to your form. For some of the fields, you can choose to provide a default value, and to mark them as read-only.

<table><thead><tr><th width="166">Field name</th><th width="403">Description</th><th>Read-only toggle</th></tr></thead><tbody><tr><td>First Name</td><td>Cardholder first name. If only <strong>First Name</strong> is visible, field will be changed to <strong>Full Name.</strong></td><td>yes</td></tr><tr><td>Last Name</td><td>Cardholder last name. If only <strong>Last Name</strong> is visible, field will be changed to <strong>Full Name.</strong></td><td>yes</td></tr><tr><td>Address</td><td>Cardholder street address.</td><td>yes</td></tr><tr><td>City</td><td>Cardholder city.</td><td>yes</td></tr><tr><td>State</td><td>Cardholder state.</td><td>yes</td></tr><tr><td>Zip Code</td><td>Cardholder zip code.</td><td>yes</td></tr><tr><td>Amount</td><td> A total $ amount to charge, when applicable to the chosen transaction type.</td><td>yes</td></tr><tr><td>REFID</td><td>A user-defined custom field</td><td>yes</td></tr><tr><td>RPGUID</td><td>A hidden user-defined custom field</td><td>yes</td></tr><tr><td>Expiration</td><td>Expiration date on the card, <strong>required</strong>.</td><td>-</td></tr><tr><td>CVV</td><td>Security code on the back of the card, <strong>required</strong>.</td><td>-</td></tr><tr><td>Agree to Pay confirmation</td><td></td><td>-</td></tr><tr><td>Agree to Save Card on File confirmation</td><td></td><td>-</td></tr><tr><td>Email</td><td>Cardholder email address.</td><td>yes</td></tr><tr><td>Auth to Email</td><td></td><td>-</td></tr><tr><td>Logos</td><td></td><td>-</td></tr></tbody></table>



### Submission options

Based on your requirements, you can choose from many submission options explained below.

<table><thead><tr><th width="194">Submission option</th><th>Description</th></tr></thead><tbody><tr><td>Redirect external</td><td>After submitting, the user will be redirected to a provided external URL. <br><br>An encrypted string containing the POST data is appended to the URL to be consumed by the merchant.</td></tr><tr><td>Redirect internal - receipt combo</td><td><p>After submitting, the user will be redirected to an internal page displaying a combination receipt for merchant and customer. <br><br>An encrypted string containing the POST data is appended to the URL to be consumed by the merchant. </p><p></p><p>This can also be used in conjunction with <strong>Silent Post</strong> for the purpose of transmitting data.</p></td></tr><tr><td>Redirect internal - receipt customer</td><td>After submitting, the user will be redirected to an internal page displaying a receipt for the customer. <br><br>An encrypted string containing the POST data is appended to the URL to be consumed by the merchant.<br><br>This can also be used in conjunction with <strong>Silent Post</strong> for the purpose of transmitting data.</td></tr><tr><td>Redirect internal - success message</td><td>After submitting, the user will be redirected to an internal page displaying a success message and a check mark image. <br><br>An encrypted string containing the POST data is appended to the URL to be consumed by the merchant.<br><br>Sometimes used with desktop apps which use embedded browsers.</td></tr><tr><td>Silent post</td><td>After submitting, an encrypted string containing the POST data is sent to the provided URL to be consumed by the merchant. The data is transmitted in the background. <strong>The user is not redirected.</strong></td></tr><tr><td>Post message</td><td>When the PayForm is inside of an iFrame, after submitting, an encrypted string containing the POST data is sent to the parent page to be consumed by the merchant. <strong>The user is not redirected.</strong></td></tr><tr><td>Require AVS full match</td><td>To submit the PayForm, a full AVS match must be submitted. <strong>This requires the Address and Zip Code to match exactly what is on record with the issuer for the card.</strong></td></tr><tr><td>Require AVS partial match</td><td>To submit the PayForm, a partial AVS match must be submitted. <strong>This requires that, at a minimum, there is a Zip Code match achieved.</strong></td></tr><tr><td>Require CVV match</td><td>To submit the PayForm, a full CVV match must be achieved. <strong>The transaction will be voided if the CVV does not fully match what is on file with the card issuer.</strong></td></tr><tr><td>Payment widget</td><td>This PayForm will collect a one-time payment. <strong>Automatically set when choosing a transaction type.</strong></td></tr><tr><td>Save Card on File widget</td><td>This PayForm will save the card on file for future use. <strong>Automatically set when choosing a transaction type.</strong></td></tr><tr><td>JSON post</td><td>Replace the encrypted POST data with a JSON object to be consumed.</td></tr><tr><td>Send only <code>TxID</code> / <code>ConsentID</code></td><td>Only include the <code>TransactionID</code> and <code>ConsentID</code> in the data to be consumed.</td></tr></tbody></table>



### Style and colors

We care about making sure that the PayForm can match the style of your branding. You'll notice that some options are mutually exclusive.&#x20;

Here is a list of all non-default customization options that can affect the look of the PayForm:

<table><thead><tr><th width="282">Customization element</th><th>Options</th></tr></thead><tbody><tr><td>Label position</td><td>Left of the textbox, above the textbox, within the textbox.</td></tr><tr><td>PayForm corners</td><td>Semiround, round, semiround subtle.</td></tr><tr><td>Font family</td><td>Serif Font, Roboto font.</td></tr><tr><td>Required field indicators</td><td>Show.</td></tr><tr><td>Hide buttons</td><td>Hide both buttons, hide cancel button.</td></tr><tr><td>Text box size</td><td>Tall text boxes, short text boxes.</td></tr><tr><td>Background color<br>Button background color<br>Button border color<br>Button text color<br>Label text color<br>Textbox text color<br>Textbox background color</td><td>Any RGB value (can be selected using the color picker).</td></tr></tbody></table>



### Pre-filled values

Depending on your needs, you might want to have some of the values pre-filled with defaults. This will allow you to provide a default for the **First Name**, **Last Name**, **Address**, **City**, **State**, **Zip**, **Amount**, **REFID**, **RPGUID**, and **Email**.

Additionally, in this part of the builder, you can set values for the hidden config fields used by the form: **Endpoint**, **Redirect URL**, **Post URL**, and **EIndex**.

| Hidden config field | Description                                                                                                                        |
| ------------------- | ---------------------------------------------------------------------------------------------------------------------------------- |
| Endpoint            | Points to specific web application on our server. Number will provide guidance.                                                    |
| Redirect URL        | A URL to redirect the user after the payment is processed, if applicable.                                                          |
| Post URL            | A URL to POST the real-time values after the payment is completed, if applicable.                                                  |
| EIndex              | Integrator key index for encryption assigned when integrator account is first created, received with the initial login credentials |





***



## PayForm API request

Once you have the request ready, you can call our REST API to generate the PayForm and the `PaymentURL` that you can use to access it. Here's the reference to [Initialize PayForm](../../../api-reference/rest-api-v2/payform-v2.md#payform-initialize) endpoint.





