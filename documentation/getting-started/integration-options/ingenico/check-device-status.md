# Check Device Status

This health check endpoint returns the status of the device.

<mark style="color:orange;">GET</mark> https://`[your-terminal-ip]`:8090/status\
Content-Type: application/json

#### Response Status Codes

* 200 OK - System is operational.

{% tabs %}
{% tab title="Sample Request" %}
None needed. There is no body for this request.
{% endtab %}

{% tab title="Sample Response" %}
<pre><code>{
  "status": "OK",
  "message": "EasyPay Middleware is running",
  "buildNumber": "1.0",
  "terminal": {
    "model": "DX4000",
    "serialNumber": "242HMD438023",
    "manufacturer": "ingenico",
    "sdkVersion": "USDK V13.15.0-20241204"
  },
  "firmware": {
<strong>    "version": "AND-Q4-ALPHA 1.18.0",
</strong>    "androidOS": "10",
    "securityFirmware": "N11.11.11.00018"
  },
  "arc": {
    "appName": "AXIUM Retail Core",
    "appVersion": "24.05.01-0002-axium-iws",
    "arclibVersion": "24.05.01-0002-axium"
  },
  "hardware": {
    "contactlessReader": true,
    "smartCardReader": true,
    "msrReader": true
  },
  "memory": {
    "totalRamMB": 1867,
    "availableRamMB": 1003,
    "totalFlashMB": 14910,
    "availableFlashMB": 10095
  },
  "health": {
    "batteryLevel": "99",
    "chargingState": "Full",
    "reboots": "147",
    "cardSwipes": "71",
    "chipInsertions": "385"
  }
}
</code></pre>
{% endtab %}

{% tab title="Header Parameters" %}
None needed.
{% endtab %}

{% tab title="Body" %}
<table><thead><tr><th width="281.00006103515625">Field</th><th>Description</th></tr></thead><tbody><tr><td>status</td><td>System status ("OK" when operational)</td></tr><tr><td>message</td><td>Human-readable status message</td></tr><tr><td>buildNumber</td><td>Middleware build version</td></tr><tr><td>terminal.model</td><td>Terminal hardware model</td></tr><tr><td>terminal.serialNumber</td><td>Device serial number</td></tr><tr><td>terminal.manufacturer</td><td>Terminal manufacturer</td></tr><tr><td>terminal.sdkVersion</td><td>Ingenico USDK version</td></tr><tr><td>firmware.version</td><td>Terminal firmware version</td></tr><tr><td>firmware.androidOS</td><td>Android OS version</td></tr><tr><td>firmware.securityFirmware</td><td>Security firmware version</td></tr><tr><td>arc.appName</td><td>ARC application name</td></tr><tr><td>arc.appVersion</td><td>ARC application version</td></tr><tr><td>arc.arclibVersion</td><td>ARC library version</td></tr><tr><td>hardware.contactlessReader</td><td>NFC/contactless reader available</td></tr><tr><td>hardware.smartCardReader</td><td>EMV chip reader available</td></tr><tr><td>hardware.msrReader</td><td>Magnetic stripe reader available</td></tr><tr><td>memory.totalRamMB</td><td>Total RAM in megabytes</td></tr><tr><td>memory.availableRamMB</td><td>Available RAM in megabytes</td></tr><tr><td>memory.totalFlashMB</td><td>Total flash storage in megabytes</td></tr><tr><td>memory.availableFlashMB</td><td>Available flash storage in megabytes</td></tr><tr><td>health.batteryLevel</td><td>Battery percentage (0-100)</td></tr><tr><td>health.chargingState</td><td>Charging status (Full, Charging, Discharging)</td></tr><tr><td>health.reboots</td><td>Total device reboot count</td></tr><tr><td>health.cardSwipes</td><td>Total MSR swipe count</td></tr><tr><td>health.chipInsertions</td><td>Total chip insertion count</td></tr></tbody></table>
{% endtab %}
{% endtabs %}

