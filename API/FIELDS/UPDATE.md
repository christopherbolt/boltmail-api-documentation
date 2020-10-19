# Update Field

Update a list field

Replace `TIMESTAMP` with timestamp (string  like '1535093670'), `PUBLICKEY` with public key (get it from [API keys tab](https://app.boltmail.nz/customer/api-keys/index) in your panel ), `{LIST-UNIQUE-ID}` with List Unique Id of the list and `{FIELD-TAG}` with the merge tag of the field.

### HTTP method
```
PUT
```
### Endpoint
```
https://app.boltmail.nz/api/lists/{LIST-UNIQUE-ID}/fields/{FIELD-TAG}
```
### Request Body Parameters

You should send data as ``x-www-form-urlencoded``. 

Example data structure, this should be serialized into x-www-form-urlencoded format: 

```
{
  "field": {
    "tag": "MY_MERGE_TAG", // required
    "label": "Human readable label." // required
    "required": "no" // Or 'yes', if yes then this field must be completed when adding a subscriber
  }
}
```

