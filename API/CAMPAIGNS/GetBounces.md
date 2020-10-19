# Get Bounces

Get a list of all bounces for a campaign 

Replace `TIMESTAMP` with timestamp (string like '1535093670'), `PUBLICKEY` with public key (get it from [API keys tab](https://app.boltmail.nz/customer/api-keys/index) in your panel ) and `{CAMPAIGN-UNIQUE-ID}` with Campaign Unique Id.

### HTTP Method
```
GET
```
### Endpoint
```
https://app.boltmail.nz/api/campaigns/{CAMPAIGN-UNIQUE-ID}/bounces
```
### Example Response

Response body will be JSON

For each bounce the bounce_type and the response message from the server will be included if available.

A bounce type of 'soft' indicates a temporary error such as an account over quota.
A bounce type of 'internal' are temporary server errors such as email rejected as spam or server temporarily unavailable.
A bounce type of 'hard' indicates a permanent error such as an email address that does not exist. BoltMail will automatically clean hard bounces from your subscriber list.

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
                "message": " smtp;452 4.2.2 The email account that you tried to reach is over quota. Please direct the recipient to https://support.google.com/mail/?p=OverQuotaTemp 20si6368866pfw.99 - gsmtp",
                "bounce_type": "soft",
                "subscriber": {
                    "subscriber_uid": "bx760tddsle3d",
                    "email": "john.doe@doe.com"
                }
            },
            {
                "message": "Internal Bounce",
                "bounce_type": "internal",
                "subscriber": {
                    "subscriber_uid": "ea916k5a3n43c",
                    "email": "john.smoth@smith.com"
                }
            }
        ]
    }
}

```