BotPoison
==========
###### Author: Jason Clark (mithereal@gmail.com)

###### Description: Trap, Block and Poison Bots. 

## Example
```php
<?php
 
require_once __DIR__ . '/vendor/autoload.php';
 
# create the warden

$warden = new Warden();
  
# ban an ip

$warden->admit('127.0.0.1');
  
# check if ip has been banned

echo $warden->lookup('127.0.0.1');
  
# unban an ip

$warden->discharge('127.0.0.1');

# clear all ips

$warden->empty();

# show all ips

$warden->jail();

# render a view with injected data (we are poisoning the bot by injecting the Email or SSN Poison 
# module Data (/lib/Poison/?.php)into the view file then rendering to txt)

echo $warden->exploit('page.html','Email');
echo $warden->exploit('page.html','SSN');

## exploits can be chained together ex. 

$injected_email = $warden->exploit('page.html','Email');
echo $warden->exploit($injected_email,'SSN');