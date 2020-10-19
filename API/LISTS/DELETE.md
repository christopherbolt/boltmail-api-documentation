# Delete List

Delete a single list

Replace `TIMESTAMP` with timestamp (string  like '1535093670'), `PUBLICKEY` with public key (get it from [API keys tab](https://app.boltmail.nz/customer/api-keys/index) in your panel ) and `{LIST-UNIQUE-ID}` with  List Unique Id of the list.

### HTTP Method
```
DELETE
```
### Endpoint
```
https://app.boltmail.nz/api/lists/{LIST-UNIQUE-ID}
```
## Code Examples

### cURL

```shell
curl -X DELETE \
  https://app.boltmail.nz/api/lists/{LIST-UNIQUE-ID} \
  -H 'X-MW-PUBLIC-KEY: PUBLICKEY' \
  -H 'X-MW-TIMESTAMP: TIMESTAMP'
```

### C# (RestSharp)

```csharp
var client = new RestClient("https://app.boltmail.nz/api/lists/{LIST-UNIQUE-ID}");
var request = new RestRequest(Method.DELETE);
request.AddHeader("X-MW-TIMESTAMP", "TIMESTAMP");
request.AddHeader("X-MW-PUBLIC-KEY", "PUBLICKEY");
IRestResponse response = client.Execute(request);
```

### PHP (with sdk)

[SDK Docs](https://developer.boltmail.nz/#/API/PHPSDK)

```php
$response = $endpoint->delete('{LIST-UNIQUE-ID}');
```

### PHP (curl)

```php
<?php

$curl = curl_init();
$time = time();
curl_setopt_array($curl, array(
  CURLOPT_URL => "https://app.boltmail.nz/api/lists/{LIST-UNIQUE-ID}",
  CURLOPT_RETURNTRANSFER => true,
  CURLOPT_ENCODING => "",
  CURLOPT_MAXREDIRS => 10,
  CURLOPT_TIMEOUT => 30,
  CURLOPT_HTTP_VERSION => CURL_HTTP_VERSION_1_1,
  CURLOPT_CUSTOMREQUEST => "DELETE",
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
  .url("https://app.boltmail.nz/api/lists/{LIST-UNIQUE-ID}")
  .delete(null)
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

conn.request("DELETE", "/api/lists/{LIST-UNIQUE-ID}", headers=headers)

res = conn.getresponse()
data = res.read()

print(data.decode("utf-8"))
```

### Ruby

```ruby
require 'uri'
require 'net/https'

url = URI("https://app.boltmail.nz/api/lists/{LIST-UNIQUE-ID}")

http = Net::HTTP.new(url.host, url.port)

request = Net::HTTP::Delete.new(url)
request["X-MW-PUBLIC-KEY"] = 'PUBLICKEY'
request["X-MW-TIMESTAMP"] = Time.now.to_i

response = http.request(request)
puts response.read_body
```

### NodeJS

```javascript
var request = require("request");
var options = {
    method: 'DELETE',
    url: 'https://app.boltmail.nz/api/lists/{LIST-UNIQUE-ID}',
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

