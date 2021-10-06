**TEMPORARILY UNAVAILABLE**

### Usage

Poll this endpoint to obtain the available offers you can use to request a new campaign.

### URI / Method

* Endpoint: `https://automizer.cloud/api/campaignrequests/available_offers` (Method: `GET`)

### Response fields

Field                           | Data Type | Nullable | Notes
------------------------------- | --------- | -------- | --------------------------------------------------------------
id                              | integer   | No       | The offer ID.
name                            | string    | No       | The offer name.
description                     | text      | Yes      | Description text.
preview_url                     | string    | Yes      | Preview url (playstore, appstore or image hosting).
impression_url                  | string    | Yes      | Impression url.
start_hour                      | integer   | Yes      | The traffic start hour. 
end_hour                        | integer   | Yes      | The traffic end hour.
payout_type                     | string    | No       | The payout type. Check the Related Entities section for a list of possible values.
payout_value                    | float     | No       | The payout value. If null, value is N/A.
payout_goal                     | string    | Yes      | The payout goal.
mandatory_url_params            | boolean   | No       | If the offer has mandatory URL parameters.
terms_and_conditions            | boolean   | No       | If the offer has terms and conditions.
additional_terms_and_conditions | text      | Yes      | The terms and conditions text.
countries                       | array     | No       | List of country codes (ISO 3166) for targeting. Index indicates the operation (include/exclude).
regions                         | array     | No       | List of regions for targeting. Index indicates the operation (include/exclude).
cities                          | array     | No       | List of cities for targeting. Index indicates the operation (include/exclude).
devices                         | array     | No       | List of devices for targeting. Index indicates the operation (include/exclude). Check the Related Entities section for a list of possible values.  
operating_systems               | array     | No       | List of operating systems for targeting. Index indicates the operation (include/exclude). Check the Related Entities section for a list of possible values.
versions                        | array     | No       | List of OS versions for targeting.
connection_types                | array     | No       | List of connection types for targeting. Index indicates the operation (include/exclude). Check the Related Entities section for a list of possible values.
carriers                        | array     | No       | List of carriers for targeting. Index indicates the operation (include/exclude). Check the Related Entities section for a list of possible values.
preview                         | string    | Yes      | The fullsize preview image URL. Hotlinking not allowed.
preview_thumb                   | string    | Yes      | The thumbnail preview image URL. Hotlinking not allowed.
status                          | string    | No       | The offer status. Posible values: Available, Pending, Denied. Pending indicates you have already requested a campaign and the request is being evaluated. Denied means you have already requested a campaign and the request was not approved. 

### Sample Response

```
{
    "data": [
        {
            "id": 20,
            "name": "Sample Offer 20",
            "description": "Sample description.",
            "preview_url": "https://play.google.com/store/apps/details?id=com.makemytrip",
            "impression_url": null,
            "start_hour": null,
            "end_hour": null,
            "payout_type": "CPC",
            "payout_value": 0.001,
            "payout_goal": null,
            "mandatory_url_params": false,
            "terms_and_conditions": true,
            "additional_terms_and_conditions": "Sample terms and conditions text.",
            "countries": {
                "include": [
                    "PS",
                    "RO"
                ]
            },
            "regions": {
                "include": [
                    "Gaza",
                    "Ilfov"
                ]
            },
            "cities": {
                "include": [
                    "Caciulati",
                    "Dragomiresti-Deal"
                ]
            },
            "devices": {
                "exclude": [
                    "Mobile"
                ]
            },
            "operating_systems": {
                "include": [
                    "Mac OS",
                    "Other/Unknown",
                    "Windows"
                ]
            },
            "versions": [
                "10.13.5",
                "2000.0.0"
            ],
            "connection_types": {
                "include": [
                    "Wi-Fi"
                ]
            },
            "carriers": {
                "exclude": [
                    "Orange (FR)"
                ]
            },
            "preview": "https://automizer.cloud/previews/20.gif",
            "preview_thumb": "https://automizer.cloud/previews/20.gif",
            "status": "Available"
        },
        // Another offer...
    ]
}
```
