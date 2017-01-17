<img src="http://i.imgur.com/diUQ0Gl.png" width="200">
<img src="http://i.imgur.com/Ovy92WP.png" width="200">

# Table of Contents

:blue_book:
- [doctype](#doctype)
- [script](#script)
- [css](#css)
- [meta](#meta)
- [video](#video)

---

```
MyWebsite/
  |--css/
  |  |--style.css <-- compiled from scss/style.scss
  |
  |--images/
  |
  |--js/
  |  |--materialize.js
  |
  |--scss/
  |  |--style.scss
  |  |--components/
  |
  |--index.html
```

---
`video`<a name="video"></a>

```html
<video width="480" controls poster="https://archive.org/download/WebmVp8Vorbis/webmvp8.gif">
  <source src="https://archive.org/download/WebmVp8Vorbis/webmvp8.webm" type="video/webm">
  <source src="https://archive.org/download/WebmVp8Vorbis/webmvp8_512kb.mp4" type="video/mp4">
  <source src="https://archive.org/download/WebmVp8Vorbis/webmvp8.ogv" type="video/ogg"> Your browser doesn't support HTML5 video tag.
</video>

<video controls>
  <source src="somevideo.webm" type="video/webm">
  <source src="somevideo.mp4" type="video/mp4">
  I'm sorry; your browser doesn't support HTML5 video in WebM with VP8/VP9 or MP4 with H.264.
  <!-- You can embed a Flash player here, to play your mp4 video in older browsers -->
</video>

<video src="assets/launch.m4v" controls webkit-playsinline ad-outlet="video"></video>
```

`WebM`
`video/webm`
`audio/webm`

`Ogg Theora Vorbis`
`audio/ogg`
`video/ogg`
`application/ogg`


```
preload
autoplay
controls
height
width
src
poster
loop
muted
playsinline
```

- [video](https://developer.mozilla.org/en-US/docs/Web/HTML/Element/video)
- [video](https://developer.mozilla.org/en-US/docs/Web/HTML/Supported_media_formats)
- https://developer.apple.com/library/content/documentation/AudioVideo/Conceptual/Using_HTML5_Audio_Video/Introduction/Introduction.html#//apple_ref/doc/uid/TP40009523
- https://developer.apple.com/library/content/documentation/UserExperience/Conceptual/iAdJSProgGuide/PlayingVideosinAds/PlayingVideosinAds.html
- [video](https://msdn.microsoft.com/zh-tw/library/hh924820(v=vs.85).aspx)

---

`doctype`<a name="doctype"></a>

```html
<!doctype html>
<!DOCTYPE html>
<!DOCTYPE html public "-//W3C//DTD HTML 4.0//en">
<!DOCTYPE html public "-//W3C//DTD HTML 4.0 Strict//en">
<!DOCTYPE html public "-//W3C//DTD HTML 4.0 Transitional//en">
<!DOCTYPE html public "-//W3C//DTD HTML 4.0 Transitional//en" "http://www.w3.org/TR/html4/loose.dtd">
```

### :books: 參考網站：
- [!DOCTYPE](https://msdn.microsoft.com/zh-tw/library/ms535242(v=vs.85).aspx)

---

```html
<html lang="en"> </html>
<html lang="en-US"> </html>

<head> </head>
<title>Untitled</title>
<title>The Title of the Page</title>
```

---

```html
<link rel="stylesheet" href="//maxcdn.bootstrapcdn.com/bootstrap/3.3.2/css/bootstrap.min.css">
<link rel="stylesheet" href="//maxcdn.bootstrapcdn.com/bootstrap/3.3.2/css/bootstrap-theme.min.css">

<script src="https://ajax.googleapis.com/ajax/libs/jquery/1.11.3/jquery.min.js"></script>
<script src="//maxcdn.bootstrapcdn.com/bootstrap/3.3.2/js/bootstrap.min.js"></script>

<link href="//netdna.bootstrapcdn.com/font-awesome/3.1.1/css/font-awesome.css" rel="stylesheet">
<link rel="stylesheet" href="https://maxcdn.bootstrapcdn.com/font-awesome/4.4.0/css/font-awesome.min.css">

```

---

`script`<a name="script"></a>

```html
<!-- HTML4 and (x)HTML -->
<script type="text/javascript" src="javascript.js"></script>

<!-- HTML5 -->
<script src="javascript.js"></script>

```

```html
<script type="text/javascript">	</script>
<script> </script>
<noscript> </noscript>
<noscript><p class="center">Dropbox 網站需啟用 JavaScript。</p></noscript>    
<script src="//www.google-analytics.com/analytics.js"></script>	
<script src="script.js"></script>	
<script src="/static/javascript/external/zxcvbn.js" type="text/javascript" async></script>	
<script src="/static/javascript/external/zxcvbn.js" type="text/javascript" defer></script>	

<a onclick="alert("Hello world!")" href="javascript:;"></a>
```

### :books: 參考網站：
- [script](https://developer.mozilla.org/en-US/docs/Web/HTML/Element/script)
- [alert](https://developer.mozilla.org/en-US/docs/Web/API/Window/alert)

---
`css`<a name="css"></a>

```html
<link rel="shortcut icon" href="https://www.example.com/H3nktOa7ZMg.ico">	
<link rel="Shortcut Icon" href="/H3nktOa7ZMg.ico" type="image/x-icon">	
<link rel="icon" type="image/png" href="assets/i/favicon.png">
<link href="https://www.example.com/CqvycaYb5lt.png" rel="apple-touch-icon">	
<link type="text/css" rel="stylesheet" href="https://www.example.com/style.css">	

<link href='https://fonts.googleapis.com/css?family=Love+Ya+Like+A+Sister' rel='stylesheet' type='text/css'>

<!-- Include the CSS -->
<link rel="stylesheet" href="style.css">	
<link rel="stylesheet" type="text/css" href="//www.example.com/style.css" media="all">	

<!-- Add to homescreen for Chrome on Android -->
<meta name="mobile-web-app-capable" content="yes">
<link rel="icon" sizes="192x192" href="assets/i/app-icon72x72@2x.png">

<!-- Add to homescreen for Safari on iOS -->
<meta name="apple-mobile-web-app-capable" content="yes">
<meta name="apple-mobile-web-app-status-bar-style" content="black">
<meta name="apple-mobile-web-app-title" content="Amaze UI"/>
<link rel="apple-touch-icon-precomposed" href="assets/i/app-icon72x72@2x.png">

<!-- Tile icon for Win8 (144x144 + tile color) -->
<meta name="msapplication-TileImage" content="assets/i/app-icon72x72@2x.png">
<meta name="msapplication-TileColor" content="#0e90d2">

<style>	</style>
```

---
`meta`<a name="meta"></a>

```html
<meta charset="utf-8">
<meta name="en:locale" content="zh_TW">

<meta name="robots" content="noodp, noydir">
<meta name="robots" content="noodp">

<meta name="robots" content="noindex,nofollow">
<meta name="googlebot" content="noindex,nofollow">

<meta name="robots" content="noindex">
<meta name="googlebot" content="noindex">

<meta name="description" content="">
<meta name="description" content="A description of the page" />

<meta name="author" content="">

<meta name="viewport" content="width=device-width">
<meta name="viewport" content="initial-scale=1">
<meta name="viewport" content="width=500, initial-scale=1">
<meta name="viewport" content="initial-scale=1, maximum-scale=1">
<meta name="viewport" content="width=device-width, initial-scale=1">
<meta name="viewport" content="width=320; initial-scale=1.0; user-scalable=no;">

<meta name="HandheldFriendly" content="true">
<meta name="MobileOptimized" content="{device-width-in-pixels}" />

<meta name="title" content="">

<meta content="text/html; charset=UTF-8" http-equiv="content-type">
<meta http-equiv="Content-Type" content="text/html; charset=utf-8" />
<meta http-equiv="Content-Type" content="text/html; charset=UTF-8">

<meta content="" name="description">

<meta http-equiv="X-UA-Compatible" content="IE=Edge">
<meta http-equiv="X-UA-Compatible" content="IE=edge,chrome=1">
<meta http-equiv="refresh" content="0;url=pages/index.html">

<meta name="google" content="notranslate" />

<!-- Set render engine for 360 browser -->
<meta name="renderer" content="webkit">

<!-- No Baidu Siteapp-->
<meta http-equiv="Cache-Control" content="no-siteapp" />
```

### :books: 參考網站：
- [可讓 Google 識別的中繼標記](https://support.google.com/webmasters/answer/79812?hl=zh-Hant)
- [Viewport_meta_tag](https://developer.mozilla.org/en-US/docs/Mozilla/Mobile/Viewport_meta_tag)
- [HandheldFriendly](https://developer.blackberry.com/playbook/html5/documentation/handheldfriendly.html)
- [viewport](https://developer.blackberry.com/playbook/html5/documentation/viewport.html)
- http://www.ibm.com/support/knowledgecenter/SS4SHV_7.0.0/com.volantis.mcs.eclipse.doc/wag/wag_meta_viewport.html
- https://support.google.com/webmasters/answer/93710?hl=zh-Hant

---

<img src="http://ogp.me/logo.png" width="200">

`opengraph`<a name="opengraph"></a>

```html
<meta property="og:type" content="article" />
<meta property="og:type" content="video.movie" />
<meta property="og:type" content="book" />

<meta property="og:title" content="Introducing our New Site" />
<meta property="og:description" content="http://samples.ogp.me/390580850990722" />
<meta property="og:type" content="article" />
<meta property="og:image" content="https://scontent-sea1-1.xx.fbcdn.net/hphotos-xap1/t39.2178-6/851565_496755187057665_544240989_n.jpg" />
<meta property="og:url" content="http://newsblog.org/news/136756249803614" />
```

```html
<meta property="og:url" content="http://www.imdb.com/title/tt2562232/" />
<meta property='og:image' content="https://images-na.ssl-images-amazon.com/images/M/MV5BODAzNDMxMzAxOV5BMl5BanBnXkFtZTgwMDMxMjA4MjE@._V1_UY1200_CR90,0,630,1200_AL_.jpg" />
<meta property='og:type' content="video.movie" />
<meta property='og:title' content="Birdman or (The Unexpected Virtue of Ignorance) (2014)" />
<meta property='og:site_name' content='IMDb' />
<meta property="og:description" content="Directed by Alejandro G. Inarritu.  With Michael Keaton, Zach Galifianakis, Edward Norton, Andrea Riseborough. Illustrated upon the progress of his latest Broadway play, a former popular actor's struggle to cope with his current life as a wasted actor is shown."
/>
```

![Imgur](http://i.imgur.com/DXvQWTV.png)

### :books: 參考網站：
- [Open Graph protocol](http://ogp.me/)
- [opengraph](https://developers.facebook.com/docs/sharing/opengraph)

---

```css
list-style-type: disc;
list-style-type: circle;
list-style-type: square;
list-style-type: decimal;
list-style-type: georgian;
list-style-type: cjk-ideographic;
list-style-type: kannada;
```

<a href="https://jsfiddle.net/grpkdp33/"><img src="http://i.imgur.com/A9cwqLx.png" width="50"></a>

```html
<ul>
  <li></li>
</ul>

<ul style="list-style-type: square;">
  <li>Item 1</li>
  <li>Item 2</li>
</ul>

<ul style="list-style-type: decimal;">
  <li>Item 1</li>
  <li>Item 2</li>
</ul>

<ul style="list-style-type: decimal-leading-zero;">
  <li>Item 1</li>
  <li>Item 2</li>
</ul>

<ul style="list-style-type: lower-alpha;">
  <li>Item 1</li>
  <li>Item 2</li>
</ul>

<ul style="list-style-type: upper-alpha;">
  <li>Item 1</li>
  <li>Item 2</li>
</ul>

<ul style="list-style-type: lower-roman;">
  <li>Item 1</li>
  <li>Item 2</li>
</ul>

<ul style="list-style-type: trad-chinese-formal;">
  <li>Item 1</li>
  <li>Item 2</li>
</ul>

<ul style="list-style-type: trad-chinese-informal;">
  <li>Item 1</li>
  <li>Item 2</li>
</ul>
```

### :books: 參考網站：
- [list-style-type](https://developer.mozilla.org/en-US/docs/Web/CSS/list-style-type)
- [list-style](https://developer.mozilla.org/en-US/docs/Web/CSS/list-style)
- [list-style-image](https://developer.mozilla.org/en-US/docs/Web/CSS/list-style-image)
- https://msdn.microsoft.com/zh-tw/library/1f6ss9cc(v=vs.100).aspx

---

```html
<option selected="" value="">請擇一</option>
<option selected="" value="">Select one</option>

<body> </body>
<div> </div>
<div id="clickme"> </div>

<h1>Hello, world!</h1>
<h2> </h2>

<span> </span>
<label>	</label>
<textarea> </textarea>
<button> </button>
<br>
<br />
<p>	</p>
<b>	</b>
<i>	</i>
<img src="mygraphic.bmp">	
<img src="large.png" width="20">
	
<tbody>	</tbody>
<thead>	</thead>
<tr> </tr>
<th> </th>
	
<a href="" target="_blank">	</a>
<a href="">	</a>

class=""
id="myDiv"
```

---
`form`<a name="form"></a>

```html
<form> </form>

<form name="aspnetForm" method="post" action="Search.aspx" id="aspnetForm">
</form>

<FORM METHOD="Get" ACTION="Profile.asp"> 
  <INPUT TYPE="Text" NAME="FirstName">  
  <INPUT TYPE="Text" NAME="LastName"> 
  <INPUT TYPE="Text" NAME="Age"> 
  <INPUT TYPE="Hidden" NAME="UserStatus" VALUE="New"> 
  <INPUT TYPE="Submit" VALUE="Enter"> 
</FORM> 

<FORM NAME="Button Example" METHOD="POST" ACTION="button.asp">
  <H3>Computer Programming Experience:</H3>
  <p>
    <INPUT TYPE="RADIO" NAME="choice" VALUE="Less than 1"> Less than 1 year.
    <BR>
    <INPUT TYPE="RADIO" NAME="choice" VALUE="1 to 5"> 1-5 years.
    <BR>
    <INPUT TYPE="RADIO" NAME="choice" VALUE="More than 5"> More than 5 years.
    <BR>
  </p>
  <p>
    <INPUT TYPE="SUBMIT" VALUE="Submit">
    <INPUT TYPE="RESET" VALUE="Clear Form">
  </p>
</form>

<input id="username" maxlength="64" name="username" type="text">
<input id="password" maxlength="64" name="password" type="password">

<input placeholder="Email address" type="email">
<input placeholder="Username" type="text">
<input placeholder="Password" type="password">

<input type="text" id="customerName" name="customerName" maxlength="50" size="30" tabindex="1" value="" autocomplete="off">	
<input type="email" id="email" name="email" maxlength="64" size="30" tabindex="3" value="" autocorrect="off" autocapitalize="off">	

<input type="email" id="inputEmail" class="form-control" placeholder="Email address" required autofocus>
<input type="password" id="inputPassword" class="form-control" placeholder="Password" required>
```
---

<a href="https://jsfiddle.net/y9po4nxv/"><img src="http://i.imgur.com/A9cwqLx.png" width="50"></a>

```html
<!DOCTYPE HTML>
<html lang="en">
  <head>
    <title>Untitled</title>
    <meta http-equiv="Content-Type" content="text/html; charset=utf-8" />
    <meta http-equiv="Cache-Control" content="no-cache">
    <meta http-equiv="Pragma" content="no-cache">
    <meta http-equiv="Expires" content="-1" />
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <meta http-equiv="X-UA-Compatible" content="IE=edge,chrome=1">
  </head>

  <body>
    <div class="container">

      <form class="form-inline">
        <div class="form-group">
          <span>Email:</span>
          <input tabindex="1" maxlength="100" class="form-control" name="email" id="email" origvalue="myname@example.com" value="myname@example.com">
        </div>
        <br />
        <br />
        <div class="form-group">
          <span>Login:</span>
          <input class="form-control" tabindex="3" maxlength="50" name="loginName" id="loginName" origvalue="loginName" value="loginName">
        </div>
        <br />
        <br />
        <div class="form-group">
          <select class="form-control" id="myselect">
            <option value="1">01 - January</option>
            <option value="2">02 - February</option>
            <option value="3">03 - March</option>
            <option value="4">04 - April</option>
            <option value="5">05 - May</option>
            <option value="6">06 - June</option>
            <option value="7">07 - July</option>
            <option value="8">08 - August</option>
            <option value="9">09 - September</option>
            <option value="10">10 - October</option>
            <option value="11">11 - November</option>
            <option value="12">12 - December</option>
          </select>
        </div>
      </form>
      <br />
      <br />
      <button type="submit" class="btn btn-default" id="btn">btn</button>
    </div>
    <!--Load the AJAX API-->
    <script src="https://ajax.googleapis.com/ajax/libs/jquery/1.11.3/jquery.min.js"></script>
    <!-- Latest compiled and minified JavaScript -->
    <script src="https://maxcdn.bootstrapcdn.com/bootstrap/3.3.5/js/bootstrap.min.js" integrity="sha512-K1qjQ+NcF2TYO/eI3M6v8EiNYZfA95pQumfvcVrTHtwQVDG+aHRqLi/ETn2uB+1JqwYqVG3LIvdm9lj6imS/pQ==" crossorigin="anonymous"></script>

    <script type="text/javascript">
      // execute when the HTML file's (document object model: DOM) has loaded
      $(document).ready(function() {});

      $("#btn").click(function() {
        // alert( $( "#myselect option:selected" ).text() );
        alert($("#myselect").val());
      });
    </script>
  </body>
</html>

<!-- Bootstrap core CSS -->
<link rel="stylesheet" href="https://maxcdn.bootstrapcdn.com/bootstrap/3.3.5/css/bootstrap.min.css" integrity="sha512-dTfge/zgoMYpP7QbHy4gWMEGsbsdZeCXz7irItjcC3sPUFtf0kuFbDz/ixG7ArTxmDjLXDmezHubeNikyKGVyQ==" crossorigin="anonymous">

<!-- Optional theme -->
<link rel="stylesheet" href="https://maxcdn.bootstrapcdn.com/bootstrap/3.3.5/css/bootstrap-theme.min.css" integrity="sha384-aUGj/X2zp5rLCbBxumKTCw2Z50WgIr1vs/PFN4praOTvYXWlVyh2UtNUU0KAUhAX" crossorigin="anonymous">

<link rel="stylesheet" href="https://maxcdn.bootstrapcdn.com/font-awesome/4.4.0/css/font-awesome.min.css">
<link rel="stylesheet" type="text/css" href="https://fonts.googleapis.com/css?family=Varela+Round">
```

`data_URIs`

```html
<!DOCTYPE HTML>
<html lang="en">
  <head>
    <style>
    </style>
    <link type="text/css" rel="stylesheet" href="data:text/css;base64,">
  </head>

  <body>
    <img src="mygraphic.png">

    <img src="data:image/png;base64,iVBORw0KGgoAAAANSUhEUgAAAEAAAABACAI
AAAFSDNYfAAAAaklEQVR42u3XQQrAIAwAQeP%2F%2F6wf8CJBJTK9lnQ7FpHGaOurt1
I34nfH9pMMZAZ8BwMGEvvh%2BBsJCAgICLwIOA8EBAQEBAQEBAQEBK79H5RfIQAAAAA
AAAAAAAAAAAAAAAAAAAAAAID%2FABMSqAfj%2FsLmvAAAAABJRU5ErkJggg%3D%3D">

    <a download="mygraphic.png" href="data:image/png;base64,iVBORw0KGgoAAAANSUhEUgAAAEAAAABACAI
AAAFSDNYfAAAAaklEQVR42u3XQQrAIAwAQeP%2F%2F6wf8CJBJTK9lnQ7FpHGaOurt1
I34nfH9pMMZAZ8BwMGEvvh%2BBsJCAgICLwIOA8EBAQEBAQEBAQEBK79H5RfIQAAAAA
AAAAAAAAAAAAAAAAAAAAAAID%2FABMSqAfj%2FsLmvAAAAABJRU5ErkJggg%3D%3D">mygraphic.png</a>
  </body>
</html>
```

### :books: 參考網站：
- [data_URIs](https://developer.mozilla.org/en-US/docs/Web/HTTP/data_URIs)
- [data Protocol](https://msdn.microsoft.com/zh-tw/library/cc848897(v=vs.85).aspx)

---

```html
<pre>
body {
  color: red;
}

a {
  color: green;
}
</pre>
```

### :books: 參考網站：
- [pre](https://developer.mozilla.org/es/docs/Web/HTML/Elemento/pre)

---

```html
<!DOCTYPE html>
<html>
  <head>
    <meta http-equiv="refresh" content="0;url=pages/index.html">
    <title>Untitled</title>
    <script language="javascript">
      window.location.href = "pages/index.html"
    </script>
  </head>

  <body>
    Go to <a href="pages/index.html">/pages/index.html</a>
  </body>
</html>
```

### :books: 參考網站：

- [行動裝置相容性測試](https://www.google.com/webmasters/tools/mobile-friendly/)
- [http-compression-test](http://www.whatsmyip.org/http-compression-test/)
- [fonts](https://developers.google.com/fonts/docs/getting_started)
- [a](https://developer.mozilla.org/en-US/docs/Web/HTML/Element/a)

---

```html
<table id="producttable">
  <thead>
    <tr>
      <td>UPC_Code</td>
      <td>Product_Name</td>
    </tr>
  </thead>
  <tbody>
    <!-- existing data could optionally be included here -->
  </tbody>
</table>

<template id="productrow">
  <tr>
    <td class="record"></td>
    <td></td>
  </tr>
</template>

<script type="text/javascript">
  if ('content' in document.createElement('template')) {
    // Instantiate the table with the existing HTML tbody and the row with the template
    var t = document.querySelector('#productrow'),
      td = t.content.querySelectorAll("td");
    td[0].textContent = "1235646565";
    td[1].textContent = "Stuff";

    // Clone the new row and insert it into the tabledocument.querySelector
    var tb = document.getElementsByTagName("tbody");
    var clone = document.importNode(t.content, true);
    tb[0].appendChild(clone);

    // Create a new row
    td[0].textContent = "0384928528";
    td[1].textContent = "Acme Kidney Beans";

    // Clone the new row and insert it into the table
    var clone2 = document.importNode(t.content, true);
    tb[0].appendChild(clone2);
  } else {
    // Find another way to add the rows to the table because 
    // the HTML template element is not supported.
  }
</script>
```


```html
<link rel="import" href="myfile1.html">
<link rel="import" href="myfile2.html">
```

myfile1.html
```html
<link rel="import" href="jquery.html">
```

myfile2.html
```html
<link rel="import" href="jquery.html">
```

```html
<script src="https://ajax.googleapis.com/ajax/libs/jquery/1.11.3/jquery.min.js"></script>
```

### :books: 參考網站：
- [HTML_Imports](https://developer.mozilla.org/en-US/docs/Web/Web_Components/HTML_Imports)
- [vulcanize](https://github.com/Polymer/vulcanize)

---

### :books: 參考網站：
- [How To  Determine Browser Version from a Script](https://support.microsoft.com/en-us/kb/167820)
- [performance](https://developers.google.com/web/fundamentals/performance/?hl=zh-tw)
- [How do I get the text value of a selected option?](http://learn.jquery.com/using-jquery-core/faq/how-do-i-get-the-text-value-of-a-selected-option/)
- [click](http://api.jquery.com/click/)
- [移除禁止轉譯 JavaScript](https://developers.google.com/speed/docs/insights/BlockingJS?hl=zh-tw)
- [為 CSS 傳送進行最佳化處理](https://developers.google.com/speed/docs/insights/OptimizeCSSDelivery)
- [CSS Sprite Generator](http://spritegen.website-performance.org/)
- [HEAD](https://github.com/joshbuchea/HEAD)


---


- http://placehold.it/60/ffffff/000000
- http://placehold.it/460x250/e67e22/ffffff&text=HTML5
- https://placeholdit.imgix.net/~text?txtsize=75&txt=&w=800&h=300
- https://placeholdit.imgix.net/~text?txtsize=75&txt=800×300&w=800&h=300
- https://placeholdit.imgix.net/~text?txtsize=8&bg=008000&txtclr=000000&txt=&w=60&h=60