# Get All Subscribers

Get the subscribers from a list optionally filtered by status

Replace `TIMESTAMP` with timestamp (string  like '1535093670'), `PUBLICKEY` with public key (get it from [API keys tab](https://app.boltmail.nz/customer/api-keys/index) in your panel ) and `{LIST-UNIQUE-ID}` with  List Unique Id of the list.

### HTTP Method
```
GET
```
### Endpoint
```
https://app.boltmail.nz/api/lists/{LIST-UNIQUE-ID}/subscribers
```
The results will be paged, you can add `page` and `per_page` query parameters to the endpoint to control the paging. eg. ``?page=1&per_page=9999``

You can also filter results by status by adding a `status` parameter to the endpoint. eg. ``?status=unsubscribed``. Valid values are `unsubscribed`, `confirmed` and `unconfirmed`

### Example Response

Response body will be JSON

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

## Code Examples

### cURL

```shell
curl -X GET \
  'https://app.boltmail.nz/api/lists/{LIST-UNIQUE-ID}/subscribers?page=1&per_page=9999' \
  -H 'X-MW-PUBLIC-KEY: PUBLICKEY' \
  -H 'X-MW-TIMESTAMP: TIMESTAMP'
```

### C# (RestSharp)

```csharp
var client = new estClient("https://app.boltmail.nz/api/lists/{LIST-UNIQUE-ID}/subscribers?page=1&per_page=9999");
var request = new RestRequest(Method.GET);
request.AddHeader("X-MW-TIMESTAMP", "TIMESTAMP");
request.AddHeader("X-MW-PUBLIC-KEY", "PUBLICKEY");
IRestResponse response = client.Execute(request);
```

### PHP (with sdk)

[SDK Docs](https://developer.boltmail.nz/#/API/PHPSDK)

```php
$response = $endpoint->getSubscribers('{LIST-UNIQUE-ID}', $pageNumber = 1, $perPage = 10);
```

### PHP (curl)

```php
<?php

$curl = curl_init();

curl_setopt_array($curl, array(
  CURLOPT_URL => "https://app.boltmail.nz/api/lists/{LIST-UNIQUE-ID}/subscribers?page=1&per_page=9999",
  CURLOPT_RETURNTRANSFER => true,
  CURLOPT_ENCODING => "",
  CURLOPT_MAXREDIRS => 10,
  CURLOPT_TIMEOUT => 30,
  CURLOPT_HTTP_VERSION => CURL_HTTP_VERSION_1_1,
  CURLOPT_CUSTOMREQUEST => "GET",
  CURLOPT_HTTPHEADER => array(
    "X-MW-PUBLIC-KEY: PUBLICKEY",
    "X-MW-TIMESTAMP: $time"
  ),
));

$response = curl_exec($curl);
$err = curl_error($curl);

curl_close($curl);

if ($err) {
  echo "cURL Error #:" . $err;
} else {
  echo $response;
}
```

### Java

```java
OkHttpClient client = new OkHttpClient();

Request request = new Request.Builder()
  .url("https://app.boltmail.nz/api/lists/{LIST-UNIQUE-ID}/subscribers?page=1&per_page=9999")
  .get()
  .addHeader("X-MW-PUBLIC-KEY", "PUBLICKEY")
  .addHeader("X-MW-TIMESTAMP", "TIMESTAMP")
  .build();

Response response = client.newCall(request).execute();
```

### Python (3)

```python
import http.client
import time

conn = http.client.HTTPConnection("app.boltmail.nz")

headers = {
    'X-MW-PUBLIC-KEY': "PUBLICKEY",
    'X-MW-TIMESTAMP': str(time.time())
    }

conn.request("GET", "/api/lists/{LIST-UNIQUE-ID}/subscribers", headers=headers)

res = conn.getresponse()
data = res.read()

print(data.decode("utf-8"))
```

### Ruby

```ruby
require 'uri'
require 'net/https'

url = URI("https://app.boltmail.nz/api/lists/{LIST-UNIQUE-ID}/subscribers?page=1&per_page=9999")

http = Net::HTTP.new(url.host, url.port)

request = Net::HTTP::Get.new(url)
request["X-MW-PUBLIC-KEY"] = Time.now.to_i
request["X-MW-TIMESTAMP"] = 'PUBLICKEY'

response = http.request(request)
puts response.read_body
```

### NodeJS

```javascript
var request = require("request");

var options = { method: 'GET',
  url: 'https://app.boltmail.nz/api/lists/{LIST-UNIQUE-ID}/subscribers',
  qs: { page: '1', per_page: '9999' },
  headers: 
   { 'X-MW-TIMESTAMP': new Date().getTime(),
     'X-MW-PUBLIC-KEY': 'PUBLICKEY' } };

request(options, function (error, response, body) {
  if (error) throw new Error(error);

  console.log(body);
});

```

