# Oto
## Installation

You can install the package via [Composer](https://getcomposer.org).

```bash
composer require hatemfaysal/oto:dev-master

```
Publish your oto config file with

```bash
php artisan vendor:publish --provider="Hatemfaysal\Oto\OtoServiceProvider" --tag="oto"
```
then change your oto config from config/oto.php file
```php
    "refresh_token"        => "", //take it from oto company
    "mode"                => "test",//live
    "currency"            => "SAR" ,
```
## Usage



## Create Order

```php
use Hatemfaysal\Oto\Oto;
    $orderData   = ["orderId"=> "1","pickupLocationCode"=> "code-020","createShipment"=> "true","deliveryOptionId"=> 564,"payment_method"=> "paid","amount"=> 100,
    "amount_due"=> 0,"currency"=> "SAR","customsValue"=>"12","customsCurrency"=>"USD","packageCount"=> 2,"packageWeight"=> 1,"boxWidth"=>10,"boxLength"=> 10,"boxHeight"=> 10,
    "orderDate"=> "19/12/2024 15:45","deliverySlotDate"=> "19/12/2024","deliverySlotTo"=> "12pm","deliverySlotFrom"=> "2:30pm","senderName"=>"Sender Company"];
    $customeData = ["name"=> "عبدالله الغامدي","email"=> "test@test.com","mobile"=> "546607389"];
    $addressData = ["address"=> "6832, Abruq AR Rughamah District, Jeddah 22272 3330, Saudi Arabia","district"=> "Al Hamra","city"=> "Jeddah","country"=> "SA","postcode"=> "12345","lat"=> "40.706333","lng"=> "29.888211","refID"=>"1000012","W3WAddress"=>"alarmed.cards.stuffy"];
    $items       = [ ["productId"=> 112,"name"=> "test product","price"=> 100,"rowTotal"=> 100,"taxAmount"=> 15,"quantity"=> 1,"sku"=> "test-product","image"=> "http://...."] , ["name"=> "test product 2","price"=> 100,"quantity"=> 1,"sku"=> "test-product-2"]];
    $response = Oto::createOrder($orderData ,$customeData ,$addressData ,$items);


```



## Check Delivery Fee

```php
use Hatemfaysal\Oto\Oto;
    $itemDetails = ["height"=> 10,"width"=> 10,"length"=> 10,"weight"=> 10,'originCity' => 'riyadh','destinationCity' => 'Jeddah'];
    $response = Oto::checkDeliveryFee($itemDetails); 

```


## Create Shipment

```php
use Hatemfaysal\Oto\Oto;

    $response = Oto::createShipment($orderId, $deliveryOptionId);


```


## Get Available Cities

```php
use Hatemfaysal\Oto\Oto;
    $response = Oto::availableCities($limit , $page); 

```

## Cancel Order

```php
use Hatemfaysal\Oto\Oto;

    $response = Oto::cancelOrder($orderId);

```

## get Order status

```php
use Hatemfaysal\Oto\Oto;

    $response = Oto::orderStatus($orderId);

```




## Create return Shipment

```php
use Hatemfaysal\Oto\Oto;

    $response = Oto::createReturnShipment($orderId);


```


## documentaion
- https://www.tryoto.com
