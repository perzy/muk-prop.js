# muk [![Build Status](https://secure.travis-ci.org/fent/node-muk.png)](http://travis-ci.org/fent/node-muk)

[short consice explanation]


# Usage

Mock an object's methods.

```js
var fs = require('fs');
var muk = require('muk');

muk(fs, 'readFile', function(path, callback) {
  process.nextTick(callback.bind(null, null, 'file contents here'));
});
```

Mock dependencies too.

```js
var mockedRequest = function(url, options, callback) {
  // mock a request here
};

require('request', mockedRequest);

console.log(mockedRequest === require('request')); // true
```

Only userland modules dependencies can be mocked.

Restore all mocked methods and modules after tests.

```
muk.restore();

fs.readFile(file, function(err, data) {
  // will actually read from `file`
});
```


# Install

    npm install muk


# Tests
Tests are written with [mocha](http://visionmedia.github.com/mocha/)

```bash
npm test
```

# License
MIT
