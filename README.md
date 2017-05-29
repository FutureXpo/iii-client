# III Client
[![npm][npm-image]][npm-url]
[![david][david-image]][david-url]
[![david-dev][david-dev-image]][david-dev-url]

[npm-image]: https://img.shields.io/npm/v/iii-client.svg
[npm-url]: https://npmjs.org/package/iii-client
[david-image]: https://david-dm.org/valentineus/iii-client/status.svg
[david-url]: https://david-dm.org/valentineus/iii-client
[david-dev-image]: https://david-dm.org/valentineus/iii-client/dev-status.svg
[david-dev-url]: https://david-dm.org/valentineus/iii-client?type=dev

Simple API for communicating with the bot of the \"iii.ru\" service.

## Features
- A small and light library.
- Receiving and sending messages.
- Create sessions, support for any available.
- Independent of the session or bot.

## Installation
```bash
npm install --save iii-client
```

## Using
To use the library, you need to know the bot ID.
It's easy to learn it, you need to go to the home address of a particular bot.
The address is as follows `http://iii.ru/inf/109cd867-0ef3-4473-af71-7543a9b2fccd`.
The value `109cd867-0ef3-4473-af71-7543a9b2fccd` and is the required parameter.

Initial connection with the bot:
```javascript
var bot = require('iii-client');

var uuid = '109cd867-0ef3-4473-af71-7543a9b2fccd';

bot.connect(uuid, function(data) {
    // code...
});
```

The answer is as follows:
```javascript
{
    cuid: '6791728a-263d-4bc8-9f7f-622856eb55ff',
    text: {
    // Lots of text...
}
```

The value of `cuid` is a session identifier and should be specified when sending a message:
```javascript
const options = {
    cuid: '6791728a-263d-4bc8-9f7f-622856eb55ff',
    text: 'Проверка связи. Ты получил моё сообщение?',
}

bot.send(options, function(raw) {
    /// code...
});
```

As a result, you will receive an answer:
```javascript
{
    result: {
        text: {
            value: 'Открой ближайшую к тебе книжку на 30-й странице и перепечатай 13-ю строчку сверху.',
            // Lots of text...
}
```

Enjoy!

## API
Description of the internal kitchen can be seen on the [documentation page](https://valentineus.github.io/iii-client/).

Found out a mistake or feel a lack of functionality? [issues](https://github.com/valentineus/iii-client/issues)

## License
[![JavaScript Style Guide](https://cdn.rawgit.com/feross/standard/master/badge.svg)](https://github.com/feross/standard)

[MIT](LICENSE.md). Copyright (c) [Valentin Popov](https://valentineus.link/).