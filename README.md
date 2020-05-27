Mercure Component
=================

> Mercure is a protocol allowing to push data updates to web browsers and other
  HTTP clients in a convenient, fast, reliable and battery-efficient way.
  It is especially useful to publish real-time updates of resources served through
  web APIs, to reactive web and mobile apps.

The Mercure Component implements the "publisher" part of [the Mercure Protocol](https://mercure.rocks).

Getting Started
---------------

```
$ composer require symfony/mercure
```

```php
// change these values accordingly to your hub installation
define('HUB_URL', 'https://demo.mercure.rocks/.well-known/mercure');
define('JWT', 'eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJtZXJjdXJlIjp7InN1YnNjcmliZSI6WyJmb28iLCJiYXIiXSwicHVibGlzaCI6WyJmb28iXX19.LRLvirgONK13JgacQ_VbcjySbVhkSmHy3IznH3tA9PM');

use Symfony\Component\Mercure\Jwt\StaticJwtProvider;
use Symfony\Component\Mercure\Publisher;
use Symfony\Component\Mercure\Update;

$publisher = new Publisher(HUB_URL, new StaticJwtProvider(JWT));
// Serialize the update, and dispatch it to the hub, that will broadcast it to the clients
$id = $publisher(new Update('https://example.com/books/1.jsonld', 'Hi from Symfony!', ['target1', 'target2']));
```

Resources
---------

* [Documentation](https://symfony.com/doc/current/mercure.html)
* [Contributing](https://symfony.com/doc/current/contributing/index.html)
* [Report issues](https://github.com/symfony/mercure/issues) and
  [send Pull Requests](https://github.com/symfony/mercure/pulls)
  in the [`symfony/mercure` repository](https://github.com/symfony/mercure)
