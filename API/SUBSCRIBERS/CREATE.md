# Add Subscriber

Add a new subscriber to a list

Replace `TIMESTAMP` with timestamp (string  like '1535093670'), `PUBLICKEY` with public key (get it from [API keys tab](https://app.boltmail.nz/customer/api-keys/index) in your panel ) and `{LIST-UNIQUE-ID}` with  List Unique Id of the list.

### HTTP Method
```
POST
```
### Endpoint
```
https://app.boltmail.nz/api/lists/{LIST-UNIQUE-ID}/subscribers
```
### Request Body Parameters

Note, you should send data with `x-www-form-urlencoded`

Each parameter should be the TAG for a custom list field, the fields available on a list will vary. The EMAIL field is required. See the FIELDS endpoints for managing the fields available on a list.

Note that the new subscriber's status is determined by the 'opt_in' setting on the list. If this value is set to 'single' then the new subscriber will have a status of confirmed. But if the list's opt_in value is 'double' then the subscriber will have a status of 'unconfirmed' and the system will send them a confirmation email with a link they must click to confirm their subscription. Only confirmed subscribers will receive the email campaigns that you send. 

Example data structure, this should be serialized into x-www-form-urlencoded format:

```
{
    "EMAIL": "john.doe@doe.com",
    "FNAME": "John",
    "LNAME": "Doe"
}
```

### Example Response

The API will respond with the data record for the new subscriber. This will include the subscriber's Unique Id, you will need this to perform further actions against the subscriber

```json
{
    "status": "success",
    "data": {
        "record": {
            "subscriber_uid": "ps9129raz7401",
            "email": "john.doe@doe.com",
            "ip_address": "127.0.0.1",
            "source": "api",
            "date_added": {
                "expression": "NOW()",
                "params": []
            }
        }
    }
}
```

## Code Examples

### cURL

```shell
curl -X POST \
  https://app.boltmail.nz/api/lists/{LIST-UNIQUE-ID}/subscribers \
  -H 'Content-Type: application/x-www-form-urlencoded' \
  -H 'X-MW-PUBLIC-KEY: PUBLICKEY' \
  -H 'X-MW-TIMESTAMP: TIMESTAMP' \
  -d 'EMAIL=john.doe%40doe.com&FNAME=John&LNAME=Doe'
```

### C# (RestSharp)

```csharp
var client = new RestClient("https://app.boltmail.nz/api/lists/{LIST-UNIQUE-ID}/subscribers");
var request = new RestRequest(Method.POST);
request.AddHeader("Content-Type", "application/x-www-form-urlencoded");
request.AddHeader("X-MW-TIMESTAMP", "TIMESTAMP");
request.AddHeader("X-MW-PUBLIC-KEY", "PUBLICKEY");
request.AddParameter("undefined", "EMAIL=john.doe%40doe.com&FNAME=John&LNAME=Doe", ParameterType.RequestBody);
IRestResponse response = client.Execute(request);
```

### PHP (with sdk)

[SDK Docs](https://developer.boltmail.nz/#/API/PHPSDK)

```php
$response = $endpoint->create('{LIST-UNIQUE-ID}', array(
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
  CURLOPT_URL => "https://app.boltmail.nz/api/lists/{LIST-UNIQUE-ID}/subscribers",
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
  .url("https://app.boltmail.nz/api/lists/{LIST-UNIQUE-ID}/subscribers")
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
conn = http.client.HTTPConnection("app.boltmail.nz")

payload = "EMAIL=john.doe%40doe.com&FNAME=John&LNAME=Doe"

headers = {
    'X-MW-PUBLIC-KEY': "PUBLICKEY",
    'X-MW-TIMESTAMP': str(time.time()),
    'Content-Type': "application/x-www-form-urlencoded"
    }

conn.request("POST", "/api/lists/{LIST-UNIQUE-ID}/subscribers", payload, headers)

res = conn.getresponse()
data = res.read()

print(data.decode("utf-8"))
```

### Ruby

```ruby
require 'uri'
require 'net/https'

url = URI("https://app.boltmail.nz/api/lists/{LIST-UNIQUE-ID}/subscribers")

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
  url: 'https://app.boltmail.nz/api/lists/{LIST-UNIQUE-ID}/subscribers',
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

