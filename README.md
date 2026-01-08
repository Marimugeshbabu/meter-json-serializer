# Meter JSON Serializer (Embedded Assignment)

This project implements an embedded-friendly JSON serialization library,
developed as part of a technical assignment for an embedded/firmware role.

---

## 📌 Project Overview

In embedded smart-meter and gateway systems, measurement data is collected
and stored internally using structured data types.  
This data must then be serialized into a strict JSON format before being
sent to a gateway or backend system.

This project focuses **only on the serialization step**, converting
structured C data into a predefined JSON format.

Out-of-scope topics such as radio communication, w-MBus, OMS, encryption,
and transport protocols are intentionally excluded.

---

## 📘 What is JSON?

JSON (JavaScript Object Notation) is a lightweight, human-readable text
format used to exchange structured data between systems.

Example:
```json
{
  "value": 107.752,
  "status": "OK"
}
🛠️ Design Approach
Meter and gateway data are modeled using C structures

JSON is generated manually using snprintf

No external JSON libraries are used

Buffer size checks prevent memory overflow

The library is transport-agnostic and hardware-independent

Suitable for embedded environments with limited resources

📂 Project Structure
pgsql
Copy code
include/    - Data models and public API
src/        - JSON serialization implementation
examples/   - Example application demonstrating usage
🔧 Public API
c
Copy code
int serialize_to_json(GatewayData *input,
                      char *output_buffer,
                      int buffer_size);
Serializes structured meter data into JSON

Writes output into a caller-provided buffer

Returns number of bytes written or error code

▶️ Example Output
The example application generates the following JSON output:

json
Copy code
[
  {
    "gatewayId": "gateway_1234",
    "date": "1970-01-01",
    "deviceType": "stromleser",
    "interval_minutes": 15,
    "total_readings": 1,
    "values": {
      "device_count": 1,
      "readings": [
        {
          "media": "water",
          "meter": "waterstarm",
          "deviceId": "stromleser_50898527",
          "unit": "m3",
          "data": [
            {
              "timestamp": "1970-01-01 00:00",
              "meter_datetime": "1970-01-01 00:00",
              "total_m3": 107.752,
              "status": "OK"
            }
          ]
        }
      ]
    }
  }
]
🧪 Example Application
A small example application is provided to:

Create sample input data

Call the serialization library

Output the generated JSON via serial or console logging

This simulates how embedded firmware would prepare data before sending it
to a gateway or backend system.

📝 Notes
External JSON libraries are intentionally avoided

Communication protocols are out of scope

The focus is on clean architecture, correctness, and embedded suitability

🚀 Possible Extensions
Support for multiple devices and data points

Deserialization (JSON → struct)

Integration with transport layers (MQTT, HTTP)











ChatGPT can make mistakes. Check
