上次更新日期： 2016-04-12                                                  

---

**Installing with Bower**
```
npm install -g gulp bower

bower cache clean
bower update

bower init
bower install --save Polymer/polymer

bower install --save Polymer/core-ajax



bower install --save iron-elements
bower install --save paper-elements


bower install --save PolymerElements/iron-icons
```

my-element.html
```html
<link rel="import" href="../bower_components/polymer/polymer.html">

<polymer-element name="my-element" noscript>
  <template>
    <span>Hello from <b>my-element</b>. This is my Shadow DOM.</span>
  </template>
</polymer-element>
```


```html
<link rel="import" href="../bower_components/polymer/polymer.html">
<link rel="import" href="../bower_components/core-ajax/core-ajax.html">

<polymer-element name="my-element" noscript>
  <template>
    <span>I'm <b>my-element</b>. This is my Shadow DOM.</span>
    <!-- to retrieve actual data, replace example.com with a real URL -->
    <core-ajax url="http://example.com/json" auto response="{{resp}}"></core-ajax>
    <textarea value="{{resp}}"></textarea>
  </template>
</polymer-element>
```


index.html
```html
<!DOCTYPE html>
<html>
  <head>
    <!-- 1. Load platform support before any code that touches the DOM. -->
    <script src="bower_components/webcomponentsjs/webcomponents.min.js"></script>
    <!-- 2. Load the component using an HTML Import -->
    <link rel="import" href="elements/my-element.html">
  </head>
  <body>
    <!-- 3. Declare the element by its tag. -->
    <my-element></my-element>
  </body>
</html>
```

```html
<!DOCTYPE html>
<html>
  <head>
    <!-- 1. Load platform support before any code that touches the DOM. -->
    <script src="bower_components/webcomponentsjs/webcomponents.min.js"></script>
    <!-- 2. Load the component using an HTML Import -->
    <link rel="import" href="bower_components/iron-icons/iron-icons.html">
  </head>
  <body>
    <!-- 3. Declare the element by its tag. -->
    <iron-icon icon="icons:account-box"></iron-icon>
    <iron-icon icon="icons:account-circle"></iron-icon>
  </body>
</html>
```

```html
<dom-module id="element-name">

  <template>
    <style>
      /* CSS rules for your element */
    </style>
  
    <!-- local DOM for your element -->

    <div>{{greeting}}</div> <!-- data bindings in local DOM -->
  </template>

  <script>
    // element registration
    Polymer({
      is: "element-name",

      // add properties and methods on the element's prototype

      properties: {
        // declare properties for the element's public API
        greeting: {
          type: String,
          value: "Hello!"
        }
      }
    });
  </script>

</dom-module>
```

---
### :books: 參考網站：

- [Get the Polymer library](https://www.polymer-project.org/1.0/docs/start/getting-the-code.html)
