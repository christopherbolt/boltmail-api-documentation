# Create Campaign

Create *and send* a new campaign

Replace `TIMESTAMP` with timestamp (string like '1535093670'), `PUBLICKEY` with public key (get it from [API keys tab](https://app.boltmail.nz/customer/api-keys/index) in your panel ), `{LIST-UNIQUE-ID}` with the Unique Id of the list and `{TEMPALTE-UNIQUE-ID}` with Unique Id of the template.

### HTTP method
```
POST
```
### Endpoint
```
https://app.boltmail.nz/api/campaigns
```
### Request Body Parameters

You should send data as ``x-www-form-urlencoded``. 

If creating a regular campaign then the "send_at" value sets the date and time that the campaign will be sent. Setting this to the current time will start the send immediatly.

Autoresponders are triggered by events, the event and time delay can be set in the autoresponder_event, autoresponder_time_unit and autoresponder_time_value fields.

A campaign can send a template by specifying the template_uid value or you can specify the content directly in the content value. If setting the content value this must be a base64 encoded string. Content must include an unsubscribe URL, for more information see: https://www.christopherbolt.com/support/knowledgebase/36/How-to-add-an-unsubscribe-link.html

The campaign subject, to_name and content can include merge tags, for more information see: https://www.christopherbolt.com/support/knowledgebase/42/Campaign-tags-and-filters.html

Example data structure, this should be serialized into x-www-form-urlencoded format:

```
{
    "campaign": {
        "name": "My API Campaign", // required
        "type": "regular", // optional: regular or autoresponder, regular is default
        "from_name": "John Doe", // required
        "from_email": "john.doe@doe.com", // required
        "subject": "Hey, i am testing the campaigns via API", // required, can include merge tags
        "to_name": "[FNAME] [LNAME]", // optional, can include merge tags
        "reply_to": "john.doe@doe.com", // required
        "send_at": "2020-10-28 09:00:00", // required if regular campaign, this sets when the campaign will start sending
        "list_uid": "{LIST-UNIQUE-ID}", // required
        "segment_uid": "{SEGMENT-UNIQUE-ID}" // optional, only to narrow down
    },
    {
        // optional block, defaults are shown
        "options" => array(
            "url_tracking": "no", // yes | no
            "json_feed": "no", // yes | no
            "xml_feed": "no", // yes | no
            "plain_text_email": "yes",// yes | no
            "email_stats": null, // a valid email address where we should send the stats after campaign done

            // - if autoresponder uncomment bellow:
            //"autoresponder_event": "AFTER-SUBSCRIBE", // AFTER-SUBSCRIBE or AFTER-CAMPAIGN-OPEN
            //"autoresponder_time_unit": "hour", // minute, hour, day, week, month, year
            //"autoresponder_time_value": 1, // 1 hour after event
            //"autoresponder_open_campaign_id": 1, // INT id of campaign, only if event is AFTER-CAMPAIGN-OPEN,

            // - if a regular campaign and is to be sent on a recurring schedule, you can set a cron job style frequency.
            // - please note that this applies only for regular campaigns.
            // - omit these paramaters if not using
            "cronjob": "0 0 * * *", // once a day
            "cronjob_enabled": 1 // 1 or 0
        ),
        // required block, template_uid or content is required.
        "template" => array(
            "template_uid": "{TEMPLATE-UNIQUE-ID}", // UID of the template you want to send
            "content": // HTML template content to send if not using a template, can include merge tags. This must be base64 encoded
            "inline_css": "no", // yes | no
            "plain_text": null, // leave empty to auto generate
            "auto_plain_text": "yes" // yes | no
        }
    }
}
```

### Example Response

Response body will be JSON

The API will respond with the Unique Id for the campaign which you will need when performing further API calls for this campaign.

```json
{
    "status": "success",
    "campaign_uid": "tk015bgvj9e8e"
}
```