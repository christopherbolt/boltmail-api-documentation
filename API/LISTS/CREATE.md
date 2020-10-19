# Create List

Create a new list

Replace `TIMESTAMP` with timestamp (string  like '1535093670'), `PUBLICKEY` with public key (get it from [API keys tab](https://app.boltmail.nz/customer/api-keys/index) in your panel )

### HTTP method
```
POST
```
### Endpoint
```
https://app.boltmail.nz/api/lists/
```
### Request Body Parameters

You should send data as ``x-www-form-urlencoded``. 

Example data structure, this should be serialized into x-www-form-urlencoded format. 

Take care to set an approriate "opt_in" value for your use case and legal requirements. If the opt_in value is set to 'single' then new subscribers added to this list will have a status of 'unconfirmed' and will be sent a confirmation email with a link they must click to confirm their subscription. If the opt_in value is 'single' then new subscribers will have a status of 'confirmed'. Only confirmed subscribers will be sent the email campaigns that you send.

```
{
  // required
  "general": {
    "name": "My list created from the API", // required
    "description": "This is a test list, created from the API." // required,
    "opt_in": "single" // or "double". If double opt in then subscribers are sent a confirmation email with a link they must click to confirm their subscription
  },
  // required
  "defaults": {
    "from_name": "John Doe", // required
    "from_email": "johndoe@doe.com", // required
    "reply_to": "johndoe@doe.com", // required
    "subject": "Hello!" // required
  },
  // optional
  "notifications": {
    // notification when new subscriber added
    "subscribe": "yes", // yes|no
    // notification when subscriber unsubscribes
    "unsubscribe": "yes",  // yes|no
    // where to send the notifications.
    "subscribe_to": "johndoe@doe.com",
    "unsubscribe_to": "johndoe@doe.com"
  },
  // optional, if not set company data from your account will be used
  "company": {
    "name": "John Doe INC",  // required
    "country": "United States", // required
    "zone": "New York", // required
    "address_1": "Some street address", // required
    "address_2": "",
    "zone_name": "",
    "city": "New York City", // when country doesn't have required zone.
    "zip_code": "10019"
  }
}
```

### Example Response

The API will respond with the Unique Id for this list. You will need to use this Unique Id to perform further API actions against this list

```json
{
    "status": "success",
    "list_uid": "sz923tpl9d28e"
}
```

## Code Examples

### cURL

```shell
curl -X POST \
  https://app.boltmail.nz/api/lists/ \
  -H 'Content-Type: application/x-www-form-urlencoded' \
  -H 'X-MW-PUBLIC-KEY: PUBLICKEY' \
  -H 'X-MW-TIMESTAMP: TIMESTAMP' \
  -d 'general%5Bname%5D=My+list+created+from+the+API&general%5Bdescription%5D=This+is+a+test+list%2C+created+from+the+API.&defaults%5Bfrom_name%5D=John+Doe&defaults%5Bfrom_email%5D=johndoe%40doe.com&defaults%5Breply_to%5D=johndoe%40doe.com&defaults%5Bsubject%5D=Hello%21&notifications%5Bsubscribe%5D=yes&notifications%5Bunsubscribe%5D=yes&notifications%5Bsubscribe_to%5D=johndoe%40doe.com&notifications%5Bunsubscribe_to%5D=johndoe%40doe.com&company%5Bname%5D=John+Doe+INC&company%5Bcountry%5D=United+States&company%5Bzone%5D=New+York&company%5Baddress_1%5D=Some+street+address&company%5Baddress_2%5D=&company%5Bzone_name%5D=&company%5Bcity%5D=New+York+City&company%5Bzip_code%5D=10019'
```

### C# (RestSharp)

```csharp
var client = new RestClient("https://app.boltmail.nz/api/lists/");
var request = new RestRequest(Method.POST);
request.AddHeader("X-MW-TIMESTAMP", "TIMESTAMP");
request.AddHeader("X-MW-PUBLIC-KEY", "PUBLICKEY");
request.AddHeader("Content-Type", "application/x-www-form-urlencoded");
request.AddParameter("undefined", "general%5Bname%5D=My+list+created+from+the+API&general%5Bdescription%5D=This+is+a+test+list%2C+created+from+the+API.&defaults%5Bfrom_name%5D=John+Doe&defaults%5Bfrom_email%5D=johndoe%40doe.com&defaults%5Breply_to%5D=johndoe%40doe.com&defaults%5Bsubject%5D=Hello%21&notifications%5Bsubscribe%5D=yes&notifications%5Bunsubscribe%5D=yes&notifications%5Bsubscribe_to%5D=johndoe%40doe.com&notifications%5Bunsubscribe_to%5D=johndoe%40doe.com&company%5Bname%5D=John+Doe+INC&company%5Bcountry%5D=United+States&company%5Bzone%5D=New+York&company%5Baddress_1%5D=Some+street+address&company%5Baddress_2%5D=&company%5Bzone_name%5D=&company%5Bcity%5D=New+York+City&company%5Bzip_code%5D=10019", ParameterType.RequestBody);
IRestResponse response = client.Execute(request);
```

### PHP (with sdk)

[SDK Docs](https://developer.boltmail.nz/#/API/PHPSDK)

```php

$endpoint = new MailWizzApi_Endpoint_Lists();
$response = $endpoint->create(array(
    // required
    'general' => array(
        'name'          => 'My list created from the API', // required
        'description'   => 'This is a test list, created from the API.', // required
    ),
    // required
    'defaults' => array(
        'from_name' => 'John Doe', // required
        'from_email'=> 'johndoe@doe.com', // required
        'reply_to'  => 'johndoe@doe.com', // required
        'subject'   => 'Hello!',
    ),
    // optional
    'notifications' => array(
        // notification when new subscriber added
        'subscribe'         => 'yes', // yes|no
        // notification when subscriber unsubscribes
        'unsubscribe'       => 'yes', // yes|no
        // where to send the notifications.
        'subscribe_to'      => 'johndoe@doe.com',
        'unsubscribe_to'    => 'johndoe@doe.com',
    ),
    // optional, if not set customer company data will be used
    'company' => array(
        'name'      => 'John Doe INC', // required
        'country'   => 'United States', // required
        'zone'      => 'New York', // required
        'address_1' => 'Some street address', // required
        'address_2' => '',
        'zone_name' => '', // when country doesn't have required zone.
        'city'      => 'New York City',
        'zip_code'  => '10019',
    ),
));
```

### PHP (curl)

```php
<?php

$curl = curl_init();

curl_setopt_array($curl, array(
  CURLOPT_URL => "https://app.boltmail.nz/api/lists/",
  CURLOPT_RETURNTRANSFER => true,
  CURLOPT_ENCODING => "",
  CURLOPT_MAXREDIRS => 10,
  CURLOPT_TIMEOUT => 30,
  CURLOPT_HTTP_VERSION => CURL_HTTP_VERSION_1_1,
  CURLOPT_CUSTOMREQUEST => "POST",
  CURLOPT_POSTFIELDS => "general%5Bname%5D=My+list+created+from+the+API&general%5Bdescription%5D=This+is+a+test+list%2C+created+from+the+API.&defaults%5Bfrom_name%5D=John+Doe&defaults%5Bfrom_email%5D=johndoe%40doe.com&defaults%5Breply_to%5D=johndoe%40doe.com&defaults%5Bsubject%5D=Hello%21&notifications%5Bsubscribe%5D=yes&notifications%5Bunsubscribe%5D=yes&notifications%5Bsubscribe_to%5D=johndoe%40doe.com&notifications%5Bunsubscribe_to%5D=johndoe%40doe.com&company%5Bname%5D=John+Doe+INC&company%5Bcountry%5D=United+States&company%5Bzone%5D=New+York&company%5Baddress_1%5D=Some+street+address&company%5Baddress_2%5D=&company%5Bzone_name%5D=&company%5Bcity%5D=New+York+City&company%5Bzip_code%5D=10019",
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

MediaType mediaType = MediaType.parse("application/octet-stream");
RequestBody body = RequestBody.create(mediaType, "general%5Bname%5D=My+list+created+from+the+API&general%5Bdescription%5D=This+is+a+test+list%2C+created+from+the+API.&defaults%5Bfrom_name%5D=John+Doe&defaults%5Bfrom_email%5D=johndoe%40doe.com&defaults%5Breply_to%5D=johndoe%40doe.com&defaults%5Bsubject%5D=Hello%21&notifications%5Bsubscribe%5D=yes&notifications%5Bunsubscribe%5D=yes&notifications%5Bsubscribe_to%5D=johndoe%40doe.com&notifications%5Bunsubscribe_to%5D=johndoe%40doe.com&company%5Bname%5D=John+Doe+INC&company%5Bcountry%5D=United+States&company%5Bzone%5D=New+York&company%5Baddress_1%5D=Some+street+address&company%5Baddress_2%5D=&company%5Bzone_name%5D=&company%5Bcity%5D=New+York+City&company%5Bzip_code%5D=10019");
Request request = new Request.Builder()
  .url("https://app.boltmail.nz/api/lists/")
  .post(body)
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

payload = "general%5Bname%5D=My+list+created+from+the+API&general%5Bdescription%5D=This+is+a+test+list%2C+created+from+the+API.&defaults%5Bfrom_name%5D=John+Doe&defaults%5Bfrom_email%5D=johndoe%40doe.com&defaults%5Breply_to%5D=johndoe%40doe.com&defaults%5Bsubject%5D=Hello%21&notifications%5Bsubscribe%5D=yes&notifications%5Bunsubscribe%5D=yes&notifications%5Bsubscribe_to%5D=johndoe%40doe.com&notifications%5Bunsubscribe_to%5D=johndoe%40doe.com&company%5Bname%5D=John+Doe+INC&company%5Bcountry%5D=United+States&company%5Bzone%5D=New+York&company%5Baddress_1%5D=Some+street+address&company%5Baddress_2%5D=&company%5Bzone_name%5D=&company%5Bcity%5D=New+York+City&company%5Bzip_code%5D=10019"

headers = {
    'X-MW-PUBLIC-KEY': "PUBLICKEY",
    'X-MW-TIMESTAMP': str(time.time())
    }

conn.request("POST", "/api/lists/", payload, headers)

res = conn.getresponse()
data = res.read()

print(data.decode("utf-8"))
```

### Ruby

```ruby
require 'uri'
require 'net/https'

url = URI("https://app.boltmail.nz/api/lists/")

http = Net::HTTP.new(url.host, url.port)

request = Net::HTTP::Post.new(url)
request["X-MW-PUBLIC-KEY"] = 'PUBLICKEY'
request["X-MW-TIMESTAMP"] = Time.now.to_i
request.body = "general%5Bname%5D=My+list+created+from+the+API&general%5Bdescription%5D=This+is+a+test+list%2C+created+from+the+API.&defaults%5Bfrom_name%5D=John+Doe&defaults%5Bfrom_email%5D=johndoe%40doe.com&defaults%5Breply_to%5D=johndoe%40doe.com&defaults%5Bsubject%5D=Hello%21&notifications%5Bsubscribe%5D=yes&notifications%5Bunsubscribe%5D=yes&notifications%5Bsubscribe_to%5D=johndoe%40doe.com&notifications%5Bunsubscribe_to%5D=johndoe%40doe.com&company%5Bname%5D=John+Doe+INC&company%5Bcountry%5D=United+States&company%5Bzone%5D=New+York&company%5Baddress_1%5D=Some+street+address&company%5Baddress_2%5D=&company%5Bzone_name%5D=&company%5Bcity%5D=New+York+City&company%5Bzip_code%5D=10019"

response = http.request(request)
puts response.read_body
```

### NodeJS

```javascript
var request = require("request");

var options = { method: 'POST',
  url: 'https://app.boltmail.nz/api/lists/',
  headers: 
   { 'X-MW-TIMESTAMP': new Date().getTime(),
     'X-MW-PUBLIC-KEY': '33b364bbfa2f81677a8a4df36fa5adad2fd53276' },
  body: 'general%5Bname%5D=My+list+created+from+the+API&general%5Bdescription%5D=This+is+a+test+list%2C+created+from+the+API.&defaults%5Bfrom_name%5D=John+Doe&defaults%5Bfrom_email%5D=johndoe%40doe.com&defaults%5Breply_to%5D=johndoe%40doe.com&defaults%5Bsubject%5D=Hello%21&notifications%5Bsubscribe%5D=yes&notifications%5Bunsubscribe%5D=yes&notifications%5Bsubscribe_to%5D=johndoe%40doe.com&notifications%5Bunsubscribe_to%5D=johndoe%40doe.com&company%5Bname%5D=John+Doe+INC&company%5Bcountry%5D=United+States&company%5Bzone%5D=New+York&company%5Baddress_1%5D=Some+street+address&company%5Baddress_2%5D=&company%5Bzone_name%5D=&company%5Bcity%5D=New+York+City&company%5Bzip_code%5D=10019' };

request(options, function (error, response, body) {
  if (error) throw new Error(error);

  console.log(body);
});

```

