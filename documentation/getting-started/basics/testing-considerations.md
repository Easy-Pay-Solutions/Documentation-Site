# Testing Considerations

## **Responses**

When Processing using the API or the VeriFone Middleware you should be ready to consume the following types of responses:

1. Approvals
2. Declines
3. Aspen Errors (non-zero error code)
4. Exceptions within your processing layer (Timeouts or other Comm issues )

For PayForm and Virtual Terminal, all of this is handled for you, however when using the API or the VeriFone your software must properly consume and handle the above conditions.

_**Lets take a look at the API first**_

If you attempt an API call such as VOID a credit card transaction you should first set up to handle the exception.

```
try
{
    response = await httpClient.PostAsync(apiUrl, content);
}
catch (Exception ee)
{
    return "Exception : " + ee.Message;
}
```

You can easily test your ability to consume an Aspen Error by simply trying to Void a transaction that doesn’t exist. Try sending a large number beyond the number of transactions already committed.

```
{
    "TxID": 53000
}
```

The response will look like the following. Notice the FunctionOK flag is false which will be your QUE to look at the error code and log this condition:

```
{"Transaction_VoidResult":{
    "ErrCode":6724,
    "ErrMsg":"ERROR:6724:HIGH:Could NOT retrieve transaction details for TXID 53000",
    "FunctionOk":false,
    "RespMsg":"",
    "TxApproved":false,
    "TxID":0
    }
}
```

Even if no error is encountered you still might not have the successful VOID as the card issuer may **decline** the reversal. Always make sure you check the TxApproved Flag .

If the card issuer declines your reversal attempt you will notice that FunctionOK = True ( No Aspen Errors were encountered ) but TxApproved = False (issuer declined the reversal)

In this case you will Monitor the RespMsg for any further information regarding the decline

Here is the proper order when consuming the API response:

1. Catch any exception in communicating to EasyPay ( perhaps a Timeout )
2. Check status of FunctionOK flag ( If false then check and log error codes and error message)
3. Check any TxApproved or other success flags for final discovery of approved operation

### Verifone testing

To simulate a issuer decline using your test account you can send the following Amount ( $12345.67 ) . You will notice that the TxEventType = TxDecline and the RespMsg will describe the decline and the TxnCode will have a Decline Code.

To simulate an Aspen Error using your test account you can send the following Amount ( $12345.68 )

You will notice the TxEventType = AspenError , you will then monitor the ErrCode and ErrMsg

To Simulate our site being unavailable you can always create a Temporary Host Entry for EasyPay5.com to a Fake IP address.

Example : 99.99.99.99 easypay5.com

After you attempt a transaction, you will see a TxEventType = Exception with a particular error code and error message which you can log.

Remember to remove the host entry when finished.
