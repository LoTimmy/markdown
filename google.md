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


Google 翻譯
```
=GOOGLETRANSLATE("", "zh-CN", "zh-TW")
=GOOGLETRANSLATE("", "ja", "")
=GOOGLETRANSLATE("", "en", "")
=GOOGLETRANSLATE("", "zh-TW", "en")


```
