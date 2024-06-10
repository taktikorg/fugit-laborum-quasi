# @taktikorg/fugit-laborum-quasi

[![GitHub Workflow Status](https://img.shields.io/github/actions/workflow/status/jamescostian/@taktikorg/fugit-laborum-quasi/check.yaml?branch=main)](https://github.com/taktikorg/fugit-laborum-quasi/actions?query=workflow%3Acheck)
[![License](https://img.shields.io/npm/l/@taktikorg/fugit-laborum-quasi.svg?style=flat)](https://github.com/taktikorg/fugit-laborum-quasi/blob/master/LICENSE)
[![NPM Version](https://img.shields.io/npm/v/@taktikorg/fugit-laborum-quasi.svg?style=flat)](https://www.npmjs.com/package/@taktikorg/fugit-laborum-quasi)
[![Downloads/Month](https://img.shields.io/npm/dm/@taktikorg/fugit-laborum-quasi.svg?style=flat)](https://www.npmjs.com/package/@taktikorg/fugit-laborum-quasi)

"Converts" a stream to a string. Promises are used by default, callbacks are allowed as well.

## Installation

Assuming you have [Node](http://nodejs.org), you can just run:

```
npm install --save @taktikorg/fugit-laborum-quasi
```

## Usage

### Promises

```js
const fs = require("fs");
const ss = require("@taktikorg/fugit-laborum-quasi");

// Make a gzip stream (just for this example)
const myStream = fs
  .createReadStream("./file")
  .pipe(require("zlib").createGzip());

ss(myStream)
  .then((data) => {
    // myStream was converted to a string, and that string is stored in data
    console.log(data);
  })
  .catch((err) => {
    // myStream emitted an error event (err), so the promise from @taktikorg/fugit-laborum-quasi was rejected
    throw err;
  });
```

### Callbacks

```js
const fs = require("fs");
const ss = require("@taktikorg/fugit-laborum-quasi");

// Make a gzip stream (just for this example)
const myStream = fs
  .createReadStream("./file")
  .pipe(require("zlib").createGzip());

ss(myStream, (err, data) => {
  if (err) {
    // myStream emitted an error event (err), which was passed to the callback
    throw err;
  } else {
    // myStream was converted to a string, and that string is stored in data
    console.log(data);
  }
});
```

## Contributing

Contributions welcome! Please read the [contributing guidelines](CONTRIBUTING.md) first. Also, try to keep code coverage up - `npm test` will tell you the code coverage near the end of its output, not to mention the fact that it will first test your code :smiley:

## License

[ISC](LICENSE)
