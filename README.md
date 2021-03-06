# Stylelint Plugin for webpack

### Why you might want to use this plugin instead of [stylelint-loader](https://github.com/adrianhall/stylelint-loader)

**stylelint-loader** lints the files you `require` or the ones you define as an `entry` in your webpack config. But `@imports` in those files are not followed, so just the main file (for each require/entry) is linted.

Instead, with **stylelint-webpack-plugin** you just define file globs, like stylelint does by default. So you get all your files linted.


## Install

```console
$ npm install stylelint-webpack-plugin
```

## Usage

In your webpack configuration

```js
var styleLintPlugin = require('stylelint-webpack-plugin');


module.exports = {
  // ...
  plugins: [
    new styleLintPlugin(),
  ],
  // ...
}
```

### Options

See [stylelint options](http://stylelint.io/user-guide/node-api/#options), for the complete list of options.

* `configFile`: You can change the config file location. Default: (`.stylelintrc`)
* `context`: String indicating the root of your SCSS files. Default inherits from webpack config.
* `files`: Change the glob pattern for finding files. Default: (`['**/*.s?(a|c)ss']`)
* `syntax`: Use `'scss'` to lint .scss files. Default (`undefined`)
* `formatter`: Use a custom formatter to print errors to the console. Default: (`require('stylelint/dist/formatters/stringFormatter').default`)
* `failOnError`: Have Webpack's build process die on error. Default: `false`
* `quiet`: Don't print stylelint output to the console. Default: `false`


```js
// Default settings
module.exports = {
  plugins: [
    new styleLintPlugin({
      configFile: '.stylelintrc',
      context: 'inherits from webpack',
      files: '**/*.s?(a|c)ss',
      failOnError: false,
    })
  ]
}
```

#### Errors

The plugin will dump full reporting of errors.
Set `failOnError` to true if you want webpack build process breaking with any stylelint error.
You can use the `quiet` option to not print stylelint output to the console.


### Acknowledgement

This project is basically a modified version of `sasslint-webpack-plugin`. It changed considerably
since stylelint is async, and its Node API changes compared with sasslint.

#### [License](LICENSE)
