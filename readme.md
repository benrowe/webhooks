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
