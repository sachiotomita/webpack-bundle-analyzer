# Webpack Bundle Analyzer
Webpack plugin and CLI utility that represents bundle content as convenient interactive zoomable treemap

[![NPM version][npm-image]][npm-url] [![Downloads][downloads-image]][npm-url]

## What is this for?
Just take a look at this demo:

![webpack bundle analyzer zoomable treemap](https://cloud.githubusercontent.com/assets/302213/19711973/908ae002-9b42-11e6-8471-bc8e9ab6dec7.gif)

This module will help you:

1. Realize what's *really* inside your bundle
2. Find out what modules make up the most of it's size
3. Find modules that got there by mistake
4. Optimize it!

And the best thing is it supports minified bundles! It parses them to get real size of bundled modules.

## Installation and usage
There are two ways to use this module:

### As plugin
```sh
npm install --save-dev webpack-bundle-analyzer
```

In `webpack.config.js`:
```js
var BundleAnalyzerPlugin = require('webpack-bundle-analyzer').BundleAnalyzerPlugin;

// ...
plugins: [new BundleAnalyzerPlugin()]
// ...
```

`BundleAnalyzerPlugin` constructor can take an optional configuration object that defaults to this:

```js
new BundleAnalyzerPlugin({
  // Can be `server`, `static` or `disabled`.
  // In `server` mode analyzer will start HTTP server to show bundle report.
  // In `static` mode single HTML file with bundle report will be generated.
  // In `disabled` mode you can use this plugin to just generate Webpack Stats JSON file by setting `generateStatsFile` to `true`.
  analyzerMode: 'server',
  // Port that will be used by in `server` mode to start HTTP server.
  analyzerPort: 8888,
  // Path to bundle report file that will be generated in `static` mode.
  // If relative path is provided, it will be relative to bundles output directory
  reportFilename: 'report.html',
  // Automatically open report in default browser
  openAnalyzer: true,
  // If `true`, Webpack Stats JSON file will be generated in bundles output directory
  generateStatsFile: false,
  // Name of Webpack Stats JSON file that will be generated if `generateStatsFile` is `true`.
  // Relative to bundles output directory.
  statsFilename: 'stats.json',
})
```

### As CLI utility
You can also analyze already existing bundles if you have Webpack Stats JSON file.

You can generate it using `BundleAnalyzerPlugin` with `generateStatsFile` option set to `true` or with this simple
command: `webpack --profile --json > stats.json`

`webpack-bundle-analyzer --help` will show you all usage information.
 
## License

[MIT](LICENSE)

[downloads-image]: https://img.shields.io/npm/dt/webpack-bundle-analyzer.svg
[npm-url]: https://www.npmjs.com/package/webpack-bundle-analyzer
[npm-image]: https://img.shields.io/npm/v/webpack-bundle-analyzer.svg
