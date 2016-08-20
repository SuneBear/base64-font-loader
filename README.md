# Base64 loader for webpack
This loader will Base64 encode any files.

## Usage

[Documentation: Using loaders](http://webpack.github.io/docs/using-loaders.html)

```js
module.exports = {
  context: path.join(__dirname, 'src'),
  entry: {
    'index': './index.js'
  },
  module: {
    loaders: [{
        test: /\.html$/,
        loader: 'raw'
      },
      {
        test: /\.scss$/,
        loader: ExtractTextPlugin.extract('style-loader', 'css-loader?sourceMap!autoprefixer-loader!sass-loader?sourceMap')
      },
      {
        test: /\.(woff|ttf|eot|svg)(\?v=[0-9]\.[0-9]\.[0-9])?$/,
        loader: 'base64-loader'
      }
    ]
  },
  devtool: 'source-map',
  output: {
    path: path.join(__dirname, 'dist'),
    publicPath: '/',
    filename: '[name].js',
    sourceMapFilename: '[file].map'
  }
};
```

## Example
### Input:

```css
@font-face {
  font-family: 'icons';
  src: url('fonts/icon.svg?v=0.0.1') format('svg');
  font-weight: normal;
  font-style: normal;
}
```

### Exports:

```css
@font-face {
  font-family: 'icons';
  src: url(data:image/svg+xml;charset=utf-8;base64,[BASE_64_STRING]) format('svg');
  font-weight: normal;
  font-style: normal;
}
```

## License

MIT (http://www.opensource.org/licenses/mit-license.php)
