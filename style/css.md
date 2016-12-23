
![](http://i.imgur.com/hSMa5Oy.png)

##### CSS 规则示意图
![](http://www.ibm.com/developerworks/cn/web/1311_huangwh_jqueryhandson/image003.jpg)


要将页面中一个 ID 为 message 的元素的字体颜色设置为蓝色、字体大小设置为 17px
```css
#message {
  color:blue;
  font-size:17px;
}
```
从上述 CSS 规则中可见，我们期望的对元素外观的操作（字体颜色设置为蓝色、字体大小设置为 17px）是通过” color:blue”和”font-size:17px”这 2 个属性声明指定的。而这些操作要作用于哪些元素，则是通过 CSS 的选择器”#message”指定为 ID 等于“message”的元素。


```css
div {
  width: 60px;
  height: 60px;
  margin: 5px;
  float: left;
}

pre, p {
  font-size: 2.5em;
  color: #FE7F88;
  background-color: transparent;
}
```

```html
<style type="text/css">
  div {
    padding: 10px;
  }
</style>
```

---

<a href="https://jsfiddle.net/agmkxp55/"><img src="http://i.imgur.com/A9cwqLx.png" width="50"></a>

```css
.fontSize-18 {
  font-size: 18px;
}

.colorRed {
  color: red;
}
```

```html
<div class="fontSize-18 colorRed">Test Message</div>
```

---

```html
<div style="background-color:blue;"></div>
<div style="background-color:rgb(15,99,30);"></div>
<div style="background-color:#123456;"></div>
<div style="background-color:#f11;"></div>
```

```css
background: green;
background: yellow;

background: url("../img/bg-pattern.png"), #7b4397;
background: url("../img/bg-pattern.png"), -webkit-linear-gradient(to left, #7b4397, #dc2430);
background: url("../img/bg-pattern.png"), linear-gradient(to left, #7b4397, #dc2430);

background-image: none;
background-image: url("http://www.example.com/bck.png");
background-image: inherit;

background-repeat: repeat;
background-repeat: no-repeat;
background-color: #123456;
background-color: #f11;
background-color: red;
background-color: blue;
background-color: lightblue;
background-color: rgb(15, 99, 30);
background-color: transparent;

border: 2px solid green;
border: solid 2px blue;
border-bottom-left-radius: 15px 30px;
border-bottom-left-radius: 2em;
border-bottom-right-radius: 15px 30px;
border-bottom-right-radius: 5em;
border-color: #7f7f7f;
border-radius: 5px;
border-style: dashed;
border-style: solid;
border-top-left-radius: 10em;
border-top-left-radius: 50px 25px;
border-top-left-radius: 50px 30px;
border-top-right-radius: 50px 25px;
border-top-right-radius: 50px 30px;
border-width: 1px;

box-shadow: 0 0 5px 5px sienna;
box-shadow: 5px 5px 5px lightgray;

clear: both;
clear: left;

color: blue;
color: grey;
color: red;
color: rgb(255, 255, 255);
color: yellow;
color: white;

cursor: pointer;

display: none;
display: block;

float: left;
font: 11px Verdana, Arial, Helvetica;
font-family: Arial;
font-family: sans-serif;
font-family: 'Microsoft JhengHei UI', 'Microsoft JhengHei', PMingLiU, MingLiU, 'Segoe UI', 'Lucida Grande', Verdana, Arial, Helvetica, sans-serif;
font-size: 20px;
font-style: italic;
font-weight: bold;
height: 60px;
left: 50px;
line-height: 25px;
list-style: none;

margin: 20px 0px 10px 75%;
margin: 8px;
margin: 0px auto;
margin-left: 3%;
margin-right: 10px;
margin-top: 10px;


max-width: 100%;
max-height: 100%;
max-height: none;

-moz-border-radius: 10em 0 5em 2em;
-moz-border-radius: 10px;
-moz-box-shadow: 10px 10px 10px #FFFFCC inset;
overflow: hidden;
padding: 10px;
padding: 5px;
padding-top: 10px;

position: absolute;
position: relative;
position: fixed;

text-align: center;
text-decoration: line-through;
text-decoration: overline;
text-decoration: underline;

visibility: hidden;
visibility: visible;

/* Content is clipped, with no scrollbars */
overflow-y: hidden;
/* Content is not clipped */
overflow-y: visible;
/* Content is clipped, with scrollbars */
overflow-y: scroll;
/* Let the browser decide */
overflow-y: auto;
/* Global values */
overflow-y: inherit;
overflow-y: initial;
overflow-y: unset;

-webkit-border-radius: 10em 0 5em 2em;
-webkit-border-radius: 10px;
-webkit-box-shadow: 10px 10px 10px #FFFFCC inset;
white-space: normal;
white-space: nowrap;
width: 45%;
width: 60px;
z-index: -1;

a:link { color: #ff0000; text-decoration: none; }
a:visited { color: #990000; text-decoration: none; }
a:active, a:hover { text-decoration: underline; }

.redtext {
  color: #ff0000;
}

```

### :books: 參考網站：
- [max-height](https://developer.mozilla.org/en-US/docs/Web/CSS/max-height)
- [max-width](https://developer.mozilla.org/en-US/docs/Web/CSS/max-width)


---

```html
<style>
@media (max-width: 600px) {
  .facet_sidebar {
    display: none;
  }
}

.show {
  display: block !important;
}
.hidden {
  display: none !important;
}
.invisible {
  visibility: hidden;
}

</style>
```

```html
<head> 
<style>
@media only screen 
  and (min-device-width: 320px) 
  and (max-device-width: 480px) {
    .hidden { display: none; }
}

@media only screen 
  and (min-device-width: 768px) 
  and (max-device-width: 1024px) {
    .hidden { display: none; }
}
</style>
</head>

<div class="show">...</div>
<div class="hidden">...</div>
```

```html
<link rel="stylesheet" media="screen and (max-device-width: 799px)" href="http://foo.bar.com/stylesheet.css" />
```

### :books: 參考網站：
- https://developer.mozilla.org/en-US/docs/Web/CSS/Media_Queries/Using_media_queries
- https://developer.mozilla.org/en-US/docs/Web/CSS/@media
- https://developer.mozilla.org/en-US/docs/Web/CSS/background-repeat
- https://developer.mozilla.org/en-US/docs/Web/CSS/overflow-y

---

```html
<head>
<style>
.vis1 {
   visibility: visible;
}
.vis2 {
   visibility: hidden;
}
</style>
</head>
<body>
   <img id="oSphere" src="sphere.jpg" alt="sphere">
   <p onmouseover="oSphere.className='vis2'" onmouseout="oSphere.className='vis1'">
   Mouseover this text to set visibility to hidden on the image of the sphere.</p>
</body>
```

### :books: 參考網站：
- https://msdn.microsoft.com/zh-tw/library/ms531180(v=vs.85).aspx

---

```css
p { background: #ccccff; border: solid 1px #666699; }
h1 { background: #ccff99; }
```
![](https://i-msdn.sec.s-msft.com/en-us/expression/dd326790.PixieMill04_01(en-us,MSDN.10).gif)

---

![](https://i-msdn.sec.s-msft.com/en-us/expression/dd326790.PixieMill04_02(en-us,MSDN.10).gif)
---

### :books: 參考網站：
- [Learning CSS](https://msdn.microsoft.com/en-us/expression/dd326792.aspx)
- [margin](https://msdn.microsoft.com/en-us/library/ms530799(v=vs.85).aspx)
- [margin-top](https://msdn.microsoft.com/zh-tw/library/ms530808(v=vs.85).aspx)
- [font-family](https://msdn.microsoft.com/zh-tw/library/ms530758(v=vs.85).aspx)
- [background-image](https://developer.mozilla.org/en-US/docs/Web/CSS/background-image)
- [position](https://developer.mozilla.org/en-US/docs/Web/CSS/position)
- [bottom](https://developer.mozilla.org/en-US/docs/Web/CSS/bottom)

---

![Imgur](http://i.imgur.com/WJl0p5y.png)

<a href="https://jsfiddle.net/b4u961fe/"><img src="http://i.imgur.com/A9cwqLx.png" width="50"></a>

```css
#d5ESWAchesut {
  position: absolute;
  background-color: #800080;
  width: 150px;
  height: 150px;
  top: 10px;
  left: 10px;
  z-index: 3;
}

#S2aKEGaMeswu {
  position: absolute;
  background-color: #008000;
  width: 150px;
  height: 150px;
  top: 20px;
  left: 20px;
  z-index: 2;
}

#xeSW8nagutr6 {
  position: absolute;
  background-color: #FF8040;
  width: 150px;
  height: 150px;
  top: 30px;
  left: 30px;
  z-index: 1;
}
```
```html
<div id="d5ESWAchesut"></div>
<div id="S2aKEGaMeswu"></div>
<div id="xeSW8nagutr6"></div>
```


---

![Imgur](http://i.imgur.com/S5v6IzG.png)

<a href="https://jsfiddle.net/vf8euwaa/"><img src="http://i.imgur.com/A9cwqLx.png" width="50"></a>

```css
div {
  background-color: #FF00FF;
  width: 60px;
  height: 60px;
}

p {
  position: relative;
  top: 10px;
  left: 50px;
}
```
```html
<div><p>HelloWorld</p></div>
```

---

<a href="https://jsfiddle.net/r1bhgry3/"><img src="http://i.imgur.com/A9cwqLx.png" width="50"></a>

```css
.w8EpEstevaWr {
  position: fixed;
  bottom: 20px;
  right: 20px;
  width: 100px;
  background-color: red;
}

pre {
  height: 600px;
}
```

```html
<div class="w8EpEstevaWr">HelloWorld</div>

<pre><p> HelloWorld</p><img id="sawezuswePh7" src="http://placehold.it/200x60" alt=""></pre>
<pre><p> HelloWorld</p><img id="sawezuswePh7" src="http://placehold.it/200x60" alt=""></pre>
<pre><p> HelloWorld</p><img id="sawezuswePh7" src="http://placehold.it/200x60" alt=""></pre>
```


---

<a href="https://jsfiddle.net/dcwnbthk/"><img src="http://i.imgur.com/A9cwqLx.png" width="50"></a>

```css
img {
  position: absolute;
  top: 0px;
  left: 0px;
  z-index: 1;
}
```
```html
<p> HelloWorld</p><img id="sawezuswePh7" src="http://placehold.it/200x60" alt="">
```

<a href="https://jsfiddle.net/b92xasu9/"><img src="http://i.imgur.com/A9cwqLx.png" width="50"></a>

```css
img {
  position: absolute;
  top: 0px;
  left: 0px;
  z-index: -1;
}
```


---

<a href="https://jsfiddle.net/yaj5n67j/"><img src="http://i.imgur.com/A9cwqLx.png" width="50"></a>

```css
div {
  position: absolute;
  text-align: center;
  width: 120px;
  height: 100px;
  font-family: sans-serif;
}

.redbox1 {
  background-color: red;
  top: 20px;
  left: 20px;
  z-index: -1;
}

.bluebox1 {
  background-color: lightblue;
  top: 50px;
  left: 40px;
  z-index: 1;
}

.redbox2 {
  background-color: red;
  top: 20px;
  left: 180px;
  z-index: 1;
}

.bluebox2 {
  background-color: lightblue;
  top: 50px;
  left: 200px;
  z-index: -1;
}
```

### :books: 參考網站：
- https://msdn.microsoft.com/zh-tw/library/ms531188.aspx
- https://msdn.microsoft.com/zh-tw/library/ee371254(v=expression.40).aspx 

---

<a href="https://jsfiddle.net/5sn6d0hg/"><img src="http://i.imgur.com/A9cwqLx.png" width="50"></a>

```html
<div id="d5ESWAchesut"></div>
<div id="S2aKEGaMeswu"></div>
```
```css
#d5ESWAchesut {
  background-image: url("http://placehold.it/200x60/e3d454/ffffff");
  width: 400px;
  height: 60px;
  border: solid 1px #666699;
}

#S2aKEGaMeswu {
  background-image: url("http://placehold.it/200x60/e3d454/ffffff");
  background-repeat: no-repeat;
  width: 400px;
  height: 60px;
  border: solid 1px #666699;
  margin-top: 10px;
}
```

---

`Normalize.css`

![](http://necolas.github.io/normalize.css/logo.svg)

### :books: 參考網站：
- [Normalize.css](http://necolas.github.io/normalize.css/)
- https://cdnjs.com/libraries/normalize
- https://necolas.github.io/normalize.css/latest/normalize.css

```console
shell> npm install --save normalize.css
shell> bower install --save normalize-css
```
---

`SVG for Everybody`

### :books: 參考網站：
- [svg4everybody](https://github.com/jonathantneal/svg4everybody)
- [svg4everybody](https://jonathantneal.github.io/svg4everybody/)
---

### :books: 參考網站：
- [Materialize](http://materializecss.com/)
- http://getbootstrap.com/
- [Semantic UI](http://semantic-ui.com/)
- http://susy.oddbird.net/



---

<a href="https://jsfiddle.net/u6bsgrt9/"><img src="http://i.imgur.com/A9cwqLx.png" width="50"></a>

```css
@import url(https://fonts.googleapis.com/earlyaccess/notosanstc.css);
@import url(http://fonts.googleapis.com/earlyaccess/notosanstc.css);
* {
  font-family: 'Noto Sans TC', sans-serif;
}
```

---

```css
@charset "UTF-8";
@charset "iso-8859-15";
```

### :books: 參考網站：
- [@charset](https://developer.mozilla.org/en-US/docs/Web/CSS/@charset)

---

```css
font-family: 'Noto Sans TC', 'Microsoft JhengHei', sans-serif !important;
font-size: 2.5em;
font-weight: 900;
text-shadow: black 0.01em 0.01em 0.05em !important; 
```

### :books: 參考網站：
- [text-shadow](https://developer.mozilla.org/en-US/docs/Web/CSS/text-shadow)
- [Microsoft JhengHei](https://www.microsoft.com/typography/fonts/family.aspx?FID=368)
- [](https://www.microsoft.com/typography/fonts/family.aspx?FID=350)