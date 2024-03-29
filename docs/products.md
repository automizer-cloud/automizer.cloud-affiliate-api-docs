### Usage

Poll this endpoint to obtain active product information.

### URI / Method

* Endpoint (all products): `https://automizer.cloud/api/products` (Method: `GET`)

### Response fields

Field                    | Data Type | Nullable | Notes
------------------------ |-----------|----------| ---------------------------------------------------------------------
id                       | integer   | No       | Unique ID of the product.
name                     | string    | No       | The name of the product.
os                       | string    | No       | The operating system for targeting. Possible values: Android, iOS.
versions                 | array     | No       | List of OS versions for targeting.
preview_url              | string    | Yes      | Preview url (playstore, appstore).
app_id                   | string    | Yes      | The App ID (Google Play / App Store).
tracking_link            | string    | No       | Tracking link with required parameters. Check panel for optional parameters.
start_hour               | int       | Yes      | Day parting start hour. Only present if end hour is set.
end_hour                 | int       | Yes      | Day parting end hour. Only present if start hour is set.
offset                   | string    | No       | Day parting offset (timezone).
hourly_impressions_cap   | integer   | Yes      | The hourly impressions cap.
hourly_clicks_cap        | integer   | Yes      | The hourly clicks cap.
daily_impressions_cap    | integer   | Yes      | The daily impressions cap.
daily_clicks_cap         | integer   | Yes      | The daily clicks cap.
daily_conversions_cap    | integer   | Yes      | The daily conversions cap.
daily_budget_cap         | float     | Yes      | The daily budget cap.
monthly_conversions_cap  | integer   | Yes      | The monthly conversions cap.
monthly_budget_cap       | float     | Yes      | The monthly budget cap.
total_budget_cap         | float     | Yes      | The total budget cap.
payout_type              | string    | Yes      | The payout type. If null, the payout types of the offers involved are being used.
payout_value             | float     | Yes      | The payout value. If null, value is N/A or the payout values of the offers involved are being used.
payout_goal              | string    | Yes      | The payout goal.
countries                | array     | No       | List of country codes (ISO 3166) for targeting. Index indicates the operation (include/exclude).
regions                  | array     | No       | List of regions for targeting. Index indicates the operation (include/exclude).
cities                   | array     | No       | List of cities for targeting. Index indicates the operation (include/exclude).
devices                  | array     | No       | List of devices for targeting. Index indicates the operation (include/exclude). Check the Related Entities section for a list of possible values.  
connection_types         | array     | No       | List of connection types for targeting. Index indicates the operation (include/exclude). Check the Related Entities section for a list of possible values.
carriers                 | array     | No       | List of carriers for targeting. Index indicates the operation (include/exclude). Check the Related Entities section for a list of possible values.
blacklisted_sub_ids      | array     | No       | List of blacklisted sub_ids.
whitelisted_sub_ids      | array     | No       | List of whitelisted sub_ids.

####Include/exclude behavior for targeting fields

* If the array key is "include", you should include the values specified. If the array is empty you should include all values.
* If the array key is "exclude", you should exclude the values specified. If the array is empty you should include all values.

### Sample Response

```
{
    "data": [
        {
            "id": 49,
            "name": "Sample Product 1",
            "os": "Android",
            "versions": [
                "11.0.0",
                "12.0.0"
            ],
            "preview_url": "https://play.google.com/store/apps/details?id=com.makemytrip",
            "app_id": "com.example.android",
            "tracking_link": "http://adult.cleverlink.xyz/click/p/?id=49&affiliate_id=21",
            "start_hour": 7,
            "end_hour": 21,
            "offset": "-03:00",
            "hourly_impressions_cap": 66692,
            "hourly_clicks_cap": 13395,
            "daily_impressions_cap": 666926,
            "daily_clicks_cap": 133955,
            "daily_conversions_cap": 652,
            "daily_budget_cap": 600.87,
            "monthly_conversions_cap": 15752,
            "monthly_budget_cap": 3000.50,
            "total_budget_cap": 6000.90,
            "payout_type": "RVS",
            "payout_value": null,
            "payout_goal": null,
            "countries": {
                "include": [
                    "SO"
                ]
            },
            "regions": {
                "include": [
                    "Jubbada Hoose"
                ]
            },
            "cities": {
                "exclude": [
                    "Kismayo"
                ]
            },
            "devices": {
                "include": [
                    "Mobile",
                    "Tablet"
                ]
            },
            "connection_types": {
                "exclude": [
                    "3G / 4G",
                    "Other/Unknown"
                ]
            },
            "carriers": {
                "exclude": [
                    "Inmarsat (GB)"
                ]
            },
            "blacklisted_sub_ids": [
                "1_kvl_0URk",
                "18_e6K_Qqbr",
                "24_uVV_gtds",
                "26_Pkn_vW0E",
                "7_CdV_Lzxu",
                "9_VzZ_W3zV"
            ],
            "whitelisted_sub_ids": [
                "12_5rD_DOBY",
                "29_gDa_4Ngg"
            ]
        },
        {
            // Another product
        }
    ]
}
```
