
<img src="https://webpack.github.io/assets/what-is-webpack.png" width="500">



```console
shell> npm install webpack -g
```

`entry.js`
```js
document.write("It works.");
```

`index.html`
```html
<html>
  <head>
    <meta charset="utf-8">
  </head>
  <body>
    <script type="text/javascript" src="bundle.js" charset="utf-8"></script>
  </body>
</html>
```

```console
shell> webpack ./entry.js bundle.js
shell> webpack --progress --colors ./entry.js bundle.js
```
---

`content.js`
```js
module.exports = "It works from content.js.";
```

`entry.js`
```js
document.write(require("./content.js"));
```
---

```console
shell> npm install css-loader style-loader
```

`style.css`
```css
body {
    background: yellow;
}
```

`entry.js`
```js
require("!style!css!./style.css");
document.write(require("./content.js"));
```
```console
shell> webpack ./entry.js bundle.js
```

---

```console
shell> npm install sass-loader node-sass webpack
```
```js
var css = require("!raw-loader!sass-loader!./file.scss");
```

```js
module.exports = {
  ...
  module: {
    loaders: [
      {
        test: /\.scss$/,
        loaders: ["style-loader", "css-loader", "sass-loader"]
      }
    ]
  }
};
```

### :books: 參考網站：
- [sass-loader](https://github.com/jtangelder/sass-loader)

---

```console
shell> npm install bootstrap-sass
```
```
require('bootstrap-loader');
```

### :books: 參考網站：
- [bootstrap-loader](https://github.com/shakacode/bootstrap-loader)

---

```
var webpack = require("webpack");

module.exports = {
  entry: {
    app: "./app.js",
    vendor: ["jquery", "underscore", ...],
  },
  output: {
    filename: "bundle.js"
  },
  plugins: [
    new webpack.optimize.CommonsChunkPlugin(/* chunkName= */"vendor", /* filename= */"vendor.bundle.js")
  ]
};
```
```
<script src="vendor.bundle.js"></script>
<script src="bundle.js"></script>
```
- https://webpack.github.io/docs/code-splitting.html

---

`entry.js`

```js
require("./style.css");
document.write(require("./content.js"));
```

```console
shell> webpack ./entry.js bundle.js --module-bind 'css=style!css'
```
---

`webpack.config.js`
```js
module.exports = {
  entry: "./entry.js",
  output: {
    path: __dirname,
    filename: "bundle.js"
  },
  module: {
    loaders: [{
      test: /\.css$/,
      loader: "style!css"
    }]
  }
};
```

```console
shell> webpack
```
---

```console
shell> webpack --progress --colors
```
---


### :books: 參考網站：
- [getting-started](http://webpack.github.io/docs/tutorials/getting-started/)


---

```console
shell> webpack
shell> webpack -p
shell> webpack --watch
shell> webpack -d
shell> webpack --progress --colors
shell> webpack --progress --colors --watch
```

---

```console
shell> npm install jquery --save-dev
```

```js
var $ = require("jquery");
$("p").text("It works.");
```

```js
require("coffee!./cup.coffee");
require("./loader!./dir/file.txt");
require("jade!./template.jade");
require("!style!css!less!bootstrap/less/bootstrap.less");
```

```js
{
    module: {
        loaders: [
            { test: /\.jade$/, loader: "jade" },
            // => "jade" loader is used for ".jade" files

            { test: /\.css$/, loader: "style!css" },
            // => "style" and "css" loader is used for ".css" files
            // Alternative syntax:
            { test: /\.css$/, loaders: ["style", "css"] },
        ]
    }
}
```


- https://webpack.github.io/docs/using-loaders.html
- https://webpack.js.org/loaders/json-loader/
- https://webpack.js.org/loaders/css-loader/
- https://github.com/jtangelder/sass-loader

```js
const HtmlWebpackPlugin = require('html-webpack-plugin'); //installed via npm
const webpack = require('webpack'); //to access built-in plugins

const config = {
  entry: './path/to/my/entry/file.js',
  output: {
    filename: 'my-first-webpack.bundle.js',
    path: './dist'
  },
  module: {
    rules: [
      {
        test: /\.(js|jsx)$/,
        loader: 'babel-loader'
      }
    ]
  },
  plugins: [
    new webpack.optimize.UglifyJsPlugin(),
    new HtmlWebpackPlugin({template: './src/index.html'})
  ]
};

module.exports = config;
```