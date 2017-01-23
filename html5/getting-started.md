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

```
@media only screen and (min-device-width: 375px) and (max-device-width: 667px) { ... }
@media only screen and (min-device-width: 375px) and (max-device-width: 667px) and (orientation: landscape) { ... }
@media only screen and (min-device-width: 375px) and (max-device-width: 667px) and (orientation: portrait) { ... }
```




### :books: 參考網站：
- https://developers.google.com/speed/docs/insights/ConfigureViewport
- https://developer.mozilla.org/en-US/docs/Web/CSS/Media_Queries/Using_media_queries