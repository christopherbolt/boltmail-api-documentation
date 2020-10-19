# Get Subscriber UID By Email

Get the Unique Id of a subscriber by email address. 

This endpoint is intended for finding the Unique Id of a subscriber which is required to perform operations on that subscriber.

Replace `TIMESTAMP` with timestamp (string  like '1535093670'), `PUBLICKEY` with public key (get it from [API keys tab](https://app.boltmail.nz/customer/api-keys/index) in your panel ) and `{LIST-UNIQUE-ID}` with  List Unique Id of the list and `{SUBSCRIBER-EMAIL}` with the Email Address of the subscriber.

### HTTP Method
```
GET
```
### Endpoint
```
https://app.boltmail.nz/api/lists/{LIST-UNIQUE-ID}/subscribers/search-by-email?EMAIL={SUBSCRIBER-EMAIL}
```
### Example Response

Response body will be JSON

```json
{
    "status": "success",
    "data": {
        "subscriber_uid": "lj898ygv9ocb0",
        "status": "confirmed",
        "date_added": "2018-06-29 02:32:11"
    }
}
```

