# Reset the Device

Sends a reset command to the terminal device, cancelling any active transaction and returning the device to idle state.

<mark style="color:orange;">POST</mark> https://`[your-terminal-ip]`:8090/reset\
Content-Type: application/json

#### Response Status Codes

* 200 OK - Reset command sent successfully.

{% tabs %}
{% tab title="Sample Request" %}
None needed. There is no body for this request.
{% endtab %}

{% tab title="Sample Response" %}
{% code overflow="wrap" %}
```
{
    "status": "OK",
    "message": "Device reset command sent"
}
```
{% endcode %}
{% endtab %}

{% tab title="Header Parameters" %}
None needed.
{% endtab %}
{% endtabs %}

