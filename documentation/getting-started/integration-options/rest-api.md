---
description: Getting started with the REST API for Number
---

# REST API

Our REST API allows full integration of Number services with a high degree of customization. You can use our [REST API reference](../../../api-reference/rest-api/) to learn about specific methods in the API.

Before you continue this section, we recommend reading sections about [authentication](../basics/authentication.md), [best practices](../basics/api-best-practices.md), and [input validation](../basics/api-input-validation.md).

## Examples

### Authenticate

An example of using the [<mark style="color:green;">`Authenticate`</mark>](../../../api-reference/rest-api/authentication.md#apicardprocrest-v1.0.0-authenticate) method.

{% tabs %}
{% tab title="C# Synchronous" %}
{% code lineNumbers="true" %}
```csharp
private void Authenticate() {

	/// create request with account code and Token 
	string jsonContent = "{\"AcctCode\":\"EP9142446\",\"Token\":\"F31D16BA862F4EC6AE95CB90450C826A\"}";

	byte[] data = Encoding.UTF8.GetBytes(jsonContent);

	// Specify Number Endpoint 
	string MyUrl = "https://easypay5.com/APIcardProcREST/v1.0.0/Authenticate";

	// create a webrequest 
	WebRequest request = WebRequest.Create(MyUrl);
	request.Method = "POST";
	request.ContentType = "application/json";
	request.ContentLength = data.Length;
	string responseContent = null;


	///  Important to handle any exceptions 
	try
	{
		// execute request 
		using (Stream stream = request.GetRequestStream())
		{
			stream.Write(data, 0, data.Length);
		}
		using (WebResponse response = request.GetResponse())
		{
			using (Stream stream = response.GetResponseStream())
			{
				using (StreamReader sr = new StreamReader(stream))
				{
					responseContent = sr.ReadToEnd();
				}
			}
		}
	}
	catch (Exception ee)
	{
		///  consume any communication exceptions and abort
		MessageBox.Show("Communication Exception : " + ee.Message);
		/// important to insert your Logging function here
		return;

	}

	/// parse Json in any number of ways  , we use Newtonsoft 
	var AuthResp = Newtonsoft.Json.JsonConvert.DeserializeObject<dynamic>(responseContent);

	var MyResp = AuthResp.AuthenticateResult;

	///  here are the important values to consume
	bool FunctionOk = (bool)MyResp.FunctionOk;
	bool AuthSuccess = (bool)MyResp.AuthSuccess;
	int ErrCode = (int)MyResp.ErrCode;
	string ErrMsg = (string)MyResp.ErrMsg;
	string RespMsg = (string)MyResp.RespMsg;

	//Check for unexpected Errors on cloud servers. If errors found log Error info and abort;
	if (!FunctionOk)
	{
		MessageBox.Show("Aspen Error : " + ErrMsg + " : ErrorCode: " + ErrCode);
		/// important to insert your Logging function here
		return;
	}

	//Check for failures such as Invalid or Expired Credentials or Inactive Account.
	if (!AuthSuccess)
	{
		MessageBox.Show("Failed Authentication : " + RespMsg);
		/// important to insert your Logging function here
		return;
	}

	/// Arriving here means that the Authentication was successful. You will retrieve a SessionKey and 
	/// a list of Merchant Records associated with this account. The session key will be used for all
	/// subsequent API calls within the next 25 hours 
	string SessKey = (string)MyResp.SessKey;
	var MerchantList = MyResp.MerchantList;

}
```
{% endcode %}
{% endtab %}

{% tab title="C# Asynchronous" %}
{% code lineNumbers="true" %}
```csharp
public static async Task<string> Authenticate()
{

	string responseData = string.Empty;

	HttpClient httpClient = new HttpClient();
	/// Number Endpoint
	string apiUrl = "https://easypay5.com/APIcardProcREST/v1.0.0/Authenticate";

	// Here is your account code and Token used to authenticate 
	string jsonContent = "{\"AcctCode\":\"EP9142446\",\"Token\":\"F31D16BA862F4EC6AE95CB90450C826A\"}";

	HttpResponseMessage response = new HttpResponseMessage();
	HttpContent content = new StringContent(jsonContent, Encoding.UTF8, "application/json");


	///  important exception handling will provide info for communication issues  
	try
	{
		response = await httpClient.PostAsync(apiUrl, content);
	}
	catch (Exception ee) {
		return "Exception : " + ee.Message;
	}

	if (response.IsSuccessStatusCode)
	{
		// Handle successful POST response
		responseData = await response.Content.ReadAsStringAsync();
	}
	else
	{
		return "http error code " + response.StatusCode;
	}

	//  now you can parse the Json Response in a number of ways ( we will use newtonsoft )
	var AuthResp = Newtonsoft.Json.JsonConvert.DeserializeObject<dynamic>(responseData);
	var MyResp = AuthResp.AuthenticateResult;

	///  here are the important values 
	bool FunctionOk = (bool)MyResp.FunctionOk;
	bool AuthSuccess = (bool)MyResp.AuthSuccess;
	int ErrCode = (int)MyResp.ErrCode;
	string ErrMsg = (string)MyResp.ErrMsg;
	string RespMsg = (string)MyResp.RespMsg;

	//Check for Aspen Errors on cloud servers. If errors found log Error info and abort;
	if (!FunctionOk)
	{
		return "Aspen Error : " + ErrMsg + " : ErrorCode:" + ErrCode;
	}

	//Check for failures such as Invalid or Expired Credentials or Inactive Account.
	if (!AuthSuccess)
	{
		return " Invalid Authentication : " + RespMsg;
	}

	/// Arriving here means that the Authentication was successful. You will retrieve a SessionKey and 
	/// a list of Merchant Records associated with this account. The session key will be used for all
	/// subsequent API calls
	string SessKey = (string)MyResp.SessKey;
	var MerchantList = MyResp.MerchantList;

	return "Success : " + SessKey;
}
```
{% endcode %}
{% endtab %}
{% endtabs %}



### Process Annual Consent <a href="#process-annual-consent" id="process-annual-consent"></a>

An example of using [<mark style="color:green;">`ConsentAnnual_ProcPayment`</mark>](../../../api-reference/rest-api/consent-annual/#apicardprocrest-v1.0.0-consentannual-procpayment) method.

{% tabs %}
{% tab title="C#" %}
{% code overflow="wrap" lineNumbers="true" %}
```csharp
public static async Task ProcessConsent(
  string sessKey, int consentId, decimal processAmount)
{
  using HttpClient httpClient = new HttpClient();
  string apiUrl = "https://easypay5.com/APIcardProcREST/v1.0.0/ConsentAnnual/ProcPayment";

  string jsonContent = $$"""
    {"ConsentID":{{consentId}},"ProcessAmount":{{processAmount}}}
  """;

  HttpContent content = new StringContent(
    jsonContent, System.Text.Encoding.UTF8, "application/json");
  httpClient.DefaultRequestHeaders.Add("SessKey", sessKey);
  HttpResponseMessage response = await httpClient
    .PostAsync(apiUrl, content);

  if (!response.IsSuccessStatusCode)
  {
    MessageBox.Show("Error code: " + response.StatusCode);
    // <Insert your Logging function here>
    return;
  }

  var saleResponse = Newtonsoft.Json.JsonConvert
    .DeserializeObject<dynamic>(
      await response.Content.ReadAsStringAsync());
  var procPaymentResult = saleResponse.ConsentAnnual_ProcPaymentResult;

  // Here are some of the important values 
  bool functionOk = (bool)procPaymentResult.FunctionOk;
  bool txApproved = (bool)procPaymentResult.TxApproved;
  int errCode = (int)procPaymentResult.ErrCode;
  string errMsg = (string)procPaymentResult.ErrMsg;
  string respMsg = (string)procPaymentResult.RespMsg;

  int txId = (int)procPaymentResult.TxID;
  int txnCode = (int)procPaymentResult.TxnCode;

  // Check for unexpected error on server
  if (!functionOk)
  {
    MessageBox.Show(errMsg + " ErrorCode: " + errCode);
    // <Insert your Logging function here>
    return;
  }

  // Check for declined transaction
  if (!txApproved)
  {
    MessageBox.Show(respMsg + " Decline Code: " + txnCode);
    // <Insert your Logging function here>
    return;
  }
  else
  {
    MessageBox.Show(respMsg + " Approval Code: " + txnCode);
    // <Insert your Logging function here>
    // <Do something with the response if needed>
    return;
  }
}
```
{% endcode %}
{% endtab %}

{% tab title="JavaScript (Node.js)" %}
{% code overflow="wrap" lineNumbers="true" %}
```javascript
'use strict';

const http = require('http');
const https = require('https');

const port = process.env.PORT || 1337;

http.createServer((req, res) => {
    let body = '';

	const sessKey = '89C8356BB8A84FE9B5303231333441303331343335'
    const data = JSON.stringify({
        ConsentID: 1,
        ProcessAmount: 5.00
    });

    const options = {
        host: 'easypay5.com',
        port: 443,
        path: '/APIcardProcREST/v1.0.0/ConsentAnnual/ProcPayment',
        method: 'POST',
        timeout: 2000,
        headers: {
            'Content-Type': 'application/json',
            'Content-Length': Buffer.byteLength(data),
            'Accept': 'application/json',
            'SessKey': sessKey
        }
    };

    const postReq = https.request(options, (postRes) => {
        postRes.setEncoding('utf8');

        postRes.on('data', (chunk) => {
            body += chunk;
        });

        postRes.on('end', () => {
            try {
                if (body === 'Bad Request') {
                    console.error('Bad request');
                    res.writeHead(400, { 'Content-Type': 'text/plain' });
                    res.end('Bad Request');
                    return;
                }

                const obj = JSON.parse(body);

                if (!obj) {
                    console.error('Communication Error: Null Object');
                    res.writeHead(500, { 'Content-Type': 'text/plain' });
                    res.end('Communication Error: Null Object');
                    return;
                }

                const { ConsentAnnual_ProcPaymentResult } = obj;

                if (!ConsentAnnual_ProcPaymentResult.FunctionOk) {
                    console.error(`${ConsentAnnual_ProcPaymentResult.ErrMsg} : ${ConsentAnnual_ProcPaymentResult.ErrCode}`);
                    res.writeHead(500, { 'Content-Type': 'text/plain' });
                    res.end(`${ConsentAnnual_ProcPaymentResult.ErrMsg} : ${ConsentAnnual_ProcPaymentResult.ErrCode}`);
                    return;
                }

                if (!ConsentAnnual_ProcPaymentResult.TxApproved) {
                    console.error(ConsentAnnual_ProcPaymentResult.RespMsg);
                    console.error(`Decline code: ${ConsentAnnual_ProcPaymentResult.TxnCode}`);
                    res.writeHead(402, { 'Content-Type': 'text/plain' });
                    res.end(`Declined: ${ConsentAnnual_ProcPaymentResult.RespMsg}`);
                    return;
                }

                console.log(`Successful Transaction: ${ConsentAnnual_ProcPaymentResult.RespMsg}`);
                console.log(`Approval code: ${ConsentAnnual_ProcPaymentResult.TxnCode}`);
                res.writeHead(200, { 'Content-Type': 'text/plain' });
                res.end(`Success: ${ConsentAnnual_ProcPaymentResult.RespMsg}`);
            } catch (error) {
                console.error('Error parsing response:', error);
                res.writeHead(500, { 'Content-Type': 'text/plain' });
                res.end('Internal Server Error');
            }
        });
    });

    postReq.on('error', (error) => {
        console.error('Request error:', error);
        res.writeHead(500, { 'Content-Type': 'text/plain' });
        res.end('Request Error');
    });

    postReq.on('timeout', () => {
        console.error('Request timed out');
        res.writeHead(504, { 'Content-Type': 'text/plain' });
        res.end('Request Timeout');
    });

    postReq.write(data);
    postReq.end();
}).listen(port, () => {
    console.log(`Server listening on port ${port}`);
});
```
{% endcode %}


{% endtab %}
{% endtabs %}



### Void Transaction <a href="#void-transaction" id="void-transaction"></a>

An example of using [<mark style="color:green;">`CardSale_Void`</mark>](../../../api-reference/rest-api/card-operations/#apicardprocrest-v1.0.0-cardsale-void) method.

{% tabs %}
{% tab title="C#" %}
{% code overflow="wrap" lineNumbers="true" %}
```csharp
public static async Task TransactionVoid(string sessKey, int txID)
{
  using HttpClient httpClient = new HttpClient();
  string apiUrl = "https://easypay5.com/APIcardProcREST/v1.0.0/ConsentAnnual/ProcPayment";

  string jsonContent = $$"""
    {"TxID":{{txID}}}
  """;

  HttpContent content = new StringContent(
    jsonContent, System.Text.Encoding.UTF8, "application/json");
  httpClient.DefaultRequestHeaders.Add("SessKey", sessKey);
  HttpResponseMessage response = await httpClient
    .PostAsync(apiUrl, content);

  if (!response.IsSuccessStatusCode)
  {
    MessageBox.Show("Error code: " + response.StatusCode);
    // <Insert your Logging function here>
    return;
  }

  var voidResponse = Newtonsoft.Json.JsonConvert
    .DeserializeObject<dynamic>(
      await response.Content.ReadAsStringAsync());
  var voidResult = voidResponse.Transaction_VoidResult;

  // Here are some of the important values 
  bool functionOk = (bool)voidResult.FunctionOk;
  int errCode = (int)voidResult.ErrCode;
  string errMsg = (string)voidResult.ErrMsg;
  string respMsg = (string)voidResult.RespMsg;

  bool txApproved = (bool)voidResult.TxApproved;
  int resultTxId = (int)voidResult.TxID;

  // Check for unexpected error on server
  if (!functionOk)
  {
    MessageBox.Show(errMsg + " ErrorCode: " + errCode);
    // <Insert your Logging function here>
    return;
  }

  // Check for declined transaction
  if (!txApproved)
  {
    MessageBox.Show(respMsg + " Decline Code: " + txnCode);
    // <Insert your Logging function here>
    return;
  }
  else
  {
    MessageBox.Show(respMsg + " Approval Code: " + txnCode);
    // <Insert your Logging function here>
    // <Do something with the response if needed>
    return;
  }
}
```
{% endcode %}
{% endtab %}
{% endtabs %}



### Credit Transaction <a href="#credit-transaction" id="credit-transaction"></a>

An example of using [<mark style="color:green;">`CardSale_ApplyCredit`</mark>](../../../api-reference/rest-api/card-operations/#apicardprocrest-v1.0.0-cardsale-applycredit) method.



{% tabs %}
{% tab title="C#" %}
{% code overflow="wrap" lineNumbers="true" %}
```csharp
public static async Task TransactionCredit(
  string sessKey, int txID, decimal creditAmount)
{
  using HttpClient httpClient = new HttpClient();
  string apiUrl = "https://easypay5.com/APIcardProcREST/v1.0.0/CardSale/ApplyCredit";

  string jsonContent = $$"""
    {"TxID":{{txID}},"CreditAmount":{{creditAmount}}}
  """;

  HttpContent content = new StringContent(
    jsonContent, System.Text.Encoding.UTF8, "application/json");
  httpClient.DefaultRequestHeaders.Add("SessKey", sessKey);
  HttpResponseMessage response = await httpClient
    .PostAsync(apiUrl, content);

  if (!response.IsSuccessStatusCode)
  {
    MessageBox.Show("Error code: " + response.StatusCode);
    // <Insert your Logging function here>
    return;
  }

  var creditResponse = Newtonsoft.Json.JsonConvert
    .DeserializeObject<dynamic>(
      await response.Content.ReadAsStringAsync());
  var creditResult = creditResponse.Transaction_ApplyCreditResult;

  // Here are some of the important values 
  bool functionOk = (bool)creditResult.FunctionOk;
  int errCode = (int)creditResult.ErrCode;
  string errMsg = (string)creditResult.ErrMsg;
  string respMsg = (string)creditResult.RespMsg;

  bool txApproved = (bool)creditResult.TxApproved;
  int resultTxId = (int)creditResult.TxID;

  // Check for unexpected error on server
  if (!functionOk)
  {
    MessageBox.Show(errMsg + " ErrorCode: " + errCode);
    // <Insert your Logging function here>
    return;
  }

  // Check for declined transaction
  if (!txApproved)
  {
    MessageBox.Show(respMsg + " Decline Code: " + txnCode);
    // <Insert your Logging function here>
    return;
  }
  else
  {
    MessageBox.Show(respMsg + " Approval Code: " + txnCode);
    // <Insert your Logging function here>
    // <Do something with the response if needed>
    return;
  }
}
```
{% endcode %}
{% endtab %}
{% endtabs %}



### Query Transaction <a href="#query-transaction" id="query-transaction"></a>

An example of using [<mark style="color:green;">`Query_Transaction`</mark>](../../../api-reference/rest-api/query/#apicardprocrest-v1.0.0-query-transaction) method.

{% tabs %}
{% tab title="C#" %}
{% code overflow="wrap" lineNumbers="true" %}
```csharp
public static async Task TransactionQuery(string sessKey, string query)
{
  using HttpClient httpClient = new HttpClient();
  string apiUrl = "https://easypay5.com/APIcardProcREST/v1.0.0/Query/Transaction";

  string jsonContent = $$"""
    {"Query":"{{query}}"}
  """;

  HttpContent content = new StringContent(
    jsonContent, System.Text.Encoding.UTF8, "application/json");
  httpClient.DefaultRequestHeaders.Add("SessKey", sessKey);
  HttpResponseMessage response = await httpClient
    .PostAsync(apiUrl, content);

  if (!response.IsSuccessStatusCode)
  {
    MessageBox.Show("Error code: " + response.StatusCode);
    // <Insert your Logging function here>
    return;
  }

  var queryResponse = Newtonsoft.Json.JsonConvert
    .DeserializeObject<dynamic>(
      await response.Content.ReadAsStringAsync());
  var queryResult = queryResponse.Transaction_QueryResult;

  // Here are some of the important values 
  bool functionOk = (bool)queryResult.FunctionOk;
  int errCode = (int)queryResult.ErrCode;
  string errMsg = (string)queryResult.ErrMsg;
  string respMsg = (string)queryResult.RespMsg;

  // Check for unexpected error on server
  if (!functionOk)
  {
    MessageBox.Show(errMsg + " ErrorCode: " + errCode);
    // <Insert your Logging function here>
    return;
  }

  var transactions = queryResult.Transactions;
  
  // <Display your transactions here>
}
```
{% endcode %}
{% endtab %}
{% endtabs %}



### Consent General Query <a href="#consent-general-query" id="consent-general-query"></a>

An example of using [<mark style="color:green;">`Query_ConsentGeneral`</mark>](../../../api-reference/rest-api/query/#apicardprocrest-v1.0.0-query-consentgeneral) method.

{% tabs %}
{% tab title="C#" %}
{% code overflow="wrap" lineNumbers="true" %}
```csharp
public static async Task ConsentGeneralQuery(string sessKey, string query)
{
  using HttpClient httpClient = new HttpClient();
  string apiUrl = "https://easypay5.com/APIcardProcREST/v1.0.0/Query/ConsentGeneral";

  string jsonContent = $$"""
    {"Query":"{{query}}"}
  """;

  HttpContent content = new StringContent(
    jsonContent, System.Text.Encoding.UTF8, "application/json");
  httpClient.DefaultRequestHeaders.Add("SessKey", sessKey);
  HttpResponseMessage response = await httpClient
    .PostAsync(apiUrl, content);

  if (!response.IsSuccessStatusCode)
  {
    MessageBox.Show("Error code: " + response.StatusCode);
    // <Insert your Logging function here>
    return;
  }

  var queryResponse = Newtonsoft.Json.JsonConvert
    .DeserializeObject<dynamic>(
      await response.Content.ReadAsStringAsync());
  var queryResult = queryResponse.ConsentGeneral_QueryResult;

  // Here are some of the important values 
  bool functionOk = (bool)queryResult.FunctionOk;
  int errCode = (int)queryResult.ErrCode;
  string errMsg = (string)queryResult.ErrMsg;
  string respMsg = (string)queryResult.RespMsg;

  // Check for unexpected error on server
  if (!functionOk)
  {
    MessageBox.Show(errMsg + " ErrorCode: " + errCode);
    // <Insert your Logging function here>
    return;
  }

  var consents = queryResult.Consents;

  // <Display your consents here>
}

```
{% endcode %}
{% endtab %}
{% endtabs %}



### Generate Receipt <a href="#generate-receipt" id="generate-receipt"></a>

An example of using [<mark style="color:green;">`ReceiptGenerate`</mark>](../../../api-reference/rest-api/receipt.md#apicardprocrest-v1.0.0-receipt-receiptgenerate) method.

{% tabs %}
{% tab title="C#" %}
{% code overflow="wrap" lineNumbers="true" %}
```csharp
public static async Task ShowReceipt(
  string sessKey, int refID, int receiptType, int recipient)
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


  using HttpClient httpClient = new HttpClient();
  string apiUrl = "https://easypay5.com/APIcardProcREST/v1.0.0/Receipt/ReceiptGenerate";

  string jsonContent = $$"""
    {"REFID":{{refID}}, "ReceiptType":{{receiptType}}, "Recipient":{{recipient}}}
  """;

  HttpContent content = new StringContent(
    jsonContent, System.Text.Encoding.UTF8, "application/json");
  httpClient.DefaultRequestHeaders.Add("SessKey", sessKey);
  HttpResponseMessage response = await httpClient
    .PostAsync(apiUrl, content);

  if (!response.IsSuccessStatusCode)
  {
    MessageBox.Show("Error code: " + response.StatusCode);
    // <Insert your Logging function here>
    return;
  }

  var receiptResponse = Newtonsoft.Json.JsonConvert
    .DeserializeObject<dynamic>(
      await response.Content.ReadAsStringAsync());
  var receiptResult = receiptResponse.ReceiptGenerateResult;

  // Here are some of the important values 
  bool functionOk = (bool)receiptResult.FunctionOk;
  int errCode = (int)receiptResult.ErrCode;
  string errMsg = (string)receiptResult.ErrMsg;
  string respMsg = (string)receiptResult.RespMsg;

  // Check for unexpected error on server
  if (!functionOk)
  {
    MessageBox.Show(errMsg + " ErrorCode: " + errCode);
    // <Insert your Logging function here>
    return;
  }

  /* Receipt generation successful. 
   * You may now add the HTML to your page.
   * <Logic to display HTML, e.g. 
   *  webBrowser1.DocumentText = response.ReceiptHtml;> */
}

```
{% endcode %}
{% endtab %}

{% tab title="JavaScript (Node.js)" %}
{% code overflow="wrap" lineNumbers="true" %}
```javascript
'use strict';

const http = require('http');
const https = require('https');

const port = process.env.PORT || 1337;

http.createServer((req, res) => {
    let body = '';

    // ReceiptType 1 TRANSACTION RECEIPT
    // ReceiptType 2 VOID RECEIPT
    // ReceiptType 3 REFUND RECEIPT
    // ReceiptType 4 ANNUAL CONSENT AGREEMENT
    // ReceiptType 5 RECURRING CONSENT AGREEMENT
    // ReceiptType 6 SUBSCRIPTION CONSENT AGREEMENT
    // Recipient 1 MERCHANT COPY
    // Recipient 2 CUSTOMER COPY
    // Recipient 3 DUAL COPY

    const data = JSON.stringify({
        REFID: 1,
        ReceiptType: 1,
        Recipient: 1
    });

    const options = {
        host: 'easypay5.com',
        port: 443,
        path: '/APIcardProcREST/v1.0.0/Receipt/ReceiptGenerate',
        timeout: 2000,
        method: 'POST',
        headers: {
            'Content-Type': 'application/json',
            'Content-Length': Buffer.byteLength(data),
            'Accept': 'application/json',
            'SessKey': '89C8356BB8A84FE9B5303231333441303331343335'
        }
    };

    const postReq = https.request(options, (postRes) => {
        let responseBody = '';

        postRes.on('data', (chunk) => {
            responseBody += chunk;
        });

        postRes.on('end', () => {
            try {
                if (responseBody === 'Bad Request') {
                    console.error('Bad request');
                    res.writeHead(400, { 'Content-Type': 'text/plain' });
                    res.end('Bad Request');
                    return;
                }

                const obj = JSON.parse(responseBody);

                if (!obj) {
                    console.error('Communication Error: Null Object');
                    res.writeHead(500, { 'Content-Type': 'text/plain' });
                    res.end('Communication Error: Null Object');
                    return;
                }

                const { ReceiptGenerateResult } = obj;

                if (!ReceiptGenerateResult.FunctionOk) {
                    console.error(`${ReceiptGenerateResult.ErrMsg} : ${ReceiptGenerateResult.ErrCode}`);
                    res.writeHead(500, { 'Content-Type': 'text/plain' });
                    res.end(`${ReceiptGenerateResult.ErrMsg} : ${ReceiptGenerateResult.ErrCode}`);
                    return;
                }

                console.log(ReceiptGenerateResult.RespMsg);
                const receiptHtml = ReceiptGenerateResult.ReceiptHtml;
                res.writeHead(200, { 'Content-Type': 'text/html' });
                res.end(receiptHtml);
            } catch (error) {
                console.error('Error parsing response:', error);
                res.writeHead(500, { 'Content-Type': 'text/plain' });
                res.end('Internal Server Error');
            }
        });
    });

    postReq.on('error', (error) => {
        console.error('Request error:', error);
        res.writeHead(500, { 'Content-Type': 'text/plain' });
        res.end('Request Error');
    });

    postReq.on('timeout', () => {
        console.error('Request timed out');
        res.writeHead(504, { 'Content-Type': 'text/plain' });
        res.end('Request Timeout');
    });

    postReq.write(data);
    postReq.end();
}).listen(port, () => {
    console.log(`Server listening on port ${port}`);
});
```
{% endcode %}


{% endtab %}
{% endtabs %}



