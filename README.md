THIS IS SIMPLE API SERVICE FOR TCP SMARTWATCH PROJECT

DOMAIN : <https://api-watch.adcm.co.th/v1/>

---

# Project Tcp Smartwatch

---
# API Documentation

---

Table of Contents:

- [Project Tcp Smartwatch](#project-tcp-smartwatch)
- [API Documentation](#api-documentation)
  - [Watch List API](#watch-list-api)
    - [API Endpoint](#api-endpoint)
    - [Response](#response)
      - [Watch Fields](#watch-fields)
    - [Example Request](#example-request)
    - [Example Response](#example-response)
  - [Smart Watch Details API](#smart-watch-details-api)
    - [API Endpoint](#api-endpoint-1)
    - [Parameters](#parameters)
    - [Response](#response-1)
      - [Data Fields](#data-fields)
    - [Example Request](#example-request-1)
    - [Example Response](#example-response-1)
  - [Health List API](#health-list-api)
    - [API Endpoint](#api-endpoint-2)
    - [Response](#response-2)
      - [Health Record Fields](#health-record-fields)
    - [Example Request](#example-request-2)
    - [Example Response](#example-response-2)
  - [Health List by IMEI API](#health-list-by-imei-api)
    - [API Endpoint](#api-endpoint-3)
    - [Path Parameters](#path-parameters)
    - [Response](#response-3)
      - [Health Record Fields](#health-record-fields-1)
    - [Example Request](#example-request-3)
    - [Example Response](#example-response-3)
  - [Health History by IMEI API](#health-history-by-imei-api)
    - [API Endpoint](#api-endpoint-4)
    - [Path Parameters](#path-parameters-1)
    - [Query Parameters](#query-parameters)
    - [Response](#response-4)
      - [Health Record Fields](#health-record-fields-2)
    - [Example Request](#example-request-4)
    - [Example Response](#example-response-4)
  - [Emergency Log API](#emergency-log-api)
    - [API Endpoint](#api-endpoint-5)
      - [Get All Emergency Logs](#get-all-emergency-logs)
      - [Get Emergency Logs by IMEI](#get-emergency-logs-by-imei)
      - [Get Emergency SOS Logs](#get-emergency-sos-logs)
      - [Get Emergency Warning Logs](#get-emergency-warning-logs)
    - [Query Parameters](#query-parameters-1)
    - [Response](#response-5)
      - [Emergency Log Fields](#emergency-log-fields)
        - [Payload Fields](#payload-fields)
    - [Example Requests](#example-requests)
      - [Get All Emergency Logs](#get-all-emergency-logs-1)
      - [Get Emergency Logs by IMEI](#get-emergency-logs-by-imei-1)
    - [Example Response](#example-response-5)
  - [Watch Interval Command API](#watch-interval-command-api)
    - [API Endpoint](#api-endpoint-6)
      - [Set Interval for Health Data Collection](#set-interval-for-health-data-collection)
    - [Request Body](#request-body)
    - [Response](#response-6)
    - [Example Request](#example-request-5)
      - [Set Interval for Health Data Collection](#set-interval-for-health-data-collection-1)
    - [Example Response](#example-response-6)
  - [Watch Temperature Command API](#watch-temperature-command-api)
    - [API Endpoint](#api-endpoint-7)
      - [Send Temperature Check Command](#send-temperature-check-command)
    - [Request Body](#request-body-1)
    - [Response](#response-7)
    - [Example Request](#example-request-6)
      - [Send Temperature Check Command](#send-temperature-check-command-1)
    - [Example Response](#example-response-7)
  - [Watch Heart Rate Command API](#watch-heart-rate-command-api)
    - [API Endpoint](#api-endpoint-8)
      - [Send Heart Rate Check Command](#send-heart-rate-check-command)
    - [Request Body](#request-body-2)
    - [Response](#response-8)
    - [Example Request](#example-request-7)
      - [Send Heart Rate Check Command](#send-heart-rate-check-command-1)
    - [Example Response](#example-response-8)
  - [License](#license)

---

## Watch List API

This API provides a list of watches.

### API Endpoint

```
GET https://api-watch.adcm.co.th/v1/watch/
```

### Response

The API response will be in JSON format and will contain the following fields:

- `type` (string): The response type. Possible values: "success".
- `status` (integer): The HTTP status code of the response. Possible values: 200.
- `message` (string): A message describing the response.
- `pagination` (object): Pagination details for the watch list.
  - `all_rows` (integer): The total number of rows in the watch list.
  - `all_pages` (integer): The total number of pages in the watch list.
  - `page_limit` (integer): The maximum number of watches per page.
  - `page_number` (integer): The current page number.
- `length` (integer): The number of watches in the current response.
- `data` (array): An array containing the watch details.

#### Watch Fields

Each watch object in the `data` array contains the following fields:

- `id` (integer): The unique identifier of the watch.
- `imei` (string): The IMEI (International Mobile Equipment Identity) number of the watch.
- `model` (string): The model of the watch.
- `type` (string): The type of the watch.
- `status` (string): The current status of the watch.
- `location` (object): The location coordinates of the watch. It may be null if the location is unavailable.
  - `latitude` (float): The latitude coordinate of the watch.
  - `longitude` (float): The longitude coordinate of the watch.

### Example Request

```
GET https://api-watch.adcm.co.th/v1/watch/
```

### Example Response

```json
{
  "type": "success",
  "status": 200,
  "message": "Watch list",
  "pagination": {
    "all_rows": 2,
    "all_pages": 1,
    "page_limit": 10,
    "page_number": 1
  },
  "length": 2,
  "data": [
    {
      "id": 1,
      "imei": "865513041161826",
      "model": "LP19",
      "type": "test",
      "status": "online",
      "location": {
        "latitude": 16.748108333333334,
        "longitude": 100.20354
      }
    },
    {
      "id": 2,
      "imei": "865513041164663",
      "model": "LP18",
      "type": "test2",
      "status": "offline",
      "location": null
    }
  ]
}
```

---

## Smart Watch Details API

This API provides information about a smart watch using its IMEI (International Mobile Equipment Identity) number.

### API Endpoint

```
GET https://api-watch.adcm.co.th/v1/watch/imei/{imei}
```

### Parameters

| Parameter | Description                              |
|-----------|------------------------------------------|
| imei      | The IMEI (International Mobile Equipment Identity) number of the smart watch. |

### Response

The API response will be in JSON format and will contain the following fields:

- `type` (string): The response type. Possible values: "success".
- `status` (integer): The HTTP status code of the response. Possible values: 200.
- `message` (string): A message describing the response.
- `data` (object): The data object containing the details of the smart watch.

#### Data Fields

The `data` object contains the following fields:

- `id` (integer): The unique identifier of the smart watch.
- `imei` (string): The IMEI (International Mobile Equipment Identity) number of the smart watch.
- `model` (string): The model of the smart watch.
- `type` (string): The type of the smart watch.
- `status` (string): The current status of the smart watch.
- `location` (object): The location coordinates of the smart watch.
  - `latitude` (float): The latitude coordinate of the smart watch.
  - `longitude` (float): The longitude coordinate of the smart watch.
- `last_update` (string): The timestamp of the last update for the smart watch.
- `last_health` (object): The health data of the smart watch.
  - `temperature` (object): The temperature data.
    - `value` (float): The temperature value.
    - `datetime` (string): The timestamp of the temperature reading.
  - `heartrate` (object): The heart rate data.
    - `value` (integer): The heart rate value.
    - `datetime` (string): The timestamp of the heart rate reading.
  - `sbp` (object): The systolic blood pressure data.
    - `value` (integer): The systolic blood pressure value.
    - `datetime` (string): The timestamp of the systolic blood pressure reading.
  - `dbp` (object): The diastolic blood pressure data.
    - `value` (integer): The diastolic blood pressure value.
    - `datetime` (string): The timestamp of the diastolic blood pressure reading.
  - `spo2` (object): The blood oxygen saturation data.
    - `value` (integer): The blood oxygen saturation value.
    - `datetime` (string): The timestamp of the blood oxygen saturation reading.
  - `bs` (object): The blood sugar data.
    - `value` (integer): The blood sugar value.
    - `datetime` (string): The timestamp of the blood sugar reading.

### Example Request

```
GET https://api-watch.adcm.co.th/v1/watch/imei/865513041161826
```

### Example Response

```json
{
  "type": "success",
  "status": 200,
  "message": "Smart Watch details by imei : 865513041161826",
  "data": {
    "id": 1,
    "imei": "865513041161826",
    "model": "LP19",
    "type": "test",
    "status": "online",
    "location": {
      "latitude": 16.748108333333334,
      "longitude": 100.20354
    },


    "last_update": "2023-05-22 10:13:38",
    "last_health": {
      "temperature": {
        "value": 36.4,
        "datetime": "2023-05-19 15:00:32"
      },
      "heartrate": {
        "value": 71,
        "datetime": "2023-05-22 10:58:32"
      },
      "sbp": {
        "value": 117,
        "datetime": "2023-05-22 10:58:32"
      },
      "dbp": {
        "value": 80,
        "datetime": "2023-05-22 10:58:32"
      },
      "spo2": {
        "value": 97,
        "datetime": "2023-05-22 10:58:32"
      },
      "bs": {
        "value": 0,
        "datetime": "2023-05-22 10:58:32"
      }
    }
  }
}
```

---

## Health List API

This API provides a list of health records.

### API Endpoint

```
GET https://api-watch.adcm.co.th/v1/health/
```

### Response

The API response will be in JSON format and will contain the following fields:

- `type` (string): The response type. Possible values: "success".
- `status` (integer): The HTTP status code of the response. Possible values: 200.
- `message` (string): A message describing the response.
- `pagination` (object): Pagination details for the health list.
  - `all_rows` (integer): The total number of rows in the health list.
  - `all_pages` (integer): The total number of pages in the health list.
  - `page_limit` (integer): The maximum number of health records per page.
  - `page_number` (integer): The current page number.
- `length` (integer): The number of health records in the current response.
- `data` (array): An array containing the health records.

#### Health Record Fields

Each health record object in the `data` array contains the following fields:

- `id` (integer): The unique identifier of the health record.
- `datetime` (string): The timestamp of the health record.
- `smart_watch_id` (integer): The ID of the smart watch associated with the health record.
- `temperature` (float): The temperature value recorded in the health record.
- `heart_rate` (integer): The heart rate value recorded in the health record. It may be null if the heart rate is unavailable.
- `sbp` (integer): The systolic blood pressure value recorded in the health record. It may be null if the systolic blood pressure is unavailable.
- `dbp` (integer): The diastolic blood pressure value recorded in the health record. It may be null if the diastolic blood pressure is unavailable.
- `spo2` (integer): The blood oxygen saturation value recorded in the health record. It may be null if the blood oxygen saturation is unavailable.
- `bs` (integer): The blood sugar value recorded in the health record. It may be null if the blood sugar is unavailable.

### Example Request

```
GET https://api-watch.adcm.co.th/v1/health/
```

### Example Response

```json
{
  "type": "success",
  "status": 200,
  "message": "Health list",
  "pagination": {
    "all_rows": 108,
    "all_pages": 11,
    "page_limit": 10,
    "page_number": 1
  },
  "length": 10,
  "data": [
    {
      "id": 1,
      "datetime": "2023-04-20T09:58:48.466Z",
      "smart_watch_id": 1,
      "temperature": 36.6,
      "heart_rate": null,
      "sbp": null,
      "dbp": null,
      "spo2": null,
      "bs": null
    },
    {
      "id": 2,
      "datetime": "2023-04-20T10:00:46.675Z",
      "smart_watch_id": 1,
      "temperature": null,
      "heart_rate": 88,
      "sbp": 114,
      "dbp": 77,
      "spo2": null,
      "bs": null
    },
    {
      "id": 3,
      "datetime": "2023-04-20T10:02:41.299Z",
      "smart_watch_id": 1,
      "temperature": null,
      "heart_rate": 73,
      "sbp": 116,
      "dbp": 76,
      "spo2": 98,
      "bs": 0
    },
    ...
  ]
}
```

---

## Health List by IMEI API

This API provides a list of health records for a specific smartwatch identified by IMEI.

### API Endpoint

```
GET https://api-watch.adcm.co.th/v1/health/imei/{imei}
```

### Path Parameters

- `imei` (string): The IMEI (International Mobile Equipment Identity) number of the smartwatch.

### Response

The API response will be in JSON format and will contain the following fields:

- `type` (string): The response type. Possible values: "success".
- `status` (integer): The HTTP status code of the response. Possible values: 200.
- `message` (string): A message describing the response.
- `length` (integer): The number of health records in the current response.
- `data` (array): An array containing the health records for the specified smartwatch.

#### Health Record Fields

Each health record object in the `data` array contains the following fields:

- `datetime` (string): The timestamp of the health record.
- `temperature` (float): The temperature value recorded in the health record. It may be null if the temperature is unavailable.
- `heart_rate` (integer): The heart rate value recorded in the health record. It may be null if the heart rate is unavailable.
- `sbp` (integer): The systolic blood pressure value recorded in the health record. It may be null if the systolic blood pressure is unavailable.
- `dbp` (integer): The diastolic blood pressure value recorded in the health record. It may be null if the diastolic blood pressure is unavailable.
- `spo2` (integer): The blood oxygen saturation value recorded in the health record. It may be null if the blood oxygen saturation is unavailable.
- `bs` (integer): The blood sugar value recorded in the health record. It may be null if the blood sugar is unavailable.

### Example Request

```
GET https://api-watch.adcm.co.th/v1/health/imei/865513041161826
```

### Example Response

```json
{
  "type": "success",
  "status": 200,
  "message": "Health list by imei : 865513041161826",
  "length": 108,
  "data": [
    {
      "datetime": "2023-05-22 11:08:32",
      "temperature": null,
      "heart_rate": 79,
      "sbp": 122,
      "dbp": 71,
      "spo2": 96,
      "bs": 0
    },
    {
      "datetime": "2023-05-22 11:03:32",
      "temperature": null,
      "heart_rate": 88,
      "sbp": 128,
      "dbp": 80,
      "spo2": 98,
      "bs": 0
    },
    {
      "datetime": "2023-05-22 10:58:32",
      "temperature": null,
      "heart_rate": 71,
      "sbp": 117,
      "dbp": 80,
      "spo2": 97,
      "bs": 0
    },
    ...
  ]
}
```

---

## Health History by IMEI API

This API provides a history of health records for a specific smartwatch identified by IMEI and a specified date.

### API Endpoint

```
GET https://api-watch.adcm.co.th/v1/health/imei/{imei}/history?date={date}
```

### Path Parameters

- `imei` (string): The IMEI (International Mobile Equipment Identity) number of the smartwatch.

### Query Parameters

- `date` (string): The date for which to retrieve the health history. Format: "YYYY-MM-DD".

### Response

The API response will be in JSON format and will contain the following fields:

- `type` (string): The response type. Possible values: "success".
- `status` (integer): The HTTP status code of the response. Possible values: 200.
- `message` (string): A message describing the response.
- `length` (integer): The number of health records in the current response.
- `data` (array): An array containing the health records for the specified smartwatch and date.

#### Health Record Fields

Each health record object in the `data` array contains the following fields:

- `datetime` (string): The timestamp of the health record.
- `temperature` (float): The temperature value recorded in the health record. It may be null if the temperature is unavailable.
- `heart_rate` (integer): The heart rate value recorded in the health record. It may be null if the heart rate is unavailable.
- `sbp` (integer): The systolic blood pressure value recorded in the health record. It may be null if the systolic blood pressure is unavailable.
- `dbp` (integer): The diastolic blood pressure value recorded in the health record. It may be null if the diastolic blood pressure is unavailable.
- `spo2` (integer): The blood oxygen saturation value recorded in the health record. It may be null if the blood oxygen saturation is unavailable.
- `bs` (integer): The blood sugar value recorded in the health record. It may be null if the blood sugar is unavailable.

### Example Request

```
GET https://api-watch.adcm.co.th/v1/health/imei/865513041161826/history?date=2023-05-20
```

### Example Response

```json
{
  "type": "success",
  "status": 200,
  "message": "Health list by imei : 865513041161826",
  "length": 69,
  "data": [
    {
      "datetime": "2023-05-20 06:35:32",
      "temperature": null,
      "heart_rate": 141,
      "sbp": 123,
      "dbp": 78,
      "spo2": 98,
      "bs": 0
    },
    {
      "datetime": "2023-05-20 06:30:32",
      "temperature": null,
      "heart_rate": 84,
      "sbp": 117,
      "dbp": 79,
      "spo2": 95,
      "bs": 0
    },
    {
      "datetime": "2023-05-20 06:25:32",
      "temperature": null,
      "heart_rate": 96,
      "sbp": 121,
      "dbp": 78,
      "spo2": 97,
      "bs": 0
    },
    ...
  ]
}
```

---


## Emergency Log API

This API provides access to emergency log data.

### API Endpoint

#### Get All Emergency Logs

This endpoint access to all emergency log data.

```
GET https://api-watch.adcm.co.th/v1/emergency
```

#### Get Emergency Logs by IMEI

This endpoint access to all emergency log data. query by imei number

```
GET https://api-watch.adcm.co.th/v1/emergency?imei={imei}
```

#### Get Emergency SOS Logs

This endpoint access to emergency log data. in SOS state only

```
GET https://api-watch.adcm.co.th/v1/emergency/sos
```

#### Get Emergency Warning Logs

This endpoint access to emergency log data. in non sos state

```
GET https://api-watch.adcm.co.th/v1/emergency/warning
```

### Query Parameters

- `imei` (string): The IMEI (International Mobile Equipment Identity) number of the smartwatch. (Optional)

### Response

The API response will be in JSON format and will contain the following fields:

- `type` (string): The response type. Possible values: "success".
- `status` (integer): The HTTP status code of the response. Possible values: 200.
- `message` (string): A message describing the response.
- `pagination` (object): Pagination information.
  - `all_rows` (integer): The total number of emergency logs.
  - `all_pages` (integer): The total number of pages.
  - `page_limit` (integer): The maximum number of logs per page.
  - `page_number` (integer): The current page number.
- `length` (integer): The number of emergency logs in the current response.
- `data` (array): An array containing the emergency log records.

#### Emergency Log Fields

Each emergency log object in the `data` array contains the following fields:

- `id` (integer): The ID of the emergency log.
- `datetime` (string): The timestamp of the emergency log.
- `smart_watch_id` (integer): The ID of the associated smartwatch.
- `location` (object): The location information. It may be null if the location is unavailable.
- `alarm_state` (string): The state of the alarm.- `alarm_state` [00: no alarm, 01：SOS, 03: not wear, 05/06：fall down alarm]
- `battery_level` (string): The battery level.
- `payload` (object): Additional payload data.
- `metadata` (object): Additional metadata. It may be null.

##### Payload Fields

The `payload` object contains various fields specific to the emergency log. The structure and fields may vary depending on the log's data.

### Example Requests

#### Get All Emergency Logs

```
GET https://api-watch.adcm.co.th/v1/emergency
```

#### Get Emergency Logs by IMEI

```
GET https://api-watch.adcm.co.th/v1/emergency?imei={imei}
```

### Example Response

```json
{
  "type": "success",
  "status": 200,
  "message": "All Emergency log list",
  "pagination": {
    "all_rows": 2,
    "all_pages": 1,
    "page_limit": 10,
    "page_number": 1
  },
  "length": 2,
  "data": [
    {
      "id": 3,
      "datetime": "2023-05-31T16:58:57.456Z",
      "smart_watch_id": 1,
      "location": null,
      "alarm_state": "03",
      "battery_level": "049",
      "payload": {
        "date": "2031-05-23",
        "gmtTime": "235855",
        "lbsData": "0000.0000N00000.0000E000.1",
        "gsmSignal": "080",
        "alarmState": "03",
        "identifier": "IW",
        "satellites": "000",
        "commandWord": "AP10",
        "lbsBaseData": {
          "cid": "42293617",
          "lac": "16664",
          "mcc": "520",
          "mnc": "3"
        },
        "workingMode": "01",
        "batteryLevel": "049",
        "dataValidity": "V",
        "replyAddress": "0",
        "deviceLanguage": "zh-cn",
        "directionAngle": "323.87",
        "remainingSpace": "0",
        "mobileHyperlink": "0",
        "wifiInformation": [
          {
            "ssid": "a",
            "macAddress": "9c-6f-52-f2-4e-be",
            "signalStrength": "111"
          }
        ],
        "fortificationState": "00"
      },
      "metadata": null
    },
    {
      "id": 2,
      "datetime": "2023-05-31T16:53:57.303Z",
      "smart_watch_id": 1,
      "location": null,
      "alarm_state": "03",
      "battery_level": "049",
      "payload": {
        "date": "2031-05-23",
        "gmtTime": "235355",
        "lbsData": "0000.0000N00000.0000E000.1",
        "gsmSignal": "080",
        "alarmState": "03",
        "identifier": "IW",
        "satellites": "000",
        "commandWord": "AP10",
        "lbsBaseData": {
          "cid": "42293617",
          "lac": "16664",
          "mcc": "520",
          "mnc": "3"
        },
        "workingMode": "01",
        "batteryLevel": "049",
        "dataValidity": "V",
        "replyAddress": "0",
        "deviceLanguage": "zh-cn",
        "directionAngle": "323.87",
        "remainingSpace": "0",
        "mobileHyperlink": "0",
        "wifiInformation": [
          {
            "ssid": "a",
            "macAddress": "9c-6f-52-f2-4e-be",
            "signalStrength": "105"
          }
        ],
        "fortificationState": "00"
      },
      "metadata": null
    }
  ]
}
```

---

## Watch Interval Command API

This API allows you to set the interval for health data collection on a smartwatch. The health data will be send from smartwatch every interval minute (device minimum 2 minute)

### API Endpoint

#### Set Interval for Health Data Collection

```
POST https://api-watch.adcm.co.th/v1/command/watch/interval
```

### Request Body

The request body should be in JSON format and should contain the following fields:

- `imei_number` (string): The IMEI (International Mobile Equipment Identity) number of the smartwatch.
- `interval_minute` (integer): The interval in minutes for health data collection.

### Response

The API response will be in JSON format and will contain the following fields:

- `type` (string): The response type. Possible values: "created".
- `status` (integer): The HTTP status code of the response. Possible values: 201.
- `message` (string): A message describing the response.

### Example Request

#### Set Interval for Health Data Collection

```
POST https://api-watch.adcm.co.th/v1/command/watch/interval

Body:
{
  "imei_number": "865513041161826",
  "interval_minute": 10
}
```

### Example Response

```json
{
  "type": "created",
  "status": 201,
  "message": "Command to set interval health : 865513041161826 every 10 minute"
}
```

---

## Watch Temperature Command API

This API allows you to send a command to a smartwatch to check the temperature. The data will send to Database within 1 minute after send command (if wearing smartwatch)

### API Endpoint

#### Send Temperature Check Command

```
POST https://api-watch.adcm.co.th/v1/command/watch/temperature
```

### Request Body

The request body should be in JSON format and should contain the following field:

- `imei_number` (string): The IMEI (International Mobile Equipment Identity) number of the smartwatch.

### Response

The API response will be in JSON format and will contain the following fields:

- `type` (string): The response type. Possible values: "created".
- `status` (integer): The HTTP status code of the response. Possible values: 201.
- `message` (string): A message describing the response.

### Example Request

#### Send Temperature Check Command

```
POST https://api-watch.adcm.co.th/v1/command/watch/temperature

Body:
{
  "imei_number": "865513041161826"
}
```

### Example Response

```json
{
  "type": "created",
  "status": 201,
  "message": "Sent Command to check temperature : 865513041161826"
}
```

---

## Watch Heart Rate Command API

This API allows you to send a command to a smartwatch to check the heart rate. The data will send to Database within 1 minute after send command (if wearing smartwatch)

### API Endpoint

#### Send Heart Rate Check Command

```
POST https://api-watch.adcm.co.th/v1/command/watch/heartrate
```

### Request Body

The request body should be in JSON format and should contain the following field:

- `imei_number` (string): The IMEI (International Mobile Equipment Identity) number of the smartwatch.

### Response

The API response will be in JSON format and will contain the following fields:

- `type` (string): The response type. Possible values: "created".
- `status` (integer): The HTTP status code of the response. Possible values: 201.
- `message` (string): A message describing the response.

### Example Request

#### Send Heart Rate Check Command

```
POST https://api-watch.adcm.co.th/v1/command/watch/heartrate

Body:
{
  "imei_number": "865513041161826"
}
```

### Example Response

```json
{
  "type": "created",
  "status": 201,
  "message": "Sent Command to check heartrate : 865513041161826"
}
```

---


## License

[ADC MICROSYSTEMS](https://adcm.co.th)

---
