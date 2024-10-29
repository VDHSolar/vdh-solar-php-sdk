<img src="https://beta.vdh-solar.nl/images/logo/logo-black.png" height="30">

# VDH Solar PHP SDK
The recommended way to interact with the VDH Solar API is by using one of our official SDKs. Today, VDH Solar offers a fine-tuned PHP library to make your life easier and give you the best experience when consuming the API.

## Installation

You can install the api-sdk in your PHP project using the composer command below.

```bash
composer require vdh-solar/api-sdk
```

## Usage

You should start by creating an instance of the VDH Solar `ApiClient`. This is the bases of all the subsequent request.

```php
$vdhApi = new \VdhSolar\ApiClient('eyJ...');
```
## Products

### List products
```php
$vdhApi->products->list();
```

### Filter products by name
```php
$vdhApi->products->list(
    name: 'Solar',
);
```

### Filter products by ID
```php
$vdhApi->products->list(
    id: 1,
);
```

### Filter products by updated date
```php
$vdhApi->products->list(
    updated_after: Carbon::yesterday()->startOfDay(),
);
```

```php
$vdhApi->products->list(
    updated_before: Carbon::yesterday()->startOfDay(),
);
```

### List a single product
```php
$vdhApi->products->get(12345);
```

## Paginated data
You can get all the paginated results by adding a paginate callback to the list method call. This callback will be called after every page load. So we will get page 1 and add them to the paginate callback method so you can do your magic. Once you magic is done, we will go and get the next page. This process will continue untill all pages have been collected.

This paginate functions works on all resources that support the list method. Eq. this is available for products, brands, categories, stock and orders.

```php
$vdhApi->products->list(
    updated_after: Carbon::yesterday()->startOfYear(),
    paginate: function (array $results): void {
        foreach ($results as $product) {
            // Do you magic
        }
    },
);
```

## Changelog

Please see [CHANGELOG](CHANGELOG.md) for more information what has changed recently.

## Docs
Please reference the full API documentation if you are missing something in these docs or in the SDK in general. You can always open a pull request or open an issue if you need changes to this SDK.

-   [VDH Solar API documentation](https://docs.vdh-solar.nl/)


## Testing

```bash
composer test
```

## Security

If you discover any security related issues, please email developers@vdh-solar.nl instead of using the issue tracker.

## Credits

-   [All Contributors](../../contributors)
-   [Marshmallow](https://github.com/marshmallow-packages)
-   [Stef van Esch](https://github.com/stefvanesch)

## License

The MIT License (MIT). Please see [License File](LICENSE.md) for more information.
