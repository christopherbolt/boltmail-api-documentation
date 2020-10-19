# Get All Campaigns

Returns all campaigns in your account

Replace `TIMESTAMP` with timestamp (string  like '1535093670'), `PUBLICKEY` with public key (get it from [API keys tab](https://app.boltmail.nz/customer/api-keys/index) in your panel )

### HTTP Method
```
GET
```
### Endpoint
```
https://app.boltmail.nz/api/campaigns
```
### Example Response

Response body will be JSON

The status attribute for each record indicates if the campaign has finished sending

```json
{
    "status": "success",
    "data": {
        "count": "2",
        "total_pages": 1,
        "current_page": 1,
        "next_page": null,
        "prev_page": null,
        "records": [
            {
                "campaign_uid": "nk597jwrr5d84",
                "name": "Test Campaign 1",
                "status": "sent",
                "group": []
            },
            {
                "campaign_uid": "ay4615anmb2aa",
                "name": "Test Campaign 2",
                "status": "draft",
                "group": []
            }
        ]
    }
}
```