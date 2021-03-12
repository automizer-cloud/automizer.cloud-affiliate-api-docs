### Usage

Poll this endpoint to obtain smartlink information.

### URI / Method

* Endpoint (all smartlinks): `https://arbolith.com/api/smartlinks` (Method: `GET`)
* Endpoint (single smartlink): `https://arbolith.com/api/smartlinks/ID` (Method: `GET`)

### Response fields

Field                    | Data Type | Nullable | Notes
------------------------ | --------- | -------- | ---------------------------------------------------------------------
id                       | integer   | No       | Unique ID of the smartlink.
affiliate_id             | integer   | No       | Your affiliate ID.
affiliate_name           | string    | No       | Your affiliate name.
name                     | string    | No       | The name of the smartlink.
tracking_link            | string    | No       | Tracking link with required parameters. Check panel for optional parameters.
status                   | string    | No       | Smartlink status. Possible values: Active, Inactive. 
traffic_rating           | string    | Yes      | Traffic rating. Check the Related Entities section for a list of possible values.
incent                   | boolean   | Yes      | If the smartlink allows incent traffic.
expiration_date          | date      | Yes      | Expiration date in YYYY-MM-DD format.
daily_conversions_cap    | integer   | Yes      | The daily conversions cap.
monthly_conversions_cap  | integer   | Yes      | The monthly conversions cap.
payout_type              | string    | Yes      | The payout type. If null, the payout types of the offers involved are being used.
payout_value             | float     | Yes      | The payout value. If null, value is N/A or the payout values of the offers involved are being used.
countries                | array     | No       | List of country codes (ISO 3166) for targeting. Index indicates the operation (include/exclude).
devices                  | array     | No       | List of devices for targeting. Index indicates the operation (include/exclude). Check the Related Entities section for a list of possible values.  
operating_systems        | array     | No       | List of operating systems for targeting. Index indicates the operation (include/exclude). Check the Related Entities section for a list of possible values.
connection_types         | array     | No       | List of connection types for targeting. Index indicates the operation (include/exclude). Check the Related Entities section for a list of possible values.
carriers                 | array     | No       | List of carriers for targeting. Index indicates the operation (include/exclude). Check the Related Entities section for a list of possible values.

####Include/exclude behavior for targeting fields

* If the array key is "include", you should include the values specified. If the array is empty you should include all values.
* If the array key is "exclude", you should exclude the values specified. If the array is empty you should include all values.

### Sample Response

```
{
    "data": [
        {
            "id": 2,
            "affiliate_id": 16,
            "affiliate_name": "Cummings-O'Connell",
            "name": "Sample SmartLink 1",
            "tracking_link": "http://ads.bravads.com/click/s/?id=2",
            "status": "Inactive",
            "traffic_rating": "Mainstream",
            "incent": true,
            "expiration_date": "2018-03-13",
            "daily_conversions_cap": 1453,
            "monthly_conversions_cap": 25371,
            "payout_type": "RVS",
            "payout_value": null,
            "countries": {
                "exclude": [
                    "BD",
                    "LT"
                ]
            },
            "devices": {
                "exclude": [
                    "Tablet"
                ]
            },
            "operating_systems": {
                "exclude": [
                    "Android",
                    "iOS",
                    "Mac OS",
                    "Other/Unknown",
                    "Windows Phone"
                ]
            },
            "connection_types": {
                "include": [
                    "Dial-up",
                    "Other/Unknown"
                ]
            },
            "carriers": {
                "include": [
                    "Digi Mobil (IT)",
                    "Lumitel (BI)",
                    "Play (PL)"
                ]
            }
        },
        {
            // Another smartlink
        }
    ]
}
```
