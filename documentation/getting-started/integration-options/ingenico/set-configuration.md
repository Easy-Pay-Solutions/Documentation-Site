# Set Configuration

Updates the middleware runtime configuration settings. All fields are optional; send only the fields you want to update.

Changes take effect immediately for subsequent transactions.

POST https://`[your-terminal-ip]`:8090/config\
Content-Type: application/json

#### Response Status Codes

* 200 OK - Configuration updated successfully.
* 400 Bad Request - Invalid JSON or field values

{% tabs %}
{% tab title="Sample Request" %}


```
{
    "basePath": "https://easypay5.com/APIcardProcREST/v1.0.0",
    "saleFromDevicePath": "/CardSale/FDevice",
    "voidPath": "/CardSale/Void",
    "enableEmvDebug": false,
    "transactionTimeout": 60,
    "errorDisplayDuration": 5,
    "approvalDisplayDuration": 4
  }
```

**Partial update example**

Enable debug mode and increase timeout:

```

      {
        "enableEmvDebug": true,
        "transactionTimeout": 120
      }
```
{% endtab %}

{% tab title="Sample Response" %}
Returns the complete current configuration after update:

```

  {
    "basePath": "https://easypay5.com/APIcardProcREST/v1.0.0",
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

