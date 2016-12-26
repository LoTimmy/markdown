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
entry.js
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
```


---

```console
shell> npm install jquery --save-dev
```

```
var $ = require("jquery");
$("p").text("It works.");
```
