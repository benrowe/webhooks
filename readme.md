# Webhooks

[![Latest Version on Packagist][ico-version]][link-packagist]
[![Software License][ico-license]](LICENSE.md)
[![Build Status][ico-travis]][link-travis]
[![Coverage Status][ico-scrutinizer]][link-scrutinizer]
[![Quality Score][ico-code-quality]][link-code-quality]
[![Total Downloads][ico-downloads]][link-downloads]

An agnostic package that handles the registration and delivery of webhook notifications to external systems

## Install

Via Composer

``` bash
$ composer require benrowe/webhooks
```

## Usage

``` php
<?php


```

## Change log

Please see [CHANGELOG](CHANGELOG.md) for more information what has changed recently.

## Testing

``` bash
$ composer test
```

## Contributing

Please see [CONTRIBUTING](CONTRIBUTING.md) and [CONDUCT](CONDUCT.md) for details.

## Security

If you discover any security related issues, please email ben.rowe.83@gmail.com instead of using the issue tracker.

## Credits

- [Ben Rowe][link-author]
- [All Contributors][link-contributors]

## License

The MIT License (MIT). Please see [License File](LICENSE.md) for more information.

[ico-version]: https://img.shields.io/packagist/v/benrowe/webhooks.svg?style=flat-square
[ico-license]: https://img.shields.io/badge/license-MIT-brightgreen.svg?style=flat-square
[ico-travis]: https://img.shields.io/travis/benrowe/webhooks/master.svg?style=flat-square
[ico-scrutinizer]: https://img.shields.io/scrutinizer/coverage/g/benrowe/webhooks.svg?style=flat-square
[ico-code-quality]: https://img.shields.io/scrutinizer/g/benrowe/webhooks.svg?style=flat-square
[ico-downloads]: https://img.shields.io/packagist/dt/benrowe/webhooks.svg?style=flat-square

[link-packagist]: https://packagist.org/packages/benrowe/webhooks
[link-travis]: https://travis-ci.org/benrowe/webhooks
[link-scrutinizer]: https://scrutinizer-ci.com/g/benrowe/webhooks/code-structure
[link-code-quality]: https://scrutinizer-ci.com/g/benrowe/webhooks
[link-downloads]: https://packagist.org/packages/benrowe/webhooks
[link-author]: https://github.com/benrowe
[link-contributors]: ../../contributors

## Notes



### Service Interface

```php
// constructor
$service = new \Benrowe\Webhooks\WebhookService(StorageInterface $storage);

// primary methods
$service->subscribe(WebhookSubscription $subscription);
$service->unsubscribe(WebhookSubscription $subscription);
$service->dispatchEvent(WebhookEvent $event);
$service->dispatch(string $eventName);

// secondary methods
$service->protocols;//collection
$service->protocols->register(ProtocolHandlerInterface $handler);

```

### Structures

```
Event {
  Name string
}

WebhookSubscription {
  PayloadUrl string
  Conte
}
```

### Ideas
- Persistance of the registered webhooks is handled by the `StorageInterface`
- Protocol handlers are registered against the service (http(s), amqp). Each protocol handler 
- Content type handlers are registered against the service (json, yaml, xml, etc). When registering a new Subscription, it will verify the payload url to see if there's an appropriate handler registered.
  - By default we will include a http(s) handler
-