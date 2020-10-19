# Get All Lists

Returns all lists in your account

Replace `TIMESTAMP` with timestamp (string  like '1535093670'), `PUBLICKEY` with public key (get it from [API keys tab](https://app.boltmail.nz/customer/api-keys/index) in your panel )

### HTTP Method
```
GET
```
### Endpoint
```
https://app.boltmail.nz/api/lists
```
### Example response

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
                "general": {
                    "list_uid": "sz923tpl9d28e",
                    "name": "My list created from the API",
                    "display_name": "My list created from the API",
                    "description": "This is a test list, created from the API."
                },
                "defaults": {
                    "from_name": "John Doe",
                    "reply_to": "johndoe@doe.com",
                    "subject": "Hello!"
                },
                "notifications": {
                    "subscribe": "no",
                    "unsubscribe": "no",
                    "subscribe_to": null,
                    "unsubscribe_to": null
                },
                "company": {
                    "name": "Example Limited",
                    "address_1": "123 Example Street",
                    "address_2": "Example",
                    "zone_name": "",
                    "city": "Auckland",
                    "zip_code": "0930",
                    "phone": "+64 9 950 3348",
                    "address_format": "[COMPANY_NAME]\n[COMPANY_ADDRESS_1] [COMPANY_ADDRESS_2]\n[COMPANY_CITY] [COMPANY_ZONE] [COMPANY_ZIP]\n[COMPANY_COUNTRY]\n[COMPANY_WEBSITE]",
                    "country": {
                        "country_id": "153",
                        "name": "New Zealand",
                        "code": "NZ"
                    },
                    "zone": {
                        "zone_id": "2344",
                        "name": "Auckland",
                        "code": "AUK"
                    }
                }
            },
            {
                "general": {
                    "list_uid": "tq534xwvdp27e",
                    "name": "Another List",
                    "display_name": "Another List",
                    "description": "My list"
                },
                "defaults": {
                    "from_name": "Test User",
                    "reply_to": "chris@christopherbolt.com",
                    "subject": ""
                },
                "notifications": {
                    "subscribe": "no",
                    "unsubscribe": "no",
                    "subscribe_to": "",
                    "unsubscribe_to": ""
                },
                "company": {
                    "name": "Example Limited",
                    "address_1": "123 Example Street",
                    "address_2": "Example",
                    "zone_name": "",
                    "city": "Auckland",
                    "zip_code": "0930",
                    "phone": "+64 9 950 3348",
                    "address_format": "[COMPANY_NAME]\n[COMPANY_ADDRESS_1] [COMPANY_ADDRESS_2]\n[COMPANY_CITY] [COMPANY_ZONE] [COMPANY_ZIP]\n[COMPANY_COUNTRY]\n[COMPANY_WEBSITE]",
                    "country": {
                        "country_id": "153",
                        "name": "New Zealand",
                        "code": "NZ"
                    },
                    "zone": {
                        "zone_id": "2344",
                        "name": "Auckland",
                        "code": "AUK"
                    }
                }
            }
        ]
    }
}
```

## Code Examples

### cURL

```shell
curl -X GET \
  https://app.boltmail.nz/api/lists \
  -H 'X-MW-PUBLIC-KEY: PUBLICKEY' \
  -H 'X-MW-TIMESTAMP: TIMESTAMP'
```

### C# (RestSharp)

```csharp
var client = new RestClient("https://app.boltmail.nz/api/lists");
var request = new RestRequest(Method.GET);
request.AddHeader("X-MW-TIMESTAMP", "TIMESTAMP");
request.AddHeader("X-MW-PUBLIC-KEY", "PUBLICKEY");
IRestResponse response = client.Execute(request);
```

### PHP (with sdk)

[SDK Docs](https://developer.boltmail.nz/#/API/PHPSDK)

```php
$response = $endpoint->getLists($pageNumber = 1, $perPage = 10);
```

### PHP (curl)

```php
<?php

$curl = curl_init();
$time = time();
curl_setopt_array($curl, array(
  CURLOPT_URL => "https://app.boltmail.nz/api/lists",
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
  .url("https://app.boltmail.nz/api/lists")
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

conn.request("GET", "/api/lists", headers=headers)

res = conn.getresponse()
data = res.read()

print(data.decode("utf-8"))
```

### Ruby

```ruby
require 'uri'
require 'net/https'

url = URI("https://app.boltmail.nz/api/lists")

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
    url: 'https://app.boltmail.nz/api/lists',
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
