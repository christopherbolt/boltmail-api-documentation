# Get Single Subscriber

Get the details of a single subscriber by Unique Id 

Replace `TIMESTAMP` with timestamp (string  like '1535093670'), `PUBLICKEY` with public key (get it from [API keys tab](https://app.boltmail.nz/customer/api-keys/index) in your panel ) and `{LIST-UNIQUE-ID}` with  List Unique Id of the list and `{SUBSCRIBER-UNIQUE-ID}` with the Unique Id of the subscriber.

### HTTP Method
```
GET
```
### Endpoint
```
https://app.boltmail.nz/api/lists/{LIST-UNIQUE-ID}/subscribers/{SUBSCRIBER-UNIQUE-ID}
```
### Example Response

Response body will be JSON

```json
{
    "status": "success",
    "data": {
        "record": {
            "subscriber_uid": "ft420ys9dl4d4",
            "status": "confirmed",
            "source": "api",
            "ip_address": "127.0.0.1",
            "EMAIL": "john.doe@doe.com",
            "FNAME": "John",
            "LNAME": "Doe"
        }
    }
}
```

