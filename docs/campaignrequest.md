### Usage

Poll this endpoint to request the creation of new campaign based on an available offer.

### URI / Method

* Endpoint: `https://arbolith.com/api/campaignrequests/from_offer/ID` (Method: `POST`)

### Notes

If your request a campaign from an offer you have already requested in the past (status Pending/Denied), the request will be silently ignored (success message). 

### Sample Response

```
{
    "status": "success"
}
```
