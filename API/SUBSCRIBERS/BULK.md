# Bulk Add Subscribers

Bulk add up to 10,000 subscribers to a list in a single API call

Replace `TIMESTAMP` with timestamp (string  like '1535093670'), `PUBLICKEY` with public key (get it from [API keys tab](https://app.boltmail.nz/customer/api-keys/index) in your panel ) and `{LIST-UNIQUE-ID}` with  List Unique Id of the list

### HTTP Method
```
POST
```
### Endpoint
```
https://app.boltmail.nz/api/lists/{LIST-UNIQUE-ID}/subscribers/bulk
```
### Request Body Parameters

Note, you should send data with `x-www-form-urlencoded`

Example data structure, this should be serialized into x-www-form-urlencoded format. Each key is the TAG for a custom list field, the fields available on a list will vary. The EMAIL field is required.

```
{
    "subscribers": [
        {
            "EMAIL": "john.doe@doe.com",
            "FNAME": "John",
            "LNAME": "Doe"
        },
        {
            "EMAIL": "john.smith@smithcom",
            "FNAME": "John",
            "LNAME": "Smith"
        }
    ]
}
```

Example serialization of the above into `x-www-form-urlencoded`:

```
subscribers[0][EMAIL]=john.doe%40doe.com&subscribers[0][FNAME]=John&subscribers[0][LNAME]=Doe&subscribers[1][EMAIL]=john.smith%40smith.com&subscribers[1][FNAME]=John&subscribers[1][LNAME]=Smith
```

### Example Response

The API will respond with the data record for each new subscriber. This will include the subscriber's Unique Id, you will need this to perform further actions against the subscriber.
If a subscriber failed an errors list will be included for that subscriber. If no errors list is included then it can be assumed that the subscriber was created successfully.

```json
{
    "status": "success",
    "data": {
        "records": [
            {
                "data": {
                    "subscriber_uid": "ps9129raz7401",
                    "EMAIL": "john.doe@doe.com",
                    "FNAME": "John",
                    "LNAME": "Doe",
                }
            },
            {
                "data": {
                    "EMAIL": "john.smith@smithcom",
                    "FNAME": "John",
                    "LNAME": "Smith"
                },
                "errors": {
                    "EMAIL": "Please provide a valid email address."
                }
            }
        ]
    }
}
```