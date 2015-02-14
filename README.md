# negotiator

[![NPM Version][npm-image]][npm-url]
[![NPM Downloads][downloads-image]][downloads-url]
[![Node.js Version][node-version-image]][node-version-url]
[![Build Status][travis-image]][travis-url]
[![Test Coverage][coveralls-image]][coveralls-url]

An HTTP content negotiator for Node.js

## Installation

```sh
$ npm install negotiator
```

## API

```js
var Negotiator = require('negotiator')
```

### Accept Negotiation

```js
availableMediaTypes = ['text/html', 'text/plain', 'application/json']

// The negotiator constructor receives a request object
negotiator = new Negotiator(request)

// Let's say Accept header is 'text/html, application/*;q=0.2, image/jpeg;q=0.8'

negotiator.mediaTypes()
// -> ['text/html', 'image/jpeg', 'application/*']

negotiator.mediaTypes(availableMediaTypes)
// -> ['text/html', 'application/json']

negotiator.mediaType(availableMediaTypes)
// -> 'text/html'
```

You can check a working example at `examples/accept.js`.

#### Methods

##### mediaTypes(availableMediaTypes)

Returns an array of preferred media types ordered by priority from a list of
available media types.

##### mediaType(availableMediaType)

Returns the most preferred media type from a list of available media types.

### Accept-Language Negotiation

```js
negotiator = new Negotiator(request)

availableLanguages = 'en', 'es', 'fr'

// Let's say Accept-Language header is 'en;q=0.8, es, pt'

negotiator.languages()
// -> ['es', 'pt', 'en']

negotiator.languages(availableLanguages)
// -> ['es', 'en']

language = negotiator.language(availableLanguages)
// -> 'es'
```

You can check a working example at `examples/language.js`.

#### Methods

##### languages(availableLanguages)

Returns an array of preferred languages ordered by priority from a list of
available languages.

##### language(availableLanguages)

Returns the most preferred language from a list of available languages.

### Accept-Charset Negotiation

```js
availableCharsets = ['utf-8', 'iso-8859-1', 'iso-8859-5']

negotiator = new Negotiator(request)

// Let's say Accept-Charset header is 'utf-8, iso-8859-1;q=0.8, utf-7;q=0.2'

negotiator.charsets()
// -> ['utf-8', 'iso-8859-1', 'utf-7']

negotiator.charsets(availableCharsets)
// -> ['utf-8', 'iso-8859-1']

negotiator.charset(availableCharsets)
// -> 'utf-8'
```

You can check a working example at `examples/charset.js`.

#### Methods

##### charsets(availableCharsets)

Returns an array of preferred charsets ordered by priority from a list of
available charsets.

##### charset(availableCharsets)

Returns the most preferred charset from a list of available charsets.

### Accept-Encoding Negotiation

```js
availableEncodings = ['identity', 'gzip']

negotiator = new Negotiator(request)

// Let's say Accept-Encoding header is 'gzip, compress;q=0.2, identity;q=0.5'

negotiator.encodings()
// -> ['gzip', 'identity', 'compress']

negotiator.encodings(availableEncodings)
// -> ['gzip', 'identity']

negotiator.encoding(availableEncodings)
// -> 'gzip'
```

You can check a working example at `examples/encoding.js`.

#### Methods

##### encodings(availableEncodings)

Returns an array of preferred encodings ordered by priority from a list of
available encodings.

##### encoding(availableEncodings)

Returns the most preferred encoding from a list of available encodings.

## License

[MIT](LICENSE)

[npm-image]: https://img.shields.io/npm/v/negotiator.svg?style=flat
[npm-url]: https://npmjs.org/package/negotiator
[node-version-image]: https://img.shields.io/node/v/negotiator.svg?style=flat
[node-version-url]: http://nodejs.org/download/
[travis-image]: https://img.shields.io/travis/jshttp/negotiator.svg?style=flat
[travis-url]: https://travis-ci.org/jshttp/negotiator
[coveralls-image]: https://img.shields.io/coveralls/jshttp/negotiator.svg?style=flat
[coveralls-url]: https://coveralls.io/r/jshttp/negotiator?branch=master
[downloads-image]: https://img.shields.io/npm/dm/negotiator.svg?style=flat
[downloads-url]: https://npmjs.org/package/negotiator
