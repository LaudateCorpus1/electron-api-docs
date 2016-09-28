# electron-api-docs [![Build Status](https://travis-ci.org/electron/electron-api-docs.svg?branch=master)](https://travis-ci.org/electron/electron-api-docs)

Electron's API documentation in a structured JSON format.

## Installation

```sh
npm install electron-api-docs --save
```

Or take it for a spin in your Node.js REPL:

```sh
npm i -g trymodule && trymodule electron-api-docs=apis
```

Note: This package is not semantically versioned. It is published in step with
Electron. When you install `electron-api-docs@1.4.1`, you're getting the API
docs from Electron v1.4.1.

## Usage

```js
const apis = require('electron-api-docs')
```

When you require it, you get an array of API objects

```js
apis.length
// => 33
```

The array has a key for each API `name`, for convenient access:

```js
apis.BrowserWindow
apis.BrowserWindow.staticMethods.getAllWindows.description
apis.WebContents.instanceMethods.savePage.parameters.saveType.possibleValues
apis.app.events.quit
```

All of the arrays have named keys, but they're still actually arrays, so
functional methods like `find`, `map`, `filter`, and `every` can be used:

```js
apis.find(api => api.name === 'BrowserWindow')

apis.filter(api => api.type === 'Class')

apis.filter(api => api.type === 'Module')

apis.map(api => api.name)

// All arrays have named keys, not just the top-level array!
apis.BrowserWindow.instanceMethods.map(method => method.name)
```

## Tests

```sh
npm install
npm test
```

## Dependencies

- [keyed-array](https://github.com/zeke/keyed-array): Recursively add named keys to arrays of objects

## Dev Dependencies

- [chai](https://github.com/chaijs/chai): BDD/TDD assertion library for node.js and the browser. Test framework agnostic.
- [gh-latest-release](https://github.com/shinnn/gh-latest-release): Get the latest published full release for the Github repository
- [json](https://github.com/trentm/json): a &#39;json&#39; command for massaging and processing JSON on the command line
- [mocha](https://github.com/mochajs/mocha): simple, flexible, fun test framework
- [standard](https://github.com/feross/standard): JavaScript Standard Style
- [standard-markdown](https://github.com/zeke/standard-markdown): Test your Markdown files for Standard JavaScript Style™


## License

MIT
