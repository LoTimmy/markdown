
![](http://i.imgur.com/hSMa5Oy.png)

```css
background: green;
background: yellow;
background-color: #123456;
background-color: #f11;
background-color: blue;
background-color: rgb(15, 99, 30);
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
cursor: pointer;
display: block;
float: left;
font: 11px Verdana, Arial, Helvetica;
font-family: Arial;
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
-moz-border-radius: 10em 0 5em 2em;
-moz-border-radius: 10px;
-moz-box-shadow: 10px 10px 10px #FFFFCC inset;
overflow: hidden;
padding: 10px;
padding: 5px;
padding-top: 10px;
position: absolute;
position: relative;
text-align: center;
text-decoration: line-through;
text-decoration: overline;
text-decoration: underline;
-webkit-border-radius: 10em 0 5em 2em;
-webkit-border-radius: 10px;
-webkit-box-shadow: 10px 10px 10px #FFFFCC inset;
white-space: normal;
white-space: nowrap;
width: 45%;
width: 60px;

a:link { color: #ff0000; text-decoration: none; }
a:visited { color: #990000; text-decoration: none; }
a:active, a:hover { text-decoration: underline; }

.redtext {
  color: #ff0000;
}

```


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
[Learning CSS](https://msdn.microsoft.com/en-us/expression/dd326792.aspx)
[margin](https://msdn.microsoft.com/en-us/library/ms530799(v=vs.85).aspx)
[margin-top](https://msdn.microsoft.com/zh-tw/library/ms530808(v=vs.85).aspx)
[font-family](https://msdn.microsoft.com/zh-tw/library/ms530758(v=vs.85).aspx)
