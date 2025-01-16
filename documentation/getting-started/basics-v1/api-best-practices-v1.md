---
description: A list of best practices for working with the APIs
---

# API Best Practices (v1)

## Logging

It's important to correctly handle exceptions and log all the responses. Before you interface with our APIs, we recommend creating a simple logging utility. This way, there'll be a trail of breadcrumbs in case any issues arise in the future. Without logs, finding out what went wrong can be time consuming.



### Recommended way to log the responses

{% stepper %}
{% step %}
#### Create a utility class for logging

It should contain a method that will take the API call name as well as `FunctionOk`, `IsSuccess`, `RespMsg`, `ErrCode`, and `ErrMsg` values. This will compile all of the information necessary to track any issue.

Store the timestamp of the response and all of those values in a database record or as a row in a log file. When logging to a file, it's recommended to roll onto a new file on a monthly basis.
{% endstep %}

{% step %}
#### Use the utility class to log all API results

Log all of the responses, including successful ones, using your utility class.
{% endstep %}
{% endstepper %}



### Logging class example

{% tabs %}
{% tab title="C#" %}
{% code overflow="wrap" lineNumbers="true" fullWidth="true" %}
```csharp
namespace APITest
{
  public static class LoggingUtil
  {
    private const string PATH = "C:\\Logs\\Payments\\";

    private static readonly object _locker = new();

    /// <summary>
    /// Log the API response and return logging success.
    /// </summary>
    /// <returns>True if logged successfully, otherwise false.</returns>
    public static bool LogResponse(string apiCallName, bool FunctionOK,
      bool IsSuccess, string RespMsg, int ErrorCode, string ErrMsg)
    {
      try
      {
        if (string.IsNullOrEmpty(RespMsg))
          RespMsg = "N/A";

        // Ensure the directory exists
        if (!Directory.Exists(PATH))
        {
          Directory.CreateDirectory(PATH);
        }

        string myMonthlyFileName = DateTime.Now.Year.ToString("D4")
          + "_" + DateTime.Now.Month.ToString("D2") + ".log";
        string timeStamp = DateTime.Now.ToString("yyyy/MM/dd HH:mm:ss.ff");
        string message = timeStamp + "," + apiCallName + "," + FunctionOK.ToString() + ","
          + IsSuccess.ToString() + "," + RespMsg + "," + ErrorCode.ToString() + "," + ErrMsg;
        bool fileExists = File.Exists(PATH + myMonthlyFileName);

        lock (_locker)
        {
          // Use StreamWriter with 'using' statement to ensure proper resource disposal
          using (StreamWriter swriter = File.AppendText(PATH + myMonthlyFileName))
          {
            // Place a header in each new monthly log file
            if (!fileExists)
              swriter.WriteLine("Timestamp,apiCallName,FunctionOK,IsSuccess,RespMsg,ErrorCode,ErrMsg");

            // Write the response as a new line
            swriter.WriteLine(message);
          }
        }
        return true;
      }
      catch (Exception ex)
      {
        // Optionally log or handle the exception here
        return false;
      }
    }
  }
}

```
{% endcode %}
{% endtab %}
{% endtabs %}



## Preventing Duplicate Charges

A common issue we encounter is complaints about duplicate charges. This can happen when integrators process card-on-file transactions without proper safeguards that prevent submitting the same form multiple times.

If there is button on a webpage that initiates a charge, and there is no mechanism preventing it from being clicked multiple times, the cardholder would be charged each time. To prevent this, it's crucial to disable the button immediately after it's pressed, ensuring that double taps do not occur.&#x20;

{% hint style="warning" %}
When processing card-on-file transactions, remember to lock the submit button after form submission to prevent multiple API calls and duplicate charges from occuring.

You may also choose to include simple logic that checks `ConsentID` and `TransactionAmount` that would prevent the same combination from being processed multiple times within a short timeframe.
{% endhint %}



