# Meter JSON Serializer

This repository contains an embedded-friendly JSON serialization library
implemented as part of a technical assignment.

## Project Goal
The goal of this project is to convert structured meter and gateway data
stored in C data structures into a predefined JSON format.

The focus is on:
- Clean software architecture
- Embedded-oriented implementation
- Deterministic JSON output
- No use of external JSON libraries

## What is JSON?
JSON (JavaScript Object Notation) is a lightweight, human-readable text
format used to exchange data between systems using key-value pairs and arrays.

## Design Overview
- Data is represented using C structs
- JSON is generated manually using `snprintf`
- No dynamic memory allocation is used
- Buffer size is checked to prevent overflow
- The core library is transport-agnostic

## Project Structure
include/ Header files and data models
src/ JSON serialization logic
examples/ Example application

## Example Output
The example application generates the following JSON output:

```json
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
The example application prints the generated JSON to a serial or console
output for demonstration purposes.

Communication protocols and hardware interaction are intentionally out of scope
