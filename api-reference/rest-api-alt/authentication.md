# Authentication

**URL Endpoint: https://easypay5.com/APIcardProcREST/v1.0.0/Authenticate**

**Request Method: POST**

{% tabs %}
{% tab title="Headers" %}
In this method you will pass us TWO values:

* Account Code (never changes throughout the lifetime of your account)
* Token (expires every 2 years)

The goal is to retrieve a session key which will be used in all subsequent calls (placed in the header.)\
&#xNAN;_&#x54;he credentials below are samples only. Actual credentials will be sent upon request._
{% endtab %}

{% tab title="Untitled" %}

{% endtab %}

{% tab title="Sample Request" %}
```clike
{
  "AcctCode": "EP911XXXX",
  "Token": "2148B239CF6846BDA5D141BF4A4CFBE8"
}
```
{% endtab %}

{% tab title="Sample Response" %}
{% code overflow="wrap" %}
```clike
{
  "AuthenticateResult": {
    "AuthSuccess": true,
    "ErrCode": 0,
    "ErrMsg": "",
    "FunctionOk": true,
    "MerchantList": [
      {
        "Address": "45 spring street portland Maine 04101 ",
        "Descrip": "Test Merchant 1",
        "ID": 1,
        "Location": "Test Merchant 1",
        "TermID": "006"
      },
      {
        "Address": "78 spring street portland Maine 04101 ",
        "Descrip": "Lodging Merch",
        "ID": 2,
        "Location": "Lodging Merch",
        "TermID": "033"
      }
    ],
    "RespMsg": "SessKey Expires|4\/18\/2019 7:29:47 AM",
    "SessKey": "B9F24903C3BA4770AE303032303541303032353437",
    "ThisUser": {
      "APILocationID": 2210,
      "AccountCode": "EP9116875",
      "AcctID": 205,
      "Alias": "vidya_Venkatraman",
      "CreatedBy": "ADMIN : vidya Venkatraman",
      "DateCreated": "\/Date(1552318720210-0400)\/",
      "DateModified": "\/Date(1552318720210-0400)\/",
      "Description": "EP DEV ACCT",
      "ExpirationDate": "\/Date(1568216320210-0400)\/",
      "ID": 2547,
      "IsExpired": false,
      "IsLockedOut": false,
      "TokenDescription": "EP DEV ACCT"
    }
  }
}
```
{% endcode %}
{% endtab %}

{% tab title="C# Code" %}
{% code overflow="wrap" %}
```clike
private void AuthenticateRest()
        {
            // create JSON object with credentials ( using NewtonSoft Library  )   
            var MyCredentials = JObject.FromObject(new
           {    // insert your credentials here 
                AcctCode = "EP8449111",
                Token = "645E3CC4FD04472182C4161BA624C578"
            });

            byte[] data = Encoding.UTF8.GetBytes(MyCredentials.ToString());

            // create Request 
            WebRequest request = WebRequest.Create("https://easypay5.com/APIcardProcREST/v1.0.0/Authenticate");
            request.Method = "POST";
            request.ContentType = "application/json";
            request.ContentLength = data.Length;

            string Myheaders = request.Headers.ToString();
            string responseContent = null;

            // Using the Try block will catch communication errors 
            try
            {
                using (Stream stream = request.GetRequestStream())
                {
                    stream.Write(data, 0, data.Length);
                }
                using (WebResponse response = request.GetResponse())
                {
                    using (Stream stream = response.GetResponseStream())
                    {
                        using (StreamReader sr99 = new StreamReader(stream))
                        {
                            responseContent = sr99.ReadToEnd();
                        }
                    }
                }
            }
            catch (Exception ee)
            {
                MessageBox.Show("Problem communicating with EasyPay Service:" + ee.Message);
                /// important to insert your Logging function here 
                return;
            }

            // Check for null Response as this would be a critical communication error as well 
            if (responseContent == null)
            {
                MessageBox.Show("Critical Error , Null Response");
                /// important to insert your Logging function here 
                return;
            }

            /// develop Response Object 
            var Auth = Newtonsoft.Json.JsonConvert.DeserializeObject<dynamic>(responseContent);

            bool FunctionOk = (bool)Auth.AuthenticateResult.FunctionOk;
            bool AuthSuccess = (bool)Auth.AuthenticateResult.AuthSuccess;
            int ErrCode = (int)Auth.AuthenticateResult.ErrCode;
            string ErrMsg = (string)Auth.AuthenticateResult.ErrMsg;
            string RespMsg = (string)Auth.AuthenticateResult.RespMsg;

            //Check for unexpected Errors on cloud servers. If errors found Stop Processing and check ErrorCodes
            if (!FunctionOk)
            {
                MessageBox.Show(ErrMsg + "ErrorCode:" + ErrCode);
                /// important to insert your Logging function here 
                return;
            }

            //Check for failures uch as Invalid or Expired Credentials or Inactive Account.
            if (!AuthSuccess)
            {
                MessageBox.Show(RespMsg);
                /// important to insert your Logging function here 
                return;
            }

            /// Arriving here means that the Authentication was successful. You will retrieve a SessionKey and 
            /// a list of Merchant Records associated with this account. The session key will be used for all
            /// subsequent API calls 
            string SessKey = (string)Auth.AuthenticateResult.SessKey;
            var MerchantList = Auth.AuthenticateResult.MerchantList;

        }
```
{% endcode %}
{% endtab %}
{% endtabs %}

