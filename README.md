# clue/datagram [![Build Status](https://travis-ci.org/clue/datagram.png?branch=master)](https://travis-ci.org/clue/datagram)

UDP datagram socket client and server for reactphp

## Quickstart example

Once [installed](#install), you can use the following code to connect to an UDP server listening on
`localhost:1234` and send and receive UDP datagrams:  

```php
$loop = React\EventLoop\Factory::create();

$factory = new Datagram\Factory($loop);

$factory->createClient('localhost:1234')->then(function (Datagram\Socket $client) {
    $client->send('first');

    $client->on('message', function($message, $serverAddress, $client) {
        echo 'received "' . $message . '" from ' . $serverAddress. PHP_EOL;
    });
});

$loop->run();
```

## Usage

This library's API is modelled after node.js's API for
[UDP / Datagram Sockets (dgram.Socket)](http://nodejs.org/api/dgram.html).

## Install

The recommended way to install this library is [through composer](http://getcomposer.org). [New to composer?](http://getcomposer.org/doc/00-intro.md)

```JSON
{
    "require": {
        "clue/datagram": "0.3.*"
    }
}
```

## License

MIT
