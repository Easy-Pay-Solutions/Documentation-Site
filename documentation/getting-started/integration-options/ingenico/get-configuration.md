# Get Device Configuration

Retrieves the current configuration settings.

GET https://`[your-terminal-ip]`:8090/config\
Content-Type: application/json

#### Response Status Codes

* 200 OK - Configuration retrieved successfully.

{% tabs %}
{% tab title="Sample Request" %}
None needed. There is no body for this request.
{% endtab %}

{% tab title="Sample Response" %}
```
 {
    "basePath": "https://easypay1.com/APIcardProcRESTV2/v2.0.0",
    "saleFromDevicePath": "/CardSale/FDevice",
    "voidPath": "/CardSale/Void",
    "enableEmvDebug": false,
    "transactionTimeout": 60,
    "errorDisplayDuration": 5,
    "approvalDisplayDuration": 4
  }
```
{% endtab %}

{% tab title="Header Parameters" %}
None needed.
{% endtab %}

{% tab title="Body" %}


<table><thead><tr><th width="186.79998779296875">Field</th><th width="109.199951171875">Type</th><th>Description</th><th>Default</th></tr></thead><tbody><tr><td>basePath</td><td>string</td><td>Base URL for payment gateway API</td><td>https://easypay5.com/APIcardProcREST/v1.0.0</td></tr><tr><td>saleFromDevicePath</td><td>string</td><td>Path appended to basePath for sale transactions</td><td>/CardSale/FDevice</td></tr><tr><td>voidPath</td><td>string</td><td>Path appended to basePath for void/reversal transactions</td><td>/CardSale/Void</td></tr><tr><td>enableEmvDebug</td><td>boolean</td><td>Include EMV tags in transaction responses for debugging</td><td>false</td></tr><tr><td>transactionTimeout</td><td>integer</td><td>Card presentation timeout in seconds</td><td>60</td></tr><tr><td>errorDisplayDuration</td><td>integer</td><td>Duration to display error messages on terminal (seconds)</td><td>5</td></tr><tr><td>approvalDisplayDuration</td><td>integer</td><td>Duration to display approval message on terminal (seconds)</td><td>4</td></tr></tbody></table>
{% endtab %}
{% endtabs %}

