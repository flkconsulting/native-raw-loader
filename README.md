<div align="center">
  <img width="200" height="200"
    src="https://cdn3.iconfinder.com/data/icons/lexter-flat-colorfull-file-formats/56/raw-256.png">
  <a href="https://github.com/webpack/webpack">
    <img width="200" height="200"
      src="https://webpack.js.org/assets/icon-square-big.svg">
  </a>
</div>

[![npm][npm]][npm-url]
[![node][node]][node-url]
[![deps][deps]][deps-url]
[![tests][tests]][tests-url]
[![coverage][cover]][cover-url]
[![chat][chat]][chat-url]
[![size][size]][size-url]

# native-raw-loader

**DEPREACTED for v5**: please consider migrating to [`asset modules`](https://webpack.js.org/guides/asset-modules/).

A loader for webpack that allows importing files as a String or as native file.

## Getting Started

To begin, you'll need to install `native-raw-loader`:

```console
$ npm install native-raw-loader --save-dev
```

Then add the loader to your `webpack` config. For example:

**file.js**

```js
import txt from './file.txt';
```

**webpack.config.js**

```js
// webpack.config.js
module.exports = {
  module: {
    rules: [
      {
        test: /\.txt$/i,
        use: 'native-raw-loader',
      },
    ],
  },
};
```

And run `webpack` via your preferred method.

## Options

|            Name             |    Type     | Default | Description            |
| :-------------------------: | :---------: | :-----: | :--------------------- |
| **[`esModule`](#esmodule)** | `{Boolean}` | `true`  | Uses ES modules syntax |
|   **[`native`](#native)**   | `{Boolean}` | `true`  | Uses native import     |

### `esModule`

Type: `Boolean`
Default: `true`

By default, `native-raw-loader` generates JS modules that use the ES modules syntax.
There are some cases in which using ES modules is beneficial, like in the case of [module concatenation](https://webpack.js.org/plugins/module-concatenation-plugin/) and [tree shaking](https://webpack.js.org/guides/tree-shaking/).

You can enable a CommonJS module syntax using:

**webpack.config.js**

```js
module.exports = {
  module: {
    rules: [
      {
        test: /\.txt$/i,
        use: [
          {
            loader: 'native-raw-loader',
            options: {
              esModule: false,
            },
          },
        ],
      },
    ],
  },
};
```

### `native`

Type: `Boolean`
Default: `true`

By default, `native-raw-loader` generates JS modules that use the ES modules syntax.
There are some cases in which using native import is beneficial, so you can a import a native fill with out any changes.

You can enable a CommonJS module syntax using:

**webpack.config.js**

```js
module.exports = {
  module: {
    rules: [
      {
        test: /\.txt$/i,
        use: [
          {
            loader: 'native-raw-loader',
            options: {
              native: true,
            },
          },
        ],
      },
    ],
  },
};
```

## Examples

### Inline

```js
import txt from 'native-raw-loader!./file.txt';
```

Beware, if you already define loader(s) for extension(s) in `webpack.config.js` you should use:

```js
import css from '!!native-raw-loader!./file.txt'; // Adding `!!` to a request will disable all loaders specified in the configuration
```

## Contributing

Please take a moment to read our contributing guidelines if you haven't yet done so.

[CONTRIBUTING](./.github/CONTRIBUTING.md)

## License

[MIT](./LICENSE)
