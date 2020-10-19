# Get All Templates

Returns all templates in your account

Replace `TIMESTAMP` with timestamp (string  like '1535093670'), `PUBLICKEY` with public key (get it from [API keys tab](https://app.boltmail.nz/customer/api-keys/index) in your panel )

### HTTP Method
```
GET
```
### Endpoint
```
https://app.boltmail.nz/api/templates
```
### Example Response

This endpoint does not include the HTML content for each template. To get the content of a template query the [endpoint for that specific template](API/TEMPLATES/SingleTemplate.md)

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
                "template_uid": "qo447z3fgc18a",
                "name": "My API Template",
                "screenshot": null
            },
            {
                "template_uid": "bt880gbac013c",
                "name": "My Test Template",
                "screenshot": null
            }
        ]
    }
}
```