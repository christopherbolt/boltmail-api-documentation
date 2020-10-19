# Update Template

Update a template

Templates can be used when creating/sending a campaign

Replace `TIMESTAMP` with timestamp (string like '1535093670'), `PUBLICKEY` with public key (get it from [API keys tab](https://app.boltmail.nz/customer/api-keys/index) in your panel ) and {TEMPLATE-UNIQUE-ID} with the template Unique Id.

### HTTP method
```
PUT
```
### Endpoint
```
https://app.boltmail.nz/api/templates/{TEMPLATE-UNIQUE-ID}
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
