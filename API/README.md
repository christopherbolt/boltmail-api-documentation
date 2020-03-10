## API Reference

Our API interface is used to integrate AvangEmail, The API is designed for developers and is accompanied with a detailed documentation.

The AvangEmail API opens up a world of feasibility for integrating our platform with your favorite CMS, Framework, or other third party software and we constantly working to create Wrapper for common CMS and Frameworks

 

### AvangEmail API (v1.0)

Our REST API service works over the HTTP protocol, Our code examples will be using cURL and PHP SDK. We are constantly working to improve this documentation. If you have questions, please contact the at support@avangemail.com

### Base URL

```
https://avangemail.net/api/
```

#### Acceptable Content Types

We accept these values of `Content-Type` header when using `POST` or `PUT` methods:

- `application/x-www-form-urlencoded` (this one is used as default and it is recommended)

- `multipart/form-data`



### Authentication

AvangEmail API use HTTP Authentication through an API key. Authorization process requires a key signing each further API request. You can choose to generate multiple keys as per your development needs. 

You can get API's from [API keys tab](https://app.avangemail.com/customer/api-keys/index) in your panel.

When you generate a new key, you will get two keys, Public key  & Private key. We considered two methods for authentication. In simple way, it just enough using  Public Key and time  in  HTTP header.For example, if your Public Key is: **dc95f6772bd9c09e12dc88f8683144c665bf0c26**  custom authentication header should look like:

```
X-MW-PUBLIC-KEY: dc95f6772bd9c09e12dc88f8683144c665bf0c26
X-MW-TIMESTAMP: 1535011806
```

