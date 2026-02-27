# Get Configuration

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
\| Field | Type | Description | Default | |-------|------|-------------|---------| | `basePath` | string | Base URL for payment gateway API | `https://easypay5.com/APIcardProcREST/v1.0.0` | | `saleFromDevicePath` | string | Path appended to basePath for sale transactions | `/CardSale/FDevice` | | `voidPath` | string | Path appended to basePath for void/reversal transactions | `/CardSale/Void` | | `enableEmvDebug` | boolean | Include EMV tags in transaction responses for debugging | `false` | | `transactionTimeout` | integer | Card presentation timeout in seconds | `60` | | `errorDisplayDuration` | integer | Duration to display error messages on terminal (seconds) | `5` | | `approvalDisplayDuration` | integer | Duration to display approval message on terminal (seconds) | `4` |
{% endtab %}
{% endtabs %}

