## Returns Lists

Returns lists  

Replace `TIMESTAMP` with timestamp (string  like '1535093670'), `PUBLICKEY` with public key (get it from [API keys tab](https://app.avangemail.com/customer/api-keys/index) in your panel )

### cURL

```cURL
curl -X GET \
  https://avangemail.net/api/lists \
  -H 'X-MW-PUBLIC-KEY: PUBLICKEY' \
  -H 'X-MW-TIMESTAMP: TIMESTAMP'
```

### C# (RestSharp)

```
var client = new RestClient("https://avangemail.net/api/lists");
var request = new RestRequest(Method.GET);
request.AddHeader("X-MW-TIMESTAMP", "TIMESTAMP");
request.AddHeader("X-MW-PUBLIC-KEY", "PUBLICKEY");
IRestResponse response = client.Execute(request);
```

### [PHP (with sdk)](https://avangemail.com/docs/#/API/PHPSDK)

```php
$response = $endpoint->getLists($pageNumber = 1, $perPage = 10);
```

### PHP (curl)

```php
<?php

$curl = curl_init();
$time = time();
curl_setopt_array($curl, array(
  CURLOPT_URL => "https://avangemail.net/api/lists",
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
  .url("https://avangemail.net/api/lists")
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

conn.request("GET", "api,lists", headers=headers)

res = conn.getresponse()
data = res.read()

print(data.decode("utf-8"))
```

### Ruby

```ruby
require 'uri'
require 'net/https'

url = URI("https://avangemail.net/api/lists")

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
    url: 'https://avangemail.net/api/lists',
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
