# Get Single Template

Get the details for a single template

Replace `TIMESTAMP` with timestamp (string  like '1535093670'), `PUBLICKEY` with public key (get it from [API keys tab](https://app.boltmail.nz/customer/api-keys/index) in your panel ) and `{TEMPLATE-UNIQUE-ID}` with the Template Unique Id

### HTTP Method
```
GET
```
### Endpoint
```
https://app.boltmail.nz/api/templates/{TEMPLATE-UNIQUE-ID}
```
### Example Response

```json
{
    "status": "success",
    "data": {
        "record": {
            "name": "My API Template",
            "content": "Hello World!<br>[UNSUBSCRIBE_URL]",
            "screenshot": null
        }
    }
}
```