### Usage

Poll this endpoint to obtain product information.

### URI / Method

* Endpoint (all products): `https://arbolith.com/api/products` (Method: `GET`)

### Response fields

Field                    | Data Type | Nullable | Notes
------------------------ | --------- | -------- | ---------------------------------------------------------------------
id                       | integer   | No       | Unique ID of the product.
name                     | string    | No       | The name of the product.
os                       | string    | No       | The operating system for targeting. Possible values: Android, iOS.
app_id                   | string    | No       | The App ID (Google Play / App Store).
tracking_link            | string    | No       | Tracking link with required parameters. Check panel for optional parameters.
status                   | string    | No       | Product status. Possible values: Active, Inactive. 
incent                   | boolean   | No       | If the product allows incent traffic.
expiration_date          | date      | Yes      | Expiration date in YYYY-MM-DD format.
daily_conversions_cap    | integer   | Yes      | The daily conversions cap.
monthly_conversions_cap  | integer   | Yes      | The monthly conversions cap.
payout_type              | string    | Yes      | The payout type. If null, the payout types of the offers involved are being used.
payout_value             | float     | Yes      | The payout value. If null, value is N/A or the payout values of the offers involved are being used.
countries                | array     | No       | List of country codes (ISO 3166) for targeting. Index indicates the operation (include/exclude).
devices                  | array     | No       | List of devices for targeting. Index indicates the operation (include/exclude). Check the Related Entities section for a list of possible values.  
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
            "id": 49,
            "name": "Product Name - Mainstream / Non-Incent",
            "os": "Android",
            "app_id": "UXqZv1tcwKJZhCZu9nc6QA3ifU622kOVoHRZbbIvV3puXmfbiF",
            "tracking_link": "http://adult.cleverlink.xyz/click/p/?id=49&affiliate_id=21",
            "status": "Inactive",
            "incent": false,
            "expiration_date": "2021-03-19",
            "daily_conversions_cap": 652,
            "monthly_conversions_cap": 15752,
            "payout_type": "RVS",
            "payout_value": null,
            "countries": {
                "exclude": [
                    "BG",
                    "UM"
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
            }
        },
        {
            // Another product
        }
    ]
}
```
