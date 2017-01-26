<img src="http://i.imgur.com/diUQ0Gl.png" width="200">


```html
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>Document</title>
</head>
<body>
	
</body>
</html>
```

> 如果要讓行動裝置呈現最佳的顯示效果，建議您在文件標題中加入中繼檢視區，並且為其指定 width=device-width, initial-scale=1 這項參數。

```html
<meta name=viewport content="width=device-width, initial-scale=1">
```
---

<img src="http://i.imgur.com/tgEkCDP.png" width="200">

```
80x80 (avatar)
150x112 (thumbnail)
320x240 (thumbnail)
640x480 (message boards)
800x600 (15-inch monitor)
1024x768 (17-inch monitor)
1280x1024 (19-inch monitor)
1600x1200 (21-inch monitor)
```


```css
/* <= 480px */
@media screen and (max-width: 480px) {
  .example {
    font-size: 16pt;
  }
}

/* <= 768px */
@media screen and (max-width: 768px) {
  .example {
    font-size: 20pt;
  }
}

/* 768px ~ 992px */
@media screen and (min-width: 768px) and (max-width: 992px) {
  .example {
    font-size: 40pt;
  }
}

/* >= 1200px */
@media screen and (min-width: 1200px) {
  .example {
    font-size: 40pt;
  }
}

```

`Portrait` `直向`
`Landscape` `橫向`

`ipad`
```css
@media only screen and (min-device-width: 768px) and (max-device-width: 1024px) { ... }
@media only screen and (min-device-width: 768px) and (max-device-width: 1024px) and (orientation: landscape) { ... }
@media only screen and (min-device-width: 768px) and (max-device-width: 1024px) and (orientation: portrait) { ... }
```

`iPad Pro`
```css
@media only screen and (min-device-width: 1024px) and (max-device-width: 1366px) { ... }
@media only screen and (min-device-width: 1024px) and (max-device-width: 1366px) and (orientation: landscape) { ... }
@media only screen and (min-device-width: 1024px) and (max-device-width: 1366px) and (orientation: portrait) { ... }
```

`Retina 顯示器`
```css
@media only screen and (min-device-width: 768px) and (max-device-width: 1024px) and (-webkit-min-device-pixel-ratio: 2) { ... }
@media only screen and (min-device-width: 768px) and (max-device-width: 1024px) and (orientation: landscape) and (-webkit-min-device-pixel-ratio: 2) { ... }
@media only screen and (min-device-width: 768px) and (max-device-width: 1024px) and (orientation: portrait) and (-webkit-min-device-pixel-ratio: 2) { ... }
```

```css
@media only screen and (min-device-width: 768px) and (max-device-width: 1024px) and (-webkit-min-device-pixel-ratio: 1) { ... }
@media only screen and (min-device-width: 768px) and (max-device-width: 1024px) and (orientation: landscape) and (-webkit-min-device-pixel-ratio: 1) { ... }
@media only screen and (min-device-width: 768px) and (max-device-width: 1024px) and (orientation: portrait) and (-webkit-min-device-pixel-ratio: 1) { ... }
```

`iPhone 6 Plus`
```css
@media only screen and (min-device-width: 414px) and (max-device-width: 736px) { ... }
@media only screen and (min-device-width: 414px) and (max-device-width: 736px) and (orientation: landscape) { ... }
@media only screen and (min-device-width: 414px) and (max-device-width: 736px) and (orientation: portrait) { ... }
```

`iPhone 6`
```css
@media only screen and (min-device-width: 375px) and (max-device-width: 667px) { ... }
@media only screen and (min-device-width: 375px) and (max-device-width: 667px) and (orientation: landscape) { ... }
@media only screen and (min-device-width: 375px) and (max-device-width: 667px) and (orientation: portrait) { ... }
```

`iPhone 5`
```css
@media only screen and (min-device-width: 320px) and (max-device-width: 568px) { ... }
@media only screen and (min-device-width: 320px) and (max-device-width: 568px) and (orientation: landscape) { ... }
@media only screen and (min-device-width: 320px) and (max-device-width: 568px) and (orientation: portrait) { ... }
```

`iPhone 4`
```css
@media only screen and (min-device-width: 320px) and (max-device-width: 480px) { ... }
@media only screen and (min-device-width: 320px) and (max-device-width: 480px) and (orientation: landscape) { ... }
@media only screen and (min-device-width: 320px) and (max-device-width: 480px) and (orientation: portrait) { ... }
```

`SMARTPHONES`
```css
@media (max-width:480px) { ... }
```

`TABLETS`
```css 
@media (min-width:768px) and (max-width:979px) { ... }
```


`SMARTPHONES TO TABLETS`
```css
@media (max-width:767px) { ... }
```

`DEFAULT`
```css
@media (min-width:980px) { ... }
```

### :books: 參考網站：
- https://developers.google.com/speed/docs/insights/ConfigureViewport
- https://developer.mozilla.org/en-US/docs/Web/CSS/Media_Queries/Using_media_queries
- https://developer.mozilla.org/en-US/docs/Learn/CSS/CSS_layout/Grids


```html
<!DOCTYPE html>
<html lang="en">
  <head>
    <meta charset="utf-8">
    <meta http-equiv="X-UA-Compatible" content="IE=edge">
    <meta name="viewport" content="width=device-width, initial-scale=1">
    <title>Document</title>

    <link href="//getbootstrap.com/dist/css/bootstrap.min.css" rel="stylesheet">

    <!--[if lt IE 9]>
      <script src="//oss.maxcdn.com/html5shiv/3.7.2/html5shiv.min.js"></script>
      <script src="//oss.maxcdn.com/respond/1.4.2/respond.min.js"></script>
    <![endif]-->
  </head>
  <body>
    <h1>Hello, world!</h1>

    <script src="//ajax.googleapis.com/ajax/libs/jquery/1.11.3/jquery.min.js"></script>
    <script src="//getbootstrap.com/dist/js/bootstrap.min.js"></script>
  </body>
</html>
```


---

```html
<div id="resizable">
  <div id="items">
    <div>1</div>
    <div>2</div>
    <div>3</div>
    <div>4</div>
    <div>5</div>
  </div>
</div>
```

```css
#resizable {
  border: 1px dashed green;
  min-width: 100px;
  height: 150px;
}

#items div {
  border: 1px solid black;
  background: yellow;
  margin: .3em;
  width: 80px;
  text-align: center;
  float: left;
}

img {
  /* width: 60px; */
  max-width: 100%;
  height: auto;
}
```
