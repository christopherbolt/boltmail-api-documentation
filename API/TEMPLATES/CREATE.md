# Create Template

Create a new template

Templates can be used when creating/sending a campaign

Replace `TIMESTAMP` with timestamp (string like '1535093670') and `PUBLICKEY` with public key (get it from [API keys tab](https://app.boltmail.nz/customer/api-keys/index) in your panel )

### HTTP method
```
POST
```
### Endpoint
```
https://app.boltmail.nz/api/templates
```
### Request Body Parameters

You should send data as ``x-www-form-urlencoded``. 

The content value must be a base64 encoded string. Content must include an unsubscribe URL, for more information see: https://www.christopherbolt.com/support/knowledgebase/36/How-to-add-an-unsubscribe-link.html

Content can include merge tags, for more information see: https://www.christopherbolt.com/support/knowledgebase/42/Campaign-tags-and-filters.html

Example data structure, this should be serialized into x-www-form-urlencoded format:

```
{
    "template": {
        "name": "My API Template", // required
        "content": "SGVsbG8gV29ybGQhW1VOU1VCU0NSSUJFX1VSTF0", // required. Base 64 encoded string of your HTML email content
        "inline_css": "no"
    },
}
```

### Example Response

The API will respond with the Unique Id for the template which you will need when performing further API calls for this template.

```json
{
    "status": "success",
    "template_uid": "tk015bgvj9e8e"
}
```