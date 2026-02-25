# Status

This health check endpoint returns the status of the device.

GET https://`[your-terminal-ip]`:8090/status\
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
`status` | System status ("OK" when operational) | | `message` | Human-readable status message | | `buildNumber` | Middleware build version | | `terminal.model` | Terminal hardware model | | `terminal.serialNumber` | Device serial number | | `terminal.manufacturer` | Terminal manufacturer | | `terminal.sdkVersion` | Ingenico USDK version | | `firmware.version` | Terminal firmware version | | `firmware.androidOS` | Android OS version | | `firmware.securityFirmware` | Security firmware version | | `arc.appName` | ARC application name | | `arc.appVersion` | ARC application version | | `arc.arclibVersion` | ARC library version | | `hardware.contactlessReader` | NFC/contactless reader available | | `hardware.smartCardReader` | EMV chip reader available | | `hardware.msrReader` | Magnetic stripe reader available | | `memory.totalRamMB` | Total RAM in megabytes | | `memory.availableRamMB` | Available RAM in megabytes | | `memory.totalFlashMB` | Total flash storage in megabytes | | `memory.availableFlashMB` | Available flash storage in megabytes | | `health.batteryLevel` | Battery percentage (0-100) | | `health.chargingState` | Charging status (Full, Charging, Discharging) | | `health.reboots` | Total device reboot count | | `health.cardSwipes` | Total MSR swipe count | | `health.chipInsertions` | Total chip insertion count
{% endtab %}
{% endtabs %}

