# Oto
## Installation

You can install the package via [Composer](https://getcomposer.org).

```bash
composer require tryoto/oto
```
Publish your oto config file with

```bash
php artisan vendor:publish --provider="Tryoto\Oto\OtoServiceProvider" --tag="oto"
```
then change your oto config from config/oto.php file
```php
    "refresh_token"        => "", //take it from oto company
    "mode"                => "test",//live
    "currency"            => "SAR" ,
```
## Usage

## Get Available Cities

```php
use Tryoto\Oto\Oto;
    $response = Oto::availableCities($limit , $page); 

```


## Check Delivery Fee

```php
use Tryoto\Oto\Oto;
    $itemDetails = ['weight' => 50 ,'totalDue' => 0 ,'originCity' => 'Riyadh','destinationCity' => 'Jeddah'];
    $response = Oto::checkDeliveryFee($itemDetails); 

```


## Create Order

```php
use Tryoto\Oto\Oto;
    $orderData   = ['orderId' => 1 ,'payment_method' => 'paid', 'amount' => '40','amount_due' => 0,'packageCount' => 10,'packageWeight' => 1 , 'orderDate' => '2022-06-12 22:30'];
    $customeData = ['name' =>'mohamed hatem' ,'email' => 'h7mdHatem26@gmail.com' , 'mobile' => '010027*****'];
    $addressData = ['address' => '20 ,hatem street, almehalla alkubra,Saudi Arabia','district' => 'hatem district' ,'city' => 'almehalla' ,'country' => 'SA' ,'lat' => '30.837645','lng' => '30.23456'];
    $items       = [ ["productId" => '123', "name"      => 'book', "price"     => '12', "rowTotal"  => '15', "taxAmount" => '3', "quantity"  => '2', "sku"  => 'arabic_book', "image"     => ''] , ["productId" => '145', "name"      => 'math book', "price"     => '18', "rowTotal"  => '20', "taxAmount" => '1', "quantity"  => '3', "sku"  => 'math_book', "image"     => '']];
    $response = Oto::createOrder($orderData ,$customeData ,$addressData ,$items);


```

## Cancel Order

```php
use Tryoto\Oto\Oto;

    $response = Oto::cancelOrder($orderId);

```

## get Order status

```php
use Tryoto\Oto\Oto;

    $response = Oto::orderStatus($orderId);

```


## Create Shipment

```php
use Tryoto\Oto\Oto;

    $response = Oto::createShipment($orderId, $deliveryOptionId);


```

## Create return Shipment

```php
use Tryoto\Oto\Oto;

    $response = Oto::createReturnShipment($orderId);


```


## documentaion
- https://www.tryoto.com
