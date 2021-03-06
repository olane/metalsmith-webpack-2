# metalsmith-webpack-2

![nodei.co](https://nodei.co/npm/metalsmith-webpack-2.png?downloads=true&downloadRank=true&stars=true)

![npm](https://img.shields.io/npm/v/metalsmith-webpack-2.svg) ![github-issues](https://img.shields.io/github/issues/leviwheatcroft/metalsmith-webpack-2.svg) ![stars](https://img.shields.io/github/stars/leviwheatcroft/metalsmith-webpack-2.svg) ![forks](https://img.shields.io/github/forks/leviwheatcroft/metalsmith-webpack-2.svg)

A [webpack][webpack] plugin for [Metalsmith][metalsmith].

See the [annotated source][annotated source] or [github repo][github repo].

## Installation

```
npm install metalsmith-webpack-2
```

## Usage

```js
import webpack from 'metalsmith-webpack-2'

Metalsmith(__dirname)
  .use(webpack(options))
  .build()
```

### Options

`options` may be:

 * a [webpack configuration][webpack configuration] object.
 * a path to your webpack configuration file
 * null / undefined, config will be read from `webpack.config.js`

## Example

Construct your webpack config exactly as you would if you were calling webpack
from the command line.

```js
Metalsmith(__dirname)
.use(webpack({
  entry: {
    site: resolve(__dirname, 'src', 'js', 'site.js'),
  },
  output: {
    path: resolve(__dirname, 'build', 'js'),
    filename: '[name].[chunkhash].js'
  }
}))
.build()
```

*Note*: It's important that absolute paths are provided to webpack, as is normal webpack behaviour. That means including your `src` and `build` directories as demonstrated above.

This example uses an asset's hash in it's filename (fingerprinting / cache busting). The filename for this asset will be stored in metalsmith meta, so you could access it from a template with something like:

`<script src="{{webpack.assets['site']}}"></script>`

This plugin will not ignore source files, you should use [metalsmith-ignore][metalsmith-ignore] for that

See the [tests][tests] for more examples, or [metalsmith-all-the-things][metalsmith-all-the-things] for a full implementation.

## Tests

```
$ npm test
```

## License

MIT License, see [LICENSE](https://github.com/christophercliff/metalsmith-webpack/blob/master/LICENSE.md) for details.

## See Also

 * [metalsmith-webpack-dev-server][metalsmith-webpack-dev-server]
 * [metalsmith-webpack-suite][metalsmith-webpack-suite]
 * [metalsmith-ignore][metalsmith-ignore]

 [annotated source]: https://leviwheatcroft.github.io/metalsmith-webpack-2 "fancy annotated source"
 [github repo]: https://github.com/leviwheatcroft/metalsmith-webpack-2 "github repo"
[metalsmith]: http://www.metalsmith.io/
[tests]: https://github.com/christophercliff/metalsmith-webpack/blob/master/test/index.js
[webpack]: http://webpack.github.io/
[webpack configuration]: http://webpack.github.io/docs/configuration.html
[metalsmith-ignore]: https://github.com/segmentio/metalsmith-ignore
[metalsmith-webpack-dev-server]: https://github.com/okonet/metalsmith-webpack-dev-server
[metalsmith-webpack-suite]: https://github.com/axe312ger/metalsmith-webpack-suite
[metalsmith-all-the-things]: https://github.com/leviwheatcroft/metalsmith-all-the-things
