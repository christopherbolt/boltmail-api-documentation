A simple BoltMail library and example for PHP.

## Getting started

TO DO
<!--- There are two ways to use BoltMail PHP SDK:

1. Installing Via Composer:

```
composer require --prefer-dist avangdev/avang-php dev-master
```

2. [Simply download zip](https://github.com/christopherbolt/avang-php/archive/master.zip)

   use example [here](https://github.com/christopherbolt/avang-php/tree/master/examples)

### Usage

you will need to require `vendor/autoload.php` file in your index.php 

Example: Add new email to mailing lists

```
<?php
require 'vendor/autoload.php';

$config = new BoltMailApi_Config(array(
    'publicKey'     => 'PUBLIC-KEY',
    'privateKey'    => 'PRIVATE-KEY',
    'components' => array(
        'cache' => array(
            'class'     => 'BoltMailApi_Cache_File',
            'filesPath' => dirname(__FILE__) . '/vendor/avangdev/avang-php/BoltMailApi/Cache/data/cache', // make sure it is writable by webserver
        )

    ),
));
BoltMailApi_Base::setConfig($config);
date_default_timezone_set('UTC');

$endpoint = new BoltMailApi_Endpoint_ListSubscribers();
/*===================================================================================*/
// ADD SUBSCRIBER
$response = $endpoint->create('LIST-UNIQUE-ID', array(
    'EMAIL'    => 'john.napi@example.com',
    'FNAME'    => 'John',
    'LNAME'    => 'Napi'
));
// DISPLAY RESPONSE, You can comment bellow
echo '<hr /><pre>';
print_r($response->body);
echo '</pre>';

/*===================================================================================*/
```

 Example: Get all lists

```

$response = $endpoint->getLists($pageNumber = 1, $perPage = 10);
// DISPLAY RESPONSE
echo '<pre>';
print_r($response->body);
echo '</pre>';
```

#####  Other Example:  [see example directory](https://github.com/christopherbolt/avang-php/tree/master/examples) 

--->