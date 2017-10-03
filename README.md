# III Client
[![NPM](https://img.shields.io/npm/v/iii-client.svg)](https://www.npmjs.com/package/iii-client)
[![Build Status](https://travis-ci.org/valentineus/iii-client.svg?branch=master)](https://travis-ci.org/valentineus/iii-client)
[![Codacy Badge](https://api.codacy.com/project/badge/Grade/81b2fdc2f5dd42a6bdc8fdb43640b282)](https://www.codacy.com/app/valentineus/iii-client)
[![Codacy Coverage Badge](https://api.codacy.com/project/badge/Coverage/81b2fdc2f5dd42a6bdc8fdb43640b282)](https://www.codacy.com/app/valentineus/iii-client/files)
[![Gitter Badge](https://badges.gitter.im/Join%20Chat.svg)](https://gitter.im/valentineus/iii-client)

Simple API for communicating with the bot of the \"iii.ru\" service.

## Features
- A small and light library.
- Works, both in NodeJS, and in the browser.
- Getting session ID.
- Sending and receiving messages.
- Does not process incoming errors.

## Installation
NodeJS:
```bash
npm install --save iii-client
```

Browser:
```html
<script src="https://unpkg.com/iii-client@latest/dist/bundle.js">
    /* iiiClient - This is the global name for accessing the package */
</script>
```

## Using
An example of a connection, receiving session identification and sending a bot message:
```javascript
import { connect, send } from 'iii-client';

var uuid = '109cd867-0ef3-4473-af71-7543a9b2fccd';
var text = 'Hello, World!';

/* We connect to the system and get a session */
connect(uuid, (request) => {
    console.info(`Session: ${request}`);
    /* Send the message and process the response */
    if (request.result) {
        var cuid = request.result.cuid;
        send(cuid, text, (answer) => {
            console.info(`Answer: ${answer}`);
        });
    }
});
```

## API
## Functions
<dl>
    <dt>
        <a href="#connect">connect(uuid, callback)</a>
    </dt>
    <dd>
        <p>Connection to the service and retrieves the session identifier.</p>
    </dd>
    <dt>
        <a href="#send">send(cuid, text, callback)</a>
    </dt>
    <dd>
        <p>Sends a message to bot and returns a response.</p>
    </dd>
</dl>

<a name="connect"></a>

## connect(uuid, callback)
Connection to the service and retrieves the session identifier.

| Param | Type | Description |
| --- | --- | --- |
| uuid | <code>String</code> | Bot ID |
| callback | <code>function</code> | Function handler |

<a name="send"></a>

## send(cuid, text, callback)
Sends a message to bot and returns a response.

| Param | Type | Description |
| --- | --- | --- |
| cuid | <code>String</code> | Session ID |
| text | <code>String</code> | Send messages |
| callback | <code>function</code> | Function handler |

## License
[![JavaScript Style Guide](https://cdn.rawgit.com/feross/standard/master/badge.svg)](https://github.com/eslint/eslint)

[MIT](LICENSE.md).
Copyright (c)
[Valentin Popov](https://valentineus.link/).