上次更新日期： 2016-08-30                                                   

---

```html
<!DOCTYPE html>
<html>
  <head>
    <style type="text/css">
      html, body { height: 100%; margin: 0; padding: 0; }
      #map { height: 100%; }
    </style>
  </head>
  <body>
    <div id="map"></div>
    <script type="text/javascript">

var map;
function initMap() {
  map = new google.maps.Map(document.getElementById('map'), {
    center: {lat: -34.397, lng: 150.644},
    zoom: 8
  });
}

    </script>
    <script async defer
      src="https://maps.googleapis.com/maps/api/js?key=YOUR_API_KEY&callback=initMap">
    </script>
  </body>
</html>

```

### :books: 參考網站：
- [Hello, World](https://developers.google.com/maps/documentation/javascript/tutorial?hl=zh-tw#The_Hello_World_of_Google_Maps_v3)

---

![](http://i.imgur.com/5oWbqTd.png)

chrome://settings/

顯示進階設定... → ☑ 在可用時使用硬體加速


Chrome 鍵盤快速鍵

**重新開啟並切換至最近關閉的分頁**	<kbd>⌘</kbd> + <kbd>Shift</kbd> + <kbd>T</kbd>
**切換至特定分頁**	     <kbd>⌘</kbd> + <kbd>1</kbd> 到 <kbd>⌘</kbd> + <kbd>8</kbd> 
**切換至最後一個分頁**      <kbd>⌘</kbd> + <kbd>9</kbd>
**切換至下一個開啟的分頁**	 <kbd>⌘</kbd> + <kbd>Option</kbd> + <kbd>→</kbd>
**切換至上一個開啟的分頁**	 <kbd>⌘</kbd> + <kbd>Option</kbd> + <kbd>←</kbd>
**將視窗縮到最小**	     <kbd>⌘</kbd> + <kbd>M</kbd>
**隱藏 Google Chrome**	<kbd>⌘</kbd> + <kbd>H</kbd>
**退出 Google Chrome**	<kbd>⌘</kbd> + <kbd>Q</kbd>
**向下捲動網頁，每次捲動一個螢幕畫面的範圍**	<kbd>空格鍵</kbd>
**向上捲動網頁，每次捲動一個螢幕畫面的範圍**	<kbd>Shift</kbd> + <kbd>空格鍵</kbd>

**放大網頁上的所有內容** <kbd>⌘</kbd> + <kbd>+</kbd>
**縮小網頁上的所有內容** <kbd>⌘</kbd> + <kbd>-</kbd>
**將網頁上的所有內容都回復為預設大小**	<kbd>⌘</kbd> + <kbd>0</kbd>


<kbd>⌘</kbd> + <kbd>↑</kbd>
<kbd>⌘</kbd> + <kbd>↓</kbd>

### :books: 參考網站：
- [快速鍵](https://support.google.com/chrome/answer/157179?hl=zh-Hant)

---

```
/*
 * cwTeXHei (Chinese-traditional) http://www.google.com/fonts/earlyaccess
 */
@font-face {
  font-family: 'cwTeXHei';
  font-style: normal;
  font-weight: 500;
  src: url(//fonts.gstatic.com/ea/cwtexhei/v3/cwTeXHei-zhonly.eot);
  src: url(//fonts.gstatic.com/ea/cwtexhei/v3/cwTeXHei-zhonly.eot?#iefix) format('embedded-opentype'),
       url(//fonts.gstatic.com/ea/cwtexhei/v3/cwTeXHei-zhonly.woff2) format('woff2'),
       url(//fonts.gstatic.com/ea/cwtexhei/v3/cwTeXHei-zhonly.woff) format('woff'),
       url(//fonts.gstatic.com/ea/cwtexhei/v3/cwTeXHei-zhonly.ttf) format('truetype');
}
```

```css
@import url(http://fonts.googleapis.com/earlyaccess/cwtexhei.css);
```
```
font-family: 'cwTeXHei', sans-serif;
```

### :books: 參考網站：
- [Google Fonts](https://fonts.google.com/)
- [earlyaccess](https://fonts.google.com/earlyaccess)


---


Google 翻譯
```
=GOOGLETRANSLATE("", "zh-CN", "zh-TW")
=GOOGLETRANSLATE("", "ja", "")
=GOOGLETRANSLATE("", "en", "")
=GOOGLETRANSLATE("", "zh-TW", "en")
```

```
=GOOGLEFINANCE("currency:USDTWD")
```