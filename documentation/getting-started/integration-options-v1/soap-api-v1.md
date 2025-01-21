---
description: Getting started with SOAP API for Number
---

# SOAP API (v1)

Our SOAP API allows full integration of Number services with a high degree of customization. You can use our [SOAP API reference](../../../api-reference/soap-api-v2/) to learn about specific methods in the API.

Before you continue this section, we recommend reading sections about [authentication](../basics-v1/api-authentication-v3.md), [best practices](../basics-v1/api-best-practices-v2.md), and [input validation](../basics-v1/api-input-validation-v1.md).



***



## Generate the service for WCF applications

The easiest way to get started using Number's SOAP API is to generate the `CardProcessClient` service. Following the steps below, you'll learn how to generate that service for applications using the [Windows Communication Foundation (WCF)](https://learn.microsoft.com/dotnet/framework/wcf/whats-wcf) framework.

### Generate `CardProcessService` using the command line

{% stepper %}
{% step %}
#### Install .NET Framework SDK

Download and install the Windows SDK that corresponds with the version of the .NET Framework you're using. You can find the SDK installer on the Microsoft website.

Alternatively, you can install Visual Studio Community, Professional, or Enterprise, which include the SDK alongside with other .NET development tools.
{% endstep %}

{% step %}
#### Locate the [ServiceModel Metadata Utility Tool](https://learn.microsoft.com/dotnet/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe) is installed

SvcUtil.exe is used to generate service model code from metadata documents such as WSDL files. For .NET Framework 4.x, it is usually located in '_C:\Program Files (x86)\Microsoft SDKs\Windows\v10.0A\bin\NETFX 4.8 Tools\\_'.
{% endstep %}

{% step %}
#### Use the tool to generate the `CardProcessService` model

Open a Command Prompt window and navigate to the directory where SvcUtil.exe is located or add the directory to your system's PATH environment variable for easier access.

Then, you can execute the following command:

```
svcutil.exe https://easypay5.com/APIcardProcR119/CardProcAPI.svc?wsdl
```

{% hint style="info" %}
By default, svcutil.exe will generate C# code. You can specify a language option by adding `/language:VB` or `/language:CPP` at the end of the command if you wish to generate a service class for Visual Basic or C++.
{% endhint %}

{% hint style="warning" %}
Make sure to run the command as an administrator. If you receive network errors, you can try downloading the [single WSDL](https://easypay5.com/APIcardProcR119/CardProcAPI.svc?singleWsdl) with the full service description and provide the file path as an argument to the command.&#x20;

Example: `svcutil.exe "C:\Users\{Name}\Downloads\CardProcAPI.xml"`
{% endhint %}

This will generate a configuration file with the name of `output.config` and a C# code file named `CardProcAPI.cs` that contains the client class. Both of the files should appear inside of the folder with the tool.&#x20;

Add the two files to your application and use the generated client class to call the service.
{% endstep %}
{% endstepper %}

Here's a brief example of creating and disposing of the service client:

{% tabs %}
{% tab title="C# (WCF)" %}
{% code lineNumbers="true" %}
```csharp
class Test
{
    static void Main()
    {
        CardProcessClient client = new CardProcessClient();

        // Use the 'client' variable to call operations on the service.

        // Always close the client.
        client.Close();
    }
}
```
{% endcode %}
{% endtab %}

{% tab title="Visual Basic (WCF)" %}
{% code lineNumbers="true" %}
```vbnet
Class Test
    Shared Sub Main()
        Dim client As CardProcessClient = New CardProcessClient()
        ' Use the 'client' variable to call operations on the service.

        ' Always close the client.
        client.Close()
    End Sub
End Class
```
{% endcode %}
{% endtab %}
{% endtabs %}



***

## Examples

### Authenticate

An example of using the [<mark style="color:green;">`Authenticate`</mark>](../../../api-reference/soap-api-v2/authentication-v1.md#authenticate) method.

{% tabs %}
{% tab title="C# (WCF)" %}
{% code overflow="wrap" lineNumbers="true" fullWidth="false" %}
```csharp
private void Authenticate(string acctCode, string token)
{
  CardProc.api_AuthResponse authResp;

  // Using statement is recommended to release resources
  using (CardProc.CardProcessClient cardClient =
    new CardProc.CardProcessClient())
  {
    // Try-catch block will catch communication errors 
    try
    {
      // WARNING: 6 UNSUCCESSFUL ATEMPTS CAUSE IP LOCK OUT
      authResp = cardClient.Authenticate(acctCode, token);
    }
    catch (Exception ex)
    {
      MessageBox.Show("Problem communicating with service:" + ex.Message);
      // <Insert your Logging function here>
      return;
    }

    // Check for null response for any critical error
    if (authResp == null)
    {
      MessageBox.Show("Critical error");
      // <Insert your Logging function here>
      return;
    }

    // Check for unexpected error on server
    if (!authResp.FunctionOk)
    {
      MessageBox.Show(authResp.ErrMsg + "ErrorCode:" + authResp.ErrCode);
      // <Insert your Logging function here>
      return;
    }

    // Check for expected problems such as invalid
    // or expired credentials and inactive account.
    if (!authResp.AuthSuccess)
    {
      MessageBox.Show(authResp.RespMsg);
      // <Insert your Logging function here>
      return;
    }

    /* Arriving here means that the Authentication was successful. 
     * You will retrieve a SessionKey and 
     * a list of Merchant Records associated with this account. 
     * The session key should be used for all subsequent API calls */

    string sessKey = authResp.SessKey;
    CardProc.api_MerchantInfo[] merchList = authResp.MerchantList;

    // <Store the Session Key and the Merchant List>
  }
}

```
{% endcode %}
{% endtab %}
{% endtabs %}



### Process Annual Consent

An example of using [<mark style="color:green;">`ConsentAnnual_ProcPayment_Alt`</mark>](../../../api-reference/soap-api-v2/consent-annual-v1/process-annual-consent-v1.md#process-annual-consent-alternative) method

{% tabs %}
{% tab title="C# (WCF)" %}
{% code overflow="wrap" lineNumbers="true" %}
```csharp
private void ProcessConsentAnnual(string sessKey, 
  int consentId, decimal amount, int merchantId)
{
  /* Pass in the Session Key obtained from Authentication call, 
   * the ConsentID ( saved Card ), the $ Amount that needs to be processed, 
   * and (optional) MerchantID to process */

  CardProc.api_CCSaleResponse response;

  // Using statement is recommended to release resources
  using (CardProc.CardProcessClient cardClient = 
    new CardProc.CardProcessClient())
  {
    // Try-catch block will catch communication errors
    try
    {
      response = cardClient.ConsentAnnual_ProcPayment_Alt(
        sessKey, consentId, amount, merchantId);
    }
    catch (Exception ex)
    {
      MessageBox.Show("Problem communicating with service: " + ex.Message);
      // <Insert your Logging function here>
      return;
    }

    // Check for null response for any critical error
    if (response == null)
    {
      MessageBox.Show("Critical error");
      // <Insert your Logging function here>
      return;
    }

    // Check for unexpected errors on server
    if (!response.FunctionOk)
    {
      MessageBox.Show("Error : " + response.ErrMsg 
        + " ErrorCode: " + response.ErrCode);
      // <Insert your Logging function here>
      return;
    }

    if (!response.TxApproved)
    {
      MessageBox.Show("TRANSACTION DECLINED: " 
        + response.RespMsg + " Decline Code: " + response.TxnCode);
      // <Insert your Logging function here>
      return;
    }
    else
    {
      MessageBox.Show("TRANSACTION SUCCESS: " 
        + response.RespMsg + " TxID: " + response.TxID);
      // <Insert your Logging function here>
      string approvalCode = response.TxnCode;
      // <Do something with the response if needed>
      return;
    }
  }
}

```
{% endcode %}
{% endtab %}
{% endtabs %}



### Void Transaction

An example of using [<mark style="color:green;">`Transaction_Void`</mark>](../../../api-reference/soap-api-v2/transaction-v1.md#void-transaction) method.

{% tabs %}
{% tab title="C# (WCF)" %}
{% code overflow="wrap" lineNumbers="true" %}
```csharp
private void Void(string sessKey, int txID)
{
  /* Pass in the Session Key obtained from Authentication call
   * and TransactionID of the transaction to be voided. */

  CardProc.api_TransactionVoidResponse response;

  // Using statement is recommended to release resources
  using (CardProc.CardProcessClient cardClient = 
    new CardProc.CardProcessClient())
  {
    // Try-catch block will catch communication errors
    try
    {
      response = cardClient.Transaction_Void(sessKey, txID);
    }
    catch (Exception ex)
    {
      MessageBox.Show("Problem communicating with service: " + ex.Message);
      // <Insert your Logging function here>
      return;
    }

    // Check for null response for any critical error
    if (response == null)
    {
      MessageBox.Show("Critical error");
      // <Insert your Logging function here>
      return;
    }

    // Check for unexpected errors on server
    if (!response.FunctionOk)
    {
      MessageBox.Show("Error: " + response.ErrMsg 
        + " ErrorCode: " + response.ErrCode);
      // <Insert your Logging function here>
      return;
    }

    if (!response.TxApproved)
    {
      MessageBox.Show(response.RespMsg 
        + " Decline Code: " + response.TxnCode);
      // <Insert your Logging function here>
      return;
    }
    else
    {
      MessageBox.Show(response.RespMsg 
        + " TxID: " + response.TxID.ToString());
      // <Insert your Logging function here>
      return;
    }
  }
}

```
{% endcode %}
{% endtab %}
{% endtabs %}



### Credit Transaction

An example of using [<mark style="color:green;">`Transaction_ApplyCredit`</mark>](../../../api-reference/soap-api-v2/transaction-v1.md#apply-transaction-credit) method.

{% tabs %}
{% tab title="C# (WCF)" %}
{% code overflow="wrap" lineNumbers="true" %}
```csharp
private void Credit(string sessKey, int txID, decimal creditAmount)
{
  /* Pass in the Session Key obtained from Authentication call 
   * and TransactionID of the Transaction to be credited, 
   * and the Amount of the credit */

  CardProc.api_TransactionCreditResponse response;

  // Using statement is recommended to release resources
  using (CardProc.CardProcessClient cardClient =
    new CardProc.CardProcessClient())
  {
    // Try-catch block will catch communication errors
    try
    {
      response = cardClient.Transaction_ApplyCredit(
        sessKey, txID, creditAmount);
    }
    catch (Exception ex)
    {
      MessageBox.Show("Problem communicating with service:" + ex.Message);
      // <Insert your Logging function here>
      return;
    }

    // Check for null response for any critical error
    if (response == null)
    {
      MessageBox.Show("Critical error");
      // <Insert your Logging function here>
      return;
    }

    // Check for unexpected errors on server
    if (!response.FunctionOk)
    {
      MessageBox.Show("Error: " + response.ErrMsg
        + " ErrorCode: " + response.ErrCode);
      // <Insert your Logging function here>
      return;
    }

    if (!response.TxApproved)
    {
      MessageBox.Show(response.RespMsg);
      // <Insert your Logging function here>
      return;
    }
    else
    {
      MessageBox.Show(response.RespMsg + " TX ID: " 
        + response.TxID.ToString());
      // <Insert your Logging function here>
      return;
    }
  }
}
```
{% endcode %}
{% endtab %}
{% endtabs %}



### Query Transaction

An example of using [<mark style="color:green;">`Transaction_Query`</mark>](../../../api-reference/soap-api-v2/transaction-v1.md#query-transactions) method.

{% tabs %}
{% tab title="C# (WCF)" %}
{% code overflow="wrap" lineNumbers="true" %}
```javascript
private void TransactionQuery(string sessKey, string query)
{
  /* Pass in the Session Key obtained from Authentication call 
   * and Query used for filtering the list of transactions */

  /* Sample Query: (A=1)&&(C>='6/1/2021')&&(C<'7/1/2021')&&(B=2)
   * this will return all records from merchant record 1 
   * which were created in JUNE and are SETTLED. */

  CardProc.api_TransactionQryResponse response;

  // Using statement is recommended to release resources
  using (CardProc.CardProcessClient cardClient =
    new CardProc.CardProcessClient())
  {
    // Try-catch block will catch communication errors
    try
    {
      response = cardClient.Transaction_Query(sessKey, query);
    }
    catch (Exception ex)
    {
      MessageBox.Show("Problem communicating with service: " + ex.Message);
      // <Insert your Logging function here>
      return;
    }

    // Check for null response for any critical error
    if (response == null)
    {
      MessageBox.Show("Critical error");
      // <Insert your Logging function here>
      return;
    }

    // Check for unexpected errors on servers
    if (!response.FunctionOk)
    {
      MessageBox.Show("Error: " + response.RespMsg
        + " ErrorCode: " + response.ErrCode);
      // <Insert your Logging function here>
      return;
    }

    CardProc.api_Transaction[] transactions = response.Transactions;

    // <Display your transactions here>
  }
}
```
{% endcode %}
{% endtab %}
{% endtabs %}



### Consent General Query

An example of using [<mark style="color:green;">`ConsentGeneral_Query`</mark>](../../../api-reference/soap-api-v2/consent-general-v1.md#query-consent) method

{% tabs %}
{% tab title="C# (WCF)" %}
{% code overflow="wrap" lineNumbers="true" %}
```csharp
private void ConsentGeneralQuery(string sessKey, string query)
{
  /* Pass in the Session Key obtained from Authentication call 
   * and Query used for filtering the list of transactions */

  /* Sample Query: (D='SMITH')&&(E>'10/20/2020')
   * all Consent records from cardholder SMITH created after 10/20/2020 */

  CardProc.api_ConsentGeneralQryResponse response;

  // Using statement is recommended to release resources
  using (CardProc.CardProcessClient cardClient =
    new CardProc.CardProcessClient())
  {
    // Try-catch block will catch communication errors
    try
    {
      response = cardClient.ConsentGeneral_Query(sessKey, query);
    }
    catch (Exception ex)
    {
      MessageBox.Show("Problem communicating with service: " + ex.Message);
      // <Insert your Logging function here>
      return;

    }
    // Check for null response for any critical error
    if (response == null)
    {
      MessageBox.Show("Critical error");
      // <Insert your Logging function here>
      return;
    }

    // Check for unexpected errors on servers
    if (!response.FunctionOk)
    {
      MessageBox.Show("Error: " + response.RespMsg
        + "ErrorCode: " + response.ErrCode);
      // <Insert your Logging function here>
      return;
    }

    CardProc.api_ConsentGeneral[] MyConsents = response.Consents;

    // <Display your consent (card-on-file) records here>
  }
}
```
{% endcode %}
{% endtab %}
{% endtabs %}



### Generate Receipt

An example of using [<mark style="color:green;">`ReceiptGenerate`</mark>](../../../api-reference/soap-api-v2/receipt-v1.md#generate-receipt) method.

{% tabs %}
{% tab title="C# (WCF)" %}
{% code overflow="wrap" lineNumbers="true" %}
```csharp
private void ShowReceipt(string sessKey, 
  int refID, int receiptType, int recipient)
{
  /* ReceiptType 1 TRANSACTION RECEIPT
   * ReceiptType 2 VOID RECEIPT
   * ReceiptType 3 REFUND RECEIPT
   * ReceiptType 4 ANNUAL RECEIPT
   * ReceiptType 5 RECURRING RECEIPT
   * ReceiptType 6 SUBSCRIPTION RECEIPT
   
   * Recipient 1 MERCHANT COPY
   * Recipient 2 CUSTOMER COPY
   * Recipient 3 DUAL COPY */

  CardProc.api_ReceiptQryResponse response;

  // Using statement is recommended to release resources
  using (CardProc.CardProcessClient cardClient =
    new CardProc.CardProcessClient())
  {
    // Try-catch block will catch communication errors
    try
    {
      response = cardClient.ReceiptGenerate(
        sessKey, refID, receiptType, recipient);
    }
    catch (Exception ex)
    {
      MessageBox.Show("Problem communicating with service: " + ex.Message);
      // <Insert your Logging function here>
      return;
    }

    // Check for null response for any critical error
    if (response == null)
    {
      MessageBox.Show("Critical Error");
      // <Insert your Logging function here>
      return;
    }

    // Check for unexpected errors on servers
    if (!response.FunctionOk)
    {
      MessageBox.Show("Error: " + response.RespMsg
        + "ErrorCode: " + response.ErrCode);
      // <Insert your Logging function here>
      return;
    }

    /* Receipt generation successful. 
     * You may now add the HTML to your page.
     * <Logic to display HTML, e.g. 
     *  webBrowser1.DocumentText = response.ReceiptHtml;> */
  }
}
```
{% endcode %}
{% endtab %}
{% endtabs %}



