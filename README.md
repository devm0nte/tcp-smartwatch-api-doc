THIS IS SIMPLE API SERVICE FOR TCP SMARTWATCH PROJECT

DOMAIN : <https://api-watch.adcm.co.th/v1/>

---

# Project Tcp Smartwatch

---
# API Documentation

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

## License

[ADC MICROSYSTEMS](https://adcm.co.th)

---