In [Postman](https://www.getpostman.com/), you can use {{$timestamp}} for  X-MW-TIMESTAM header.

In secure method you should create signature  with keys. The description of the work is implemented in [PHP SDK](https://avangemail.com/docs/#/API/PHPSDK).

cURL example:

#### cURL request example

```
curl -v GET \
  'https://avangemail.net/api/' \
  -H 'X-MW-PUBLIC-KEY: {replace-it-with-your-public-key}' \
  -H 'X-MW-TIMESTAMP: {replace-it-timestamp}'
```


### HTTP status codes

API response is JSON formatted, AvangEmail uses standard HTTP response codes. 



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

### Reference

#### LIST

| HTTP method | Endpoint                                                     | Function                               |
| ----------- | ------------------------------------------------------------ | -------------------------------------- |
| GET         | [/lists](https://avangemail.com/docs/#/API/LIST/LISTS)       | Returns lists you have in your account |
| GET         | [/lists/{LIST-UNIQUE-ID}](https://avangemail.com/docs/#/API/LIST/SingleList) | Get a single list with unique id       |
| DELETE      | [/lists/{LIST-UNIQUE-ID}](https://avangemail.com/docs/#/API/LIST/DELETE) | Delete a single list with unique id    |
| PUT         | [/lists/{LIST-UNIQUE-ID}](https://avangemail.com/docs/#/API/LIST/UPDATE) | Update a single list with unique id    |
| POST        | /lists/{LIST-UNIQUE-ID}/copy                                 | Copy a single list with unique id      |
| POST        | [/lists](https://avangemail.com/docs/#/API/LIST/CREATE)      | Create a single list                   |
| GET         | [/lists/{LIST-UNIQUE-ID}/fields](https://avangemail.com/docs/#/API/LIST/ListFields) | Get fields list with unique id         |
| GET         | [/lists/{LIST-UNIQUE-ID}/segments](https://avangemail.com/docs/#/API/LIST/ListSegment) | Get segments list with unique id       |



#### SUBSCRIBERS

| HTTP method | Endpoint                                                     | Function                                 |
| ----------- | ------------------------------------------------------------ | :--------------------------------------- |
| GET         | [/lists/{LIST-UNIQUE-ID}/subscribers](https://avangemail.com/docs/#/API/SUBSCRIBER/SUBSCRIBERS) | Returns all subscribers have in the list |
| POST        | [/lists/{LIST-UNIQUE-ID}/subscribers](https://avangemail.com/docs/#/API/SUBSCRIBER/AddSubscriber) | Add a subscriber to the list             |
| PUT         | /lists/{LIST-UNIQUE-ID}/subscribers/{SUBSCRIBER-UNIQUE-ID}/unsubscribe | Unsubscribe a subscriber from the list   |
| PUT         | /lists/{LIST-UNIQUE-ID}/subscribers/{SUBSCRIBER-UNIQUE-ID}   | Update a subscriber from the list        |
| DELETE      | /lists/{LIST-UNIQUE-ID}/subscribers/{SUBSCRIBER-UNIQUE-ID}   | Delete a subscriber from the list        |
| GET         | /lists/{LIST-UNIQUE-ID}/subscribers/{SUBSCRIBER-UNIQUE-ID}   | Get  subscriber detail from the list     |
| GET         | /lists/{LIST-UNIQUE-ID}/subscribers/search-by-email          | Get subscribers by email in the list     |
| GET         | /lists/subscribers/search-by-email-in-all-lists              | Get subscribers by email in all lists    |
| PUT         | /lists/subscribers/unsubscribe-by-email-from-all-lists       | Unsubscribe a subscriber from all lists  |



#### CAMPAIGNS

| HTTP method | Endpoint                                                     | Function                                    |
| ----------- | ------------------------------------------------------------ | ------------------------------------------- |
| GET         | /campaigns/{CAMPAIGN-UNIQUE-ID}                              | Get  campaign detail by the unique id       |
| GET         | /campaigns                                                   | Get all campaigns                           |
| POST        | /campaigns                                                   | Create a new campaign                       |
| PUT         | /campaigns/{CAMPAIGN-UNIQUE-ID}                              | Update campaign by the unique id            |
| POST        | /campaigns/{CAMPAIGN-UNIQUE-ID}                              | Copy campaign by the unique id              |
| DELETE      | /campaigns/{CAMPAIGN-UNIQUE-ID}                              | Delete campaign by the unique id            |
| PUT         | /campaigns/{CAMPAIGN-UNIQUE-ID}/pause-unpause                | Pause - unpause a campaign by the unique id |
| PUT         | /campaigns/{CAMPAIGN-UNIQUE-ID}/mark-sent                    | Mark campaign as sent by the unique id      |
| GET         | /campaigns/{CAMPAIGN-UNIQUE-ID}/bounces                      | Get  campaign bounces by the unique id      |
| POST        | /campaigns/{CAMPAIGN-UNIQUE-ID}/bounces                      | Create campaign bounces by the unique id    |
| GET         | /campaigns/{CAMPAIGN-UNIQUE-ID}/track-opening/{SUBSCRIBER-UNIQUE-ID} | Track subscriber open for campaign          |
| GET         | /campaigns/{CAMPAIGN-UNIQUE-ID}/track-unsubscribe{SUBSCRIBER-UNIQUE-ID} | Track subscriber unsubscribe for campaign   |
| POST        | /campaigns/{CAMPAIGN-UNIQUE-ID}/track-opening/{SUBSCRIBER-UNIQUE-ID} | Track subscriber unsubscribe for campaign   |
| GET         | /campaigns/{CAMPAIGN-UNIQUE-ID}/track-opening/{SUBSCRIBER-UNIQUE-ID} | Track subscriber open for campaign          |





#### TEMPLATE

| HTTP method | Endpoint                        | Function                              |
| ----------- | ------------------------------- | ------------------------------------- |
| GET         | /templates/{TEMPLATE-UNIQUE-ID} | Get  template detail by the unique id |
| GET         | /templates                      | Get all templates                     |
| POST        | /templates                      | Create new template                   |
| PUT         | /templates/{TEMPLATE-UNIQUE-ID} | Update template by the unique id      |
| DELETE      | /templates/{TEMPLATE-UNIQUE-ID} | Delete template by the unique id      |

#### TRANSACTIONAL

| HTTP method | Endpoint                                | Function                                          |
| ----------- | --------------------------------------- | ------------------------------------------------- |
| GET         | /transactional-emails/{EMAIL-UNIQUE-ID} | Get a transactional email detail by the unique id |
| GET         | /transacthional-emails                  | Get all transactional emails                      |
| POST        | /transactional-emails                   | Create a new transactional email                  |
| DELETE      | /transactional-emails/{EMAIL-UNIQUE-ID} | Delete a transactional email by the unique id     |

#### Other

| HTTP method | Endpoint                      | Function               |
| ----------- | ----------------------------- | ---------------------- |
| GET         | /countries/{COUNTRY-ID}/zones | Get country zones      |
| GET         | /countries                    | Get all country        |
| POST        | /customers                    | Create a new customers |

