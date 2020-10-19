# Get Single Campaign

Get the details for a single campaign

Replace `TIMESTAMP` with timestamp (string  like '1535093670'), `PUBLICKEY` with public key (get it from [API keys tab](https://app.boltmail.nz/customer/api-keys/index) in your panel ) and `{CAMPAIGN-UNIQUE-ID}` with the Campaign Unique Id.

### HTTP Method
```
GET
```
### Endpoint
```
https://app.boltmail.nz/api/campaigns/{CAMPAIGN-UNIQUE-ID}
```
### Example Response

Response body will be JSON

The status attribute for the data record indicates if the campaign has finished sending

```json
{
    "status": "success",
    "data": {
        "record": {
            "campaign_uid": "ff153x0rfg59e",
            "name": "Test Campaign",
            "type": "regular",
            "from_name": "Test List Owner",
            "from_email": "john.doe@doe.com",
            "to_name": "[FNAME] [LNAME]",
            "reply_to": "john.doe@doe.com",
            "subject": "Test Subject",
            "status": "sent",
            "date_added": "27/07/20, 11:34 PM",
            "send_at": "27/07/20, 11:34 PM",
            "list": {
                "list_uid": "po613voejz0f7",
                "name": "Test List",
                "subscribers_count": 345
            },
            "segment": [],
            "group": []
        }
    }
}
```