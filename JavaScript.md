最後更新： 2016-10-11      

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

- [ipify](https://www.ipify.org/)


- [colorDepth](https://developer.mozilla.org/en-US/docs/Web/API/Screen/colorDepth)
- [width](https://developer.mozilla.org/en-US/docs/Web/API/Screen/width)

```js 
var myCar = {};           // 物件 (Object)
var myCar = new Object(); // 物件 (Object)
```

objectName.propertyName

```js 
myCar.make = "Ford";     // 屬性 (Property)
myCar.model = "Mustang"; // 屬性 (Property)
myCar.year = 1969;       // 屬性 (Property)

myCar["make"] = "Ford";      // 屬性 (Property)
myCar["model"] = "Mustang";  // 屬性 (Property)
myCar["year"] = 1969;        // 屬性 (Property)
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
