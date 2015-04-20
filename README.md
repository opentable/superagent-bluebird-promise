superagent-es6-promise
===========================

Add promise support to
[Superagent](http://visionmedia.github.io/superagent/) using
[es6-promise](https://github.com/jakearchibald/es6-promise).

This is a port of [superagent-bluebird-promise](https://github.com/KyleAMathews/superagent-bluebird-promise).

## Install
`npm install git+https://git@github.com/opentable/superagent-es6-promise.git`

## Usage
Simply require this package instead of `superagent`. Then you can call `.then()` instead of `.end()` to get a promise for your requests.

```javascript
var request = require('superagent-es6-promise');

request.get('/an-endpoint')
  .then(function(res) {
    console.log(res);
  }, function(error) {
    console.log(error);
  });
  
// Or, using .catch()
request.get('/an-endpoint')
  .then(function(res) {
    console.log(res);
  })
  .catch(function(error) {
    console.log(error);
  });
```

To generate a promise without registering any callbacks (e.g. when returning a promise from within a library), call `.promise()` instead.

```javascript
request.get('/an-endpoint').promise()
```

An error is thrown for all HTTP errors and responses that have a response code of 400 or above.

The `error` parameter always has a key `error` and for 4xx and 5xx responses, will also have a `status` and `res` key.

## Tests
TODO (fix existing)
