## Add Subscriber

Replace `TIMESTAMP` with timestamp (string  like '1535093670'), `{LISTID}` with  List Unique Id of each list &  `PUBLICKEY` with public key (get it from [API keys tab](https://app.avangemail.com/customer/api-keys/index) in your panel ), 

#### Request Body Parameters

Note, you should send data with `x-www-form-urlencoded` or `multipart/form-data` , `and application/json` not support

Example data:

```
{
    "EMAIL": "john.doe@doe.com",
    "FNAME": "John",
    "LNAME": "Doe"
}
```

### cURL

```cURL
curl -X POST \
  https://avangemail.net/api/lists/{LISTID}/subscribers \
  -H 'Content-Type: application/x-www-form-urlencoded' \
  -H 'X-MW-PUBLIC-KEY: PUBLICKEY' \
  -H 'X-MW-TIMESTAMP: TIMESTAMP' \
  -d 'EMAIL=john.doe%40doe.com&FNAME=John&LNAME=Doe'
```

### C# (RestSharp)

```
var client = new RestClient("https://avangemail.net/api/lists/{LISTID}/subscribers");
var request = new RestRequest(Method.POST);
request.AddHeader("Content-Type", "application/x-www-form-urlencoded");
request.AddHeader("X-MW-TIMESTAMP", "TIMESTAMP");
request.AddHeader("X-MW-PUBLIC-KEY", "PUBLICKEY");
request.AddParameter("undefined", "EMAIL=john.doe%40doe.com&FNAME=John&LNAME=Doe", ParameterType.RequestBody);
IRestResponse response = client.Execute(request);
```

### [PHP (with sdk)](https://avangemail.com/docs/#/API/PHPSDK)

```php
$response = $endpoint->create('{LISTID}', array(
    'EMAIL'    => 'john.doe@doe.com', 
    'FNAME'    => 'John',
    'LNAME'    => 'Doe'
));
```

### PHP (curl)

```php
<?php

$curl = curl_init();

curl_setopt_array($curl, array(
  CURLOPT_URL => "https://avangemail.net/api/lists/{LISTID}/subscribers",
  CURLOPT_RETURNTRANSFER => true,
  CURLOPT_ENCODING => "",
  CURLOPT_MAXREDIRS => 10,
  CURLOPT_TIMEOUT => 30,
  CURLOPT_HTTP_VERSION => CURL_HTTP_VERSION_1_1,
  CURLOPT_CUSTOMREQUEST => "POST",
  CURLOPT_POSTFIELDS => "EMAIL=john.doe%40doe.com&FNAME=John&LNAME=Doe",
  CURLOPT_HTTPHEADER => array(
    "Content-Type: application/x-www-form-urlencoded",
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

MediaType mediaType = MediaType.parse("application/x-www-form-urlencoded");
RequestBody body = RequestBody.create(mediaType, "EMAIL=john.doe%40doe.com&FNAME=John&LNAME=Doe");
Request request = new Request.Builder()
  .url("https://avangemail.net/api/lists/{LISTID}/subscribers")
  .post(body)
  .addHeader("X-MW-PUBLIC-KEY", "PUBLICKEY")
  .addHeader("X-MW-TIMESTAMP", "TIMESTAMP")
  .addHeader("Content-Type", "application/x-www-form-urlencoded")
  .build();

Response response = client.newCall(request).execute();
```

### Python (3)

```python
import http.client
import time
conn = http.client.HTTPConnection("avangemail,net")

payload = "EMAIL=john.doe%40doe.com&FNAME=John&LNAME=Doe"

headers = {
    'X-MW-PUBLIC-KEY': "PUBLICKEY",
    'X-MW-TIMESTAMP': str(time.time()),
    'Content-Type': "application/x-www-form-urlencoded"
    }

conn.request("POST", "api,lists,{LISTID},subscribers", payload, headers)

res = conn.getresponse()
data = res.read()

print(data.decode("utf-8"))
```

### Ruby

```ruby
require 'uri'
require 'net/https'

url = URI("https://avangemail.net/api/lists/{LISTID}/subscribers")

http = Net::HTTP.new(url.host, url.port)

request = Net::HTTP::Post.new(url)
request["X-MW-PUBLIC-KEY"] = 'PUBLICKEY'
request["X-MW-TIMESTAMP"] = Time.now.to_i
request["Content-Type"] = 'application/x-www-form-urlencoded'
request.body = "EMAIL=john.doe%40doe.com&FNAME=John&LNAME=Doe"

response = http.request(request)
puts response.read_body
```

### NodeJS

```javascript
var request = require("request");

var options = { method: 'POST',
  url: 'https://avangemail.net/api/lists/{LISTID}/subscribers',
  headers: 
   { 'Content-Type': 'application/x-www-form-urlencoded',
     'X-MW-TIMESTAMP': new Date().getTime(),
     'X-MW-PUBLIC-KEY': 'PUBLICKEY' },
  form: { EMAIL: 'john.doe@doe.com', FNAME: 'John', LNAME: 'Doe' } };

request(options, function (error, response, body) {
  if (error) throw new Error(error);

  console.log(body);
});

```

