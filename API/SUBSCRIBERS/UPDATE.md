# Update Subscriber

Update a subscriber's details

Replace `TIMESTAMP` with timestamp (string  like '1535093670'), `PUBLICKEY` with public key (get it from [API keys tab](https://app.boltmail.nz/customer/api-keys/index) in your panel ), `{LIST-UNIQUE-ID}` with List Unique Id of the list and `{SUBSCRIBER-UNIQUE-ID}` with the Unique Id of the subscriber.

### HTTP method
```
PUT
```
### Endpoint
```
https://app.boltmail.nz/api/lists/{LIST-UNIQUE-ID}/subscribers/{SUBSCRIBER-UNIQUE-ID}
```
If you do not know the Unqiue Id of your subscriber you should first query the [Get Subscriber UID By Email](API/SUBSCRIBERS/SingleSubscriberByEmail.md) endpoint

### Request Body Parameters

You should send data as ``x-www-form-urlencoded``. 

Each parameter should be the TAG for a custom list field, the fields available on a list will vary. The EMAIL field is required. See the FIELDS endpoints for managing the fields available on a list.

Example data structure, this should be serialized into x-www-form-urlencoded format: 

```
{
  "EMAIL": "john.doe@doe.com",
  "FNAME": "John",
  "LNAME": "Doe",
}
```

