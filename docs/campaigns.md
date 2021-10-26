### Usage

Poll this endpoint to obtain campaign information.

### URI / Method

* Endpoint (all campaigns): `https://automizer.cloud/api/campaigns` (Method: `GET`)

### Response fields

Field                           | Data Type | Nullable | Notes
------------------------------- | --------- | -------- | --------------------------------------------------------------
id                              | integer   | No       | Unique ID of the campaign.
name                            | string    | No       | The name of the campaign.
affiliate_id                    | integer   | No       | Your affiliate ID.
affiliate_name                  | string    | No       | Your affiliate name.
offer_id                        | integer   | No       | The ID of the offer your campaign is based on.
offer_name                      | string    | No       | The name of the offer that your campaign is based on.
description                     | text      | Yes      | Description text.
preview_url                     | string    | Yes      | Preview url (playstore, appstore or image hosting).
tracking_link                   | string    | No       | Tracking link with required parameters. Check panel for optional parameters.
impression_url                  | string    | Yes      | Impression url.
mandatory_url_params            | boolean   | No       | If the campaign has mandatory URL parameters.
mandatory_url_appname           | boolean   | No       | If the offer's appname is a mandatory URL parameter.
mandatory_url_device_id         | boolean   | No       | If the offer's device_id is a mandatory URL parameter.
terms_and_conditions            | boolean   | No       | If the campaign has terms and conditions.
additional_terms_and_conditions | text      | Yes      | The terms and conditions text.
status                          | string    | No       | Campaign status. Possible values: Active, Inactive.
start_hour                      | integer   | Yes      | The traffic start hour. 
end_hour                        | integer   | Yes      | The traffic end hour.
expiration_date                 | date      | Yes      | Expiration date in YYYY-MM-DD format.
daily_conversions_cap           | integer   | Yes      | The daily conversions cap.
monthly_conversions_cap         | integer   | Yes      | The monthly conversions cap.
payout_type                     | string    | No       | The payout type. Check the Related Entities section for a list of possible values.
payout_value                    | float     | Yes      | The payout value. If null, value is N/A.
payout_goal                     | string    | Yes      | The payout goal.
dynamic_payout                  | boolean   | No       | If dynamic payout is false the campaign is deactivated whenever the offer payout is reduced.
countries                       | array     | No       | List of country codes (ISO 3166) for targeting. Index indicates the operation (include/exclude).
regions                         | array     | No       | List of regions for targeting. Index indicates the operation (include/exclude).
cities                          | array     | No       | List of cities for targeting. Index indicates the operation (include/exclude).
devices                         | array     | No       | List of devices for targeting. Index indicates the operation (include/exclude). Check the Related Entities section for a list of possible values.  
operating_systems               | array     | No       | List of operating systems for targeting. Index indicates the operation (include/exclude). Check the Related Entities section for a list of possible values.
versions                        | array     | No       | List of OS versions for targeting.
connection_types                | array     | No       | List of connection types for targeting. Index indicates the operation (include/exclude). Check the Related Entities section for a list of possible values.
carriers                        | array     | No       | List of carriers for targeting. Index indicates the operation (include/exclude). Check the Related Entities section for a list of possible values.
blacklist_subs                  | boolean   | No       | Specifies if blacklist mode should be used for sub_ids. If false, user should whitelist sub_ids. 
sub_ids                         | array     | No       | List of sub_ids.
preview                         | string    | Yes      | The fullsize preview image URL. Hotlinking not allowed.
preview_thumb                   | string    | Yes      | The thumbnail preview image URL. Hotlinking not allowed.
creatives                       | array     | No       | List of available creative files. The file sizes are expressed in KB. Extensions enabled: jpg, jpeg, jpe, gif, png, swf, zip, rar, mp4. Hotlinking not allowed.

####Include/exclude behavior for targeting fields

* If the array key is "include", you should include the values specified. If the array is empty you should include all values.
* If the array key is "exclude", you should exclude the values specified. If the array is empty you should include all values.

### Sample Response

```
{
    "data": [
        {
            "id": 1,
            "name": "Sample Campaign 1",
            "affiliate_id": 16,
            "affiliate_name": "Hoeger Inc",
            "offer_id": 25,
            "offer_name": "Sample Offer 1",
            "description": "Sample description",
            "preview_url": "https://play.google.com/store/apps/details?id=com.makemytrip",
            "tracking_link": "http://ads.cleverlink.xyz/click/?campaign_id=1",
            "impression_url": null,
            "mandatory_url_params": true,
            "mandatory_url_appname": true,
            "mandatory_url_device_id": true,
            "terms_and_conditions": true,
            "additional_terms_and_conditions": "Sample additional terms and conditions.",
            "status": "Inactive",
            "start_hour": 10,
            "end_hour": 18,
            "expiration_date": "2018-02-16",
            "daily_conversions_cap": 556,
            "monthly_conversions_cap": 13913,
            "payout_type": "CPA",
            "payout_value": 0.33,
            "payout_goal": "install",
            "dynamic_payout": true,
            "countries": {
                "include": [
                    "MY",
                    "TK"
                ]
            },
            "regions": {
                "include": [
                    "Malaysia",
                    "Tokelau"
                ]
            },
            "cities": {
                "include": []
            },
            "devices": {
                "include": [
                    "Mobile"
                ]
            },
            "operating_systems": {
                "exclude": [
                    "Android",
                    "Other/Unknown",
                    "Windows"
                ]
            },
            "versions": [
                "15.0.0",
                "15.1.0"
            ],
            "connection_types": {
                "include": [
                    "Corporate",
                    "Dial-up",
                    "Other/Unknown"
                ]
            },
            "carriers": {
                "exclude": [
                    "MTA (US)",
                    "Pelephone (IL)"
                ]
            },
            "blacklist_subs": true,
            "sub_ids": [
                "2_157",
                "4_157"
            ],
            "preview": "https://automizer.cloud/previews/25.jpg",
            "preview_thumb": "https://automizer.cloud/previews/25_t.jpg",
            "creatives": [
                {
                    "url": "https://automizer.cloud/creativities/25/banner.png",
                    "size": 142,
                    "mime_type": "image/png",
                    "width": 678,
                    "height": 565
                },
                {
                    "url": "https://automizer.cloud/creativities/21/Files.zip",
                    "size": 8,
                    "mime_type": "application/zip",
                    "width": 0,
                    "height": 0
                }
            ],
        },
        {
            // Another campaign...
        }
    ]
}
```
