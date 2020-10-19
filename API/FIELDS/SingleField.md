# Get Single Field

Get details of a single field

Replace `TIMESTAMP` with timestamp (string like '1535093670'), `PUBLICKEY` with public key (get it from [API keys tab](https://app.boltmail.nz/customer/api-keys/index) in your panel ), `{LIST-UNIQUE-ID}` with List Unique Id of the list and `{FIELD-TAG}` with the merge tag of the field.

### HTTP Method
```
GET
```
### Endpoint
```
https://app.boltmail.nz/api/lists/{LIST-UNIQUE-ID}/fields/{FIELD-TAG}
```
### Example Response

Response body will be JSON

```json
{
    "status": "success",
    "data": {
        "record": {
            "tag": "FNAME",
            "label": "First name",
            "required": "no",
            "help_text": null,
            "type": {
                "name": "Text",
                "identifier": "text",
                "description": "Text"
            }
        }
    }
}
```