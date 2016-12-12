
```js 
bitDepth = window.screen.colorDepth
iAvail = window.screen.availHeight
var screenAvailWidth = window.screen.availWidth;

iHeight = window.screen.height
lWidth = window.screen.width

alert("load new content");
document.write("<h1>Main title</h1>")
```

```html
<div>
  <script type="text/javascript">
    document.write("<h1>Main title</h1>")
  </script>
</div>
```

```html
<script type="application/javascript">
  function getIP(json) {
    document.write("My public IP address is: ", json.ip);
  }
</script>

<script type="application/javascript" src="https://api.ipify.org?format=jsonp&callback=getIP"></script>
```

### :books: 參考網站：
- [ipify](https://www.ipify.org/)

---

```html
<p onmouseover="this.style.color='red'" onmouseout="this.style.color='black'">
  Move the mouse pointer over this text to change its color. Move the pointer off the text to change the color back.
</p>
```

```html
<img src="http://placehold.it/350x150">
<img src="http://placehold.it/350x150" onmouseover="this.src='http://placehold.it/350x150/ffffff/000000'" onmouseout="this.src='http://placehold.it/350x150'">
```

### :books: 參考網站：
- https://msdn.microsoft.com/en-us/library/ms536949(v=vs.85).aspx


---

```html
<!DOCTYPE html>
<html>
  <head>
    <title>getElementById example</title>
    <script>
      function changeColor(newColor) {
        var elem = document.getElementById("para1");
        elem.style.color = newColor;
      }
    </script>
  </head>

  <body>
    <p id="para1">Some text here</p>
    <button onclick="changeColor('blue');">blue</button>
    <button onclick="changeColor('red');">red</button>
  </body>
</html>
```

```html
<!doctype html>
<html>
  <head>
    <meta charset="UTF-8">
    <title>Document</title>
  </head>

  <body>
    <div id="parent-id">
      <p>hello word1</p>
      <p id="test1">hello word2</p>
      <p>hello word3</p>
      <p>hello word4</p>
    </div>
    <script>
      var parentDOM = document.getElementById("parent-id");
      var test1 = parentDOM.getElementById("test1");
      //throw error
      //Uncaught TypeError: parentDOM.getElementById is not a function
    </script>
  </body>
</html>
```


### :books: 參考網站：
- [getElementById](https://developer.mozilla.org/en-US/docs/Web/API/Document/getElementById)
- [for...in](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Statements/for...in)


---

### :books: 參考網站：
- [colorDepth](https://developer.mozilla.org/en-US/docs/Web/API/Screen/colorDepth)
- [width](https://developer.mozilla.org/en-US/docs/Web/API/Screen/width)

```js 
var myCar = {}; // 物件 (Object)
var myCar = new Object(); // 物件 (Object)
```

objectName.propertyName

```js 
myCar.make = "Ford"; // 屬性 (Property)
myCar.model = "Mustang"; // 屬性 (Property)
myCar.year = 1969; // 屬性 (Property)

myCar["make"] = "Ford"; // 屬性 (Property)
myCar["model"] = "Mustang"; // 屬性 (Property)
myCar["year"] = 1969; // 屬性 (Property)
```

```js
var myCar = {
  'make': 'Ford',
  'model': 'Mustang',
  'year': 1969
};
```

```js
console.log(myCar.make);
console.log(myCar);
```

```js
console.log(typeof(myCar));
console.log(typeof(myCar.make));
console.log(typeof(myCar.year));
```
