# Get Segments

Get all segments from a list

Segments are filtered views within a list. You cannot currently create a segment from the API, you must use the web interface.

Replace `TIMESTAMP` with timestamp (string like '1535093670'), `PUBLICKEY` with public key (get it from [API keys tab](https://app.boltmail.nz/customer/api-keys/index) in your panel ) and `{LIST-UNIQUE-ID}` with  List Unique Id of the list.

### HTTP Method
```
GET
```
### Endpoint
```
https://app.boltmail.nz/api/lists/{LIST-UNIQUE-ID}/segments
```
### Example Response

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
                "segment_uid": "ay126yy236d31",
                "name": "Eample segment 1",
                "subscribers_count": "20"
            },
            {
                "segment_uid": "xy895p9x8seb5",
                "name": "Example segment 3",
                "subscribers_count": "240"
            }
        ]
    }
}
```

## Code Examples

### cURL

```shell
curl -X GET \
  https://app.boltmail.nz/api/lists/{LIST-UNIQUE-ID}/segments \
  -H 'X-MW-PUBLIC-KEY: PUBLICKEY' \
  -H 'X-MW-TIMESTAMP: TIMESTAMP'
```

### C# (RestSharp)

```csharp
var client = new RestClient("https://app.boltmail.nz/api/lists/{LIST-UNIQUE-ID}/segments");
var request = new RestRequest(Method.GET);
request.AddHeader("X-MW-TIMESTAMP", "TIMESTAMP");
request.AddHeader("X-MW-PUBLIC-KEY", "PUBLICKEY");
IRestResponse response = client.Execute(request);
```

### [PHP (with sdk)](https://developer.boltmail.nz/#/API/PHPSDK)

```php
$response = $endpoint->getSegments('{LISTID}');
```

### PHP (curl)

```php
<?php

$curl = curl_init();
$time = time();
curl_setopt_array($curl, array(
  CURLOPT_URL => "https://app.boltmail.nz/api/lists/{LIST-UNIQUE-ID}/segments",
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
  .url("https://app.boltmail.nz/api/lists/{LIST-UNIQUE-ID}/segments")
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
conn.request("GET", "/api/lists/{LIST-UNIQUE-ID}/segments", headers=headers)

res = conn.getresponse()
data = res.read()

print(data.decode("utf-8"))
```

### Ruby

```ruby
require 'uri'
require 'net/https'

url = URI("https://app.boltmail.nz/api/lists/{LIST-UNIQUE-ID}/segments")

http = Net::HTTP.new(url.host, url.port)

request = Net::HTTP::Get.new(url)
request["X-MW-PUBLIC-KEY"] = 'PUBLICKEY'
request["X-MW-TIMESTAMP"] = Time.now.to_i

response = http.request(request)
puts response.read_body
```

### NodeJS

```javascript
var request = require("request");
var options = {
    method: 'GET',
    url: 'https://app.boltmail.nz/api/lists/{LIST-UNIQUE-ID}/segments',
    headers:{
        'X-MW-TIMESTAMP': new Date().getTime(),
        'X-MW-PUBLIC-KEY': 'PUBLICKEY'
    }
};
request(options, function (error, response, body) {
    if (error) throw new Error(error);
    console.log(body);
});
```

