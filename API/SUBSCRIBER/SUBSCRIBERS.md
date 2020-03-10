## GET SUBSCRIBERS

Replace `TIMESTAMP` with timestamp (string  like '1535093670'), `{LISTID}` with  List Unique Id of each list &  `PUBLICKEY` with public key (get it from [API keys tab](https://app.avangemail.com/customer/api-keys/index) in your panel ), 

Add part ``?page=1&per_page=9999`` to end of request URL , you can change ``page`` & ``per_page`` with your desirable amount.

### cURL

```cURL
curl -X GET \
  'https://avangemail.net/api/lists/{LISTID}/subscribers?page=1&per_page=9999' \
  -H 'X-MW-PUBLIC-KEY: PUBLICKEY' \
  -H 'X-MW-TIMESTAMP: TIMESTAMP'
```

### C# (RestSharp)

```
var client = new estClient("https://avangemail.net/api/lists/{LISTID}/subscribers?page=1&per_page=9999");
var request = new RestRequest(Method.GET);
request.AddHeader("X-MW-TIMESTAMP", "TIMESTAMP");
request.AddHeader("X-MW-PUBLIC-KEY", "PUBLICKEY");
IRestResponse response = client.Execute(request);
```

### [PHP (with sdk)](https://avangemail.com/docs/#/API/PHPSDK)

```php
$response = $endpoint->getSubscribers('{LISTID}', $pageNumber = 1, $perPage = 10);
```

### PHP (curl)

```php
<?php

$curl = curl_init();

curl_setopt_array($curl, array(
  CURLOPT_URL => "https://avangemail.net/api/lists/{LISTID}/subscribers?page=1&per_page=9999",
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
  .url("https://avangemail.net/api/lists/{LISTID}/subscribers?page=1&per_page=9999")
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

conn = http.client.HTTPConnection("avangemail,net")

headers = {
    'X-MW-PUBLIC-KEY': "PUBLICKEY",
    'X-MW-TIMESTAMP': str(time.time())
    }

conn.request("GET", "api,lists,{LISTID},subscribers", headers=headers)

res = conn.getresponse()
data = res.read()

print(data.decode("utf-8"))
```

### Ruby

```ruby
require 'uri'
require 'net/https'

url = URI("https://avangemail.net/api/lists/{LISTID}/subscribers?page=1&per_page=9999")

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
  url: 'https://avangemail.net/api/lists/{LISTID}/subscribers',
  qs: { page: '1', per_page: '9999' },
  headers: 
   { 'X-MW-TIMESTAMP': new Date().getTime(),
     'X-MW-PUBLIC-KEY': 'PUBLICKEY' } };

request(options, function (error, response, body) {
  if (error) throw new Error(error);

  console.log(body);
});

```

