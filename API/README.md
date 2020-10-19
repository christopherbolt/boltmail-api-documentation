# API Reference

## Introduction

Our API interface is used to integrate BoltMail, The API is designed for developers and is accompanied with a detailed documentation.

The BoltMail API opens up a world of feasibility for integrating our platform with your favorite CMS, Framework, or other third party software and we constantly working to create Wrapper for common CMS and Frameworks

Our REST API service works over the HTTP protocol, Our code examples will be using cURL and PHP SDK. We are constantly working to improve this documentation. If you have questions, please contact the at support@boltmail.nz

## Base URL

```
https://app.boltmail.nz/api/
```

## Acceptable Content Types

For `POST` or `PUT` methods data must be sent as `application/x-www-form-urlencoded` and a `Content-Type` header of `application/x-www-form-urlencoded` should be included.

`application/json` is not supported.


## Authentication

BoltMail API uses HTTP Authentication through an API key. 

You can choose to generate multiple keys as per your development needs. 

You can generate API key's from [API keys tab](https://app.boltmail.nz/customer/api-keys/index) in your BoltMail panel. 

We recommend setting an IP address whitelist for each key, this will restrict access to only the IP addresses listed.

To authenticate you will need to send a minimum of two custom authentication headers:

X-MW-PUBLIC-KEY: your public key

X-MW-TIMESTAMP: your current timestamp

For example, if your Public Key is: **dc95f6772bd9c09e12dc88f8683144c665bf0c26** authentication header should look like:

```
X-MW-PUBLIC-KEY: dc95f6772bd9c09e12dc88f8683144c665bf0c26
X-MW-TIMESTAMP: 1535011806
```

