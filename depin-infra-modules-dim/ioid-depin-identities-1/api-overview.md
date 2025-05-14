# API Overview

{% hint style="warning" %}
#### API Availability Notice

Important: The APIs described in this document are for reference only. They represent the intended design and functionality of the ioID platform but are not yet live or operational.

Please do not attempt to integrate or use these endpoints in production environments. We will update this documentation once the APIs are deployed and stable.
{% endhint %}

* **Generate an ioID for a device**

```
POST /api/v1/ioid/generate
```

```json
{
  "projectName": "SmartHome",
  "deviceIdentifier": "SN123456"
}
```

* **Bind an ioID to the owner's wallet**

```
POST /api/v1/ioid/owner/bind
```

```json
{
  "projectName": "SmartHome",
  "deviceSerial": "SN123456",
  "chainid": 1,
  "tokenContract": "0xabc",
  "tokenid": 123
}
```

* **Upload device metrics**

```
POST /api/upload-device-metrics
```

```json
{
  "uid": "device-id",
  "events": [{
    "publisher": "sensor-a",
    "timestamp": "2024-06-01T00:00:00Z",
    "custom": { "longitude": 1, "latitude": 1 }
  }]
}
```
