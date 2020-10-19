# Create Field

Create a new field for a list

Replace `TIMESTAMP` with timestamp (string  like '1535093670'), `PUBLICKEY` with public key (get it from [API keys tab](https://app.boltmail.nz/customer/api-keys/index) in your panel ) and `{LIST-UNIQUE-ID}` with the List Unique Id.

### HTTP method
```
POST
```
### Endpoint
```
https://app.boltmail.nz/api/lists/{LIST-UNIQUE-ID}
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