In [Postman](https://www.getpostman.com/), you can use {{$timestamp}} for  X-MW-TIMESTAMP header.

<!--In secure method you should create signature  with keys. The description of the work is implemented in [PHP SDK](https://developer.boltmail.nz/#/API/PHPSDK).-->

cURL example:

### cURL request example

```shell
curl -v GET \
  'https://app.boltmail.nz/api/' \
  -H 'X-MW-PUBLIC-KEY: {replace-it-with-your-public-key}' \
  -H 'X-MW-TIMESTAMP: {replace-it-timestamp}'
```


## Response

API response is always JSON formatted. The response object will always include a "status" attribute at the top level with a value of "success" for a successful request or "error" for a failed request.

### Successful response

A successful response will include an attribute of "status" with a value of "success". 

If the response includes data this will be contained within an object named "data". 

#### Single record response

If the data contains a single record then this will be contained inside a sub-object named "record"

Example of a single record response:

```json
{
    "status": "success",
    "data": {
        "record": {
            "subscriber_uid": "zz828zm50m3fb",
            "status": "unconfirmed",
            "source": "api",
            "ip_address": "127.0.0.1",
            "EMAIL": "john.doe@doe.com",
            "FNAME": "John",
            "LNAME": "Doe",
        }
    }
}
```

#### Multiple record response

If the data contains multiple records then these will be contained inside a sub-object named "records".

Endpoints that return a large number of records, such as the subscribers endpoint, will be paged. If this is the case there will be additional paramaters named "count", "total_pages" and "current_page".

You can move between pages by added a page query paramater to the endpoint. e.g. `?page=4`. You can also specify the length of a page using the page_length parameter, e.g. `?page=4&page_length=100`. Note that a large page_length may result in poor performance.

Example of a multiple record response with paging:

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
                "subscriber_uid": "sm8665teg9aa9",
                "EMAIL": "john.doe@doe.com",
                "APITEST": "",
                "FNAME": "John",
                "LNAME": "Doe",
                "status": "confirmed",
                "source": "import",
                "ip_address": null,
                "date_added": "2019-06-11 20:50:48"
            },
            {
                "subscriber_uid": "3hf82237hfew",
                "EMAIL": "john.smith@smith.com",
                "APITEST": "",
                "FNAME": "John",
                "LNAME": "Smith",
                "status": "confirmed",
                "source": "import",
                "ip_address": null,
                "date_added": "2019-06-11 20:50:48"
            },
        ]
    }
}
```

### Unsuccessful response

A failed response will include an attribute of "status" with a value of "error". It will also include an attribute of "error" containing explanations as to why the request failed. If there are multiple errors then this value may be a list.

Example failed response with a single error:

```json
{
    "status": "error",
    "error": "The subscriber already exists in this list."
}
```

Example failed response with multiple errors:

```json
{
    "status": "error",
    "error": {
        "name": "Campaign name cannot be blank.",
        "from_name": "From name cannot be blank.",
        "from_email": "From email cannot be blank.",
        "subject": "Subject cannot be blank.",
        "reply_to": "Reply to cannot be blank."
    }
}
```

### HTTP Response codes

BoltMail uses standard HTTP response codes.

| http status codes | Description                                               |
| ----------------- | --------------------------------------------------------- |
| 100               | Continue                                                  |
| 101               | Switching Protocols                                       |
| 102               | Processing                                                |
| 200               | OK                                                        |
| 201               | Created                                                   |
| 202               | Accepted                                                  |
| 203               | Non-Authoritative Info                                    |
| 204               | No Content                                                |
| 205               | Reset Content                                             |
| 206               | Partial Content                                           |
| 207               | Multi-Status                                              |
| 208               | Already Reported                                          |
| 226               | IM Used                                                   |
| 300               | Multiple Choices                                          |
| 301               | Moved Permanently                                         |
| 302               | Found                                                     |
| 303               | See Other                                                 |
| 304               | Not Modified                                              |
| 305               | Use Proxy                                                 |
| 306               | Reserved                                                  |
| 307               | Temporary Redirect                                        |
| 308               | Permanent Redirect                                        |
| 400               | Bad Request                                               |
| 401               | Unauthorized                                              |
| 402               | Payment Required                                          |
| 403               | Forbidden                                                 |
| 404               | Not Found                                                 |
| 405               | Method Not Allowed                                        |
| 406               | Not Acceptable                                            |
| 407               | Proxy Authentication R                                    |
| 408               | Request Timeout                                           |
| 409               | Conflict                                                  |
| 410               | Gone                                                      |
| 411               | Length Required                                           |
| 412               | Precondition Failed                                       |
| 413               | 'Request Entity Too Lar                                   |
| 414               | Request-URI Too Long                                      |
| 415               | Unsupported Media Type                                    |
| 416               | Requested Range Not Satisfiable                           |
| 417               | Expectation Failed                                        |
| 418               | I\'m a teapot                                             |
| 422               | Unprocessable Entity                                      |
| 423               | Locked                                                    |
| 424               | Failed Dependency                                         |
| 425               | Reserved for WebDAV advanced collections expired proposal |
| 426               | Upgrade Required                                          |
| 428               | Precondition Required                                     |
| 429               | Too Many Requests                                         |
| 431               | Request Header Fields Too Large                           |
| 500               | Internal Server Error                                     |
| 501               | Not Implemented                                           |
| 502               | Bad Gateway                                               |
| 503               | Service Unavailable                                       |
| 504               | Gateway Timeout                                           |
| 505               | HTTP Version Not Supported                                |
| 506               | Variant Also Negotiates (Experimental)                    |
| 507               | Insufficient Storage                                      |
| 508               | Loop Detected                                             |
| 510               | Not Extended                                              |
| 511               | Network Authentication Required                           |

## Endpoint Reference

### LISTS

| HTTP method | Endpoint                                                     | Function                               |
| ----------- | ------------------------------------------------------------ | -------------------------------------- |
| GET         | [/lists](API/LISTS/LISTS)       | Returns all lists you have in your account |
| GET         | [/lists/{LIST-UNIQUE-ID}](API/LISTS/SingleList) | Get a single list with unique id       |
| POST        | [/lists](API/LISTS/CREATE)      | Create a single list                   |
| PUT         | [/lists/{LIST-UNIQUE-ID}](API/LISTS/UPDATE) | Update a single list with unique id    |
| POST        | /lists/{LIST-UNIQUE-ID}/copy                                 | Copy a list with unique id      |
| DELETE      | [/lists/{LIST-UNIQUE-ID}](API/LISTS/DELETE) | Delete a single list with unique id    |
| GET         | [/lists/{LIST-UNIQUE-ID}/segments](API/LISTS/ListSegments) | Get segments list with unique id       |


### FIELDS

| HTTP method | Endpoint                                                     | Function                               |
| ----------- | ------------------------------------------------------------ | -------------------------------------- |
| GET         | [/lists/{LIST-UNIQUE-ID}/fields](API/FIELDS/FIELDS) | Get all fields for list        |
| GET         | [/lists/{LIST-UNIQUE-ID}/fields/{FIELD-TAG}](API/FIELDS/SingleField) | Get details of a single field         |
| POST         | [/lists/{LIST-UNIQUE-ID}/fields](API/FIELDS/CREATE) | Create a new field         |
| PUT         | [/lists/{LIST-UNIQUE-ID}/fields/{FIELD-TAG}](API/FIELDS/UPDATE) | Update a single field         |
| DELETE         | [/lists/{LIST-UNIQUE-ID}/fields/{FIELD-TAG}](API/FIELDS/DELETE) | Delete a single field         |



### SUBSCRIBERS

| HTTP method | Endpoint                                                     | Function                                 |
| ----------- | ------------------------------------------------------------ | ---------------------------------------- |
| GET         | [/lists/{LIST-UNIQUE-ID}/subscribers](API/SUBSCRIBERS/SUBSCRIBERS) | Returns all subscribers in the list optionally filtered by status |
| GET         | [/lists/{LIST-UNIQUE-ID}/subscribers/{SUBSCRIBER-UNIQUE-ID}](API/SUBSCRIBERS/SingleSubscriber)   | Get a single subscriber's details from the list     |
| POST        | [/lists/{LIST-UNIQUE-ID}/subscribers](API/SUBSCRIBERS/CREATE) | Add a subscriber to the list             |
| POST        | [/lists/{LIST-UNIQUE-ID}/subscribers/bulk](API/SUBSCRIBERS/BULK)                      | Bulk add up to 10,000 subscribers to the list |
| PUT         | /lists/{LIST-UNIQUE-ID}/subscribers/{SUBSCRIBER-UNIQUE-ID}/unsubscribe | Unsubscribe a subscriber from the list   |
| PUT         | [/lists/{LIST-UNIQUE-ID}/subscribers/{SUBSCRIBER-UNIQUE-ID}](API/SUBSCRIBERS/UPDATE)   | Update a subscriber from the list        |
| DELETE      | [/lists/{LIST-UNIQUE-ID}/subscribers/{SUBSCRIBER-UNIQUE-ID}](API/SUBSCRIBERS/DELETE)   | Delete a subscriber from the list        |
| GET         | [/lists/{LIST-UNIQUE-ID}/subscribers/search-by-email?EMAIL={SUBSCRIBER-EMAIL}](API/SUBSCRIBERS/SingleSubscriberByEmail)          | Get the Unique Id of a subscriber by email    |
| GET         | /lists/subscribers/search-by-email-in-all-lists              | Get subscribers by email in all lists    |
| PUT         | /lists/subscribers/unsubscribe-by-email-from-all-lists       | Unsubscribe a subscriber from all lists  |



### CAMPAIGNS

| HTTP method | Endpoint                                                     | Function                                    |
| ----------- | ------------------------------------------------------------ | ------------------------------------------- |
| GET         | [/campaigns](API/CAMPAIGNS/CAMPAIGNS)                                                   | Get all campaigns                           |
| GET         | [/campaigns/{CAMPAIGN-UNIQUE-ID}](API/CAMPAIGNS/SingleCampaign)                             | Get  campaign detail by the unique id       |
| POST        | [/campaigns](API/CAMPAIGNS/CREATE)                                                  | Create a new campaign                       |
| PUT         | [/campaigns/{CAMPAIGN-UNIQUE-ID}](API/CAMPAIGNS/UPDATE)                              | Update campaign by the unique id            |
| POST        | /campaigns/{CAMPAIGN-UNIQUE-ID}/copy                              | Copy campaign by the unique id              |
| DELETE      | [/campaigns/{CAMPAIGN-UNIQUE-ID}](API/CAMPAIGNS/DELETE)                              | Delete campaign by the unique id            |
| PUT         | /campaigns/{CAMPAIGN-UNIQUE-ID}/pause-unpause                | Pause - unpause a campaign by the unique id |
| PUT         | /campaigns/{CAMPAIGN-UNIQUE-ID}/mark-sent                    | Mark campaign as sent by the unique id      |
| GET         | [/campaigns/{CAMPAIGN-UNIQUE-ID}/bounces](API/CAMPAIGNS/GetBounces)                    | Get  campaign bounces by the unique id      |
| POST        | /campaigns/{CAMPAIGN-UNIQUE-ID}/bounces                      | Record campaign bounces by the unique id    |
| GET         | /campaigns/{CAMPAIGN-UNIQUE-ID}/track-opening/{SUBSCRIBER-UNIQUE-ID} | Record subscriber as opened campaign |
| POST        | /campaigns/{CAMPAIGN-UNIQUE-ID}/track-unsubscribe/{SUBSCRIBER-UNIQUE-ID} | Unsubscribe subscriber for campaign |





### TEMPLATE

| HTTP method | Endpoint                        | Function                              |
| ----------- | ------------------------------- | ------------------------------------- |
| GET         | [/templates](API/TEMPLATES/TEMPLATES)                       | Get all templates                     |
| GET         | [/templates/{TEMPLATE-UNIQUE-ID}](API/TEMPLATES/SingleTemplate)   | Get  template detail by the unique id |
| POST        | [/templates](API/TEMPLATES/CREATE)                      | Create new template                   |
| PUT         | [/templates/{TEMPLATE-UNIQUE-ID}](API/TEMPLATES/UPDATE) | Update template by the unique id      |
| DELETE      | [/templates/{TEMPLATE-UNIQUE-ID}](API/TEMPLATES/DELETE) | Delete template by the unique id      |

### TRANSACTIONAL

| HTTP method | Endpoint                                | Function                                          |
| ----------- | --------------------------------------- | ------------------------------------------------- |
| GET         | /transactional-emails/{EMAIL-UNIQUE-ID} | Get a transactional email detail by the unique id |
| GET         | /transactional-emails                  | Get all transactional emails                      |
| POST        | /transactional-emails                   | Create a new transactional email                  |
| DELETE      | /transactional-emails/{EMAIL-UNIQUE-ID} | Delete a transactional email by the unique id     |



