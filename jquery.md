
### :books: 參考網站：
- https://api.jquery.com/mouseout/
- https://api.jquery.com/css/
---


- [lazyload](#lazyload)

---

```js
jQuery(document).ready(function() {
});

$(document).ready(function() {
});

$(function() {
});
```

### :books: 參考網站：
- [ready](http://api.jquery.com/ready/)

```html
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="utf-8">
  <title>jQuery demo</title>
</head>
<body>
  <!--[if lt IE 9]>
    <script src="jquery-1.9.0.js"></script>
  <![endif]-->
  <!--[if gte IE 9]>
    <script src="jquery-2.0.0.js"></script>
  <!--<![endif]-->
   
  <script src="https://code.jquery.com/jquery-1.10.2.js"></script> 
  <script>
  $(document).ready(function() {
    $("p").text("The DOM is now loaded and can be manipulated.");
  });
  </script>
</body>
</html>
```

```html
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="utf-8">
  <title>load demo</title>
  <style>
  body {
    font-size: 12px;
    font-family: Arial;
  }
  </style>
  <script src="https://code.jquery.com/jquery-1.10.2.js"></script>
</head>
<body>
  <b>Successful Response (should be blank):</b>
  <div id="success"></div><b>Error Response:</b>
  <div id="error"></div>
  <script>
  $("#success").load("/not-here.php", function(response, status, xhr) {
    if (status == "error") {
      var msg = "Sorry but there was an error: ";
      $("#error").html(msg + xhr.status + " " + xhr.statusText);
    }
  });
  </script>
</body>
</html>
```

### :books: 參考網站：
- [load](http://api.jquery.com/load/)

---


ajax/test.html

```html
<ul class="level-1">
  <li class="item-i">I</li>
  <li class="item-ii">II
    <ul class="level-2">
      <li class="item-a">A</li>
      <li class="item-b">B
        <ul class="level-3">
          <li class="item-1">1</li>
          <li class="item-2">2</li>
          <li class="item-3">3</li>
        </ul>
      </li>
      <li class="item-c">C</li>
    </ul>
  </li>
  <li class="item-iii">III</li>
</ul>
```


```js

$.post( "ajax/test.html", function( data ) {
  $( ".result" ).html( data );
});

$.post( "ajax/test.html", function( data ) {
  $( $.parseHTML( data ) ).find( "li" ).css( "background-color", "red" );
});

```

### :books: 參考網站：
- [post](http://api.jquery.com/jQuery.post/)
- [get](https://api.jquery.com/jquery.get/)
- [parseHTML](http://api.jquery.com/jQuery.parseHTML/)
- [find](http://api.jquery.com/find/)

---

```html
<!doctype html>
<html lang="en">
<head>
  <meta charset="utf-8">
  <title>attr demo</title>
  <style>
  p {
    margin: 20px 0 0;
  }
  b {
    color: blue;
  }
  </style>
  <script src="https://code.jquery.com/jquery-1.10.2.js"></script>
</head>
<body>
 
<input id="check1" type="checkbox" checked="checked">
<label for="check1">Check me</label>
<p></p>
 
<script>
$( "input" )
  .change(function() {
    var $input = $( this );
    $( "p" ).html( ".attr( 'checked' ): <b>" + $input.attr( "checked" ) + "</b><br>" +
      ".prop( 'checked' ): <b>" + $input.prop( "checked" ) + "</b><br>" +
      ".is( ':checked' ): <b>" + $input.is( ":checked" ) + "</b>" );
  })
  .change();
</script>
 
</body>
</html>
```

### :books: 參考網站：

- [attr](http://api.jquery.com/attr/)

---


<a name="lazyload"></a>

```html
<script src="jquery.js"></script>
<script src="jquery.lazyload.js"></script>

<img class="lazy" data-original="img/example.jpg" width="640" height="480">

<script>
  $(function() {
  //  $("img.lazy").lazyload();
    $("img.lazy").lazyload({
      effect : "fadeIn"
    });
  });
</script>
```

**Install with Bower**
```console
shell> bower install jquery.lazyload
```

---

```js
$( "div.demo-container" ).text( "<p>This is a test.</p>" );
$( "p" ).text( "<b>Some</b> new text." );

$( "div.demo-container" ).html();

$( "li" ).add( "p" ).css( "background-color", "red" );
$( "p" ).add( "span" ).css( "background", "yellow" );

$( ".inner" ).append( "<p>Test</p>" );

$( "#target" ).click(function() {
  alert( "Handler for .click() called." );
});


$( "p" ).click(function() {
  var htmlString = $( this ).html();
  $( this ).text( htmlString );
});

$( "div.demo-container" )
  .html( "<p>All new content. <em>You bet!</em></p>" );


$.ajax({
  url: "test.html",
  context: document.body
}).done(function() {
  $( this ).addClass( "done" );
});

$.ajax({
  statusCode: {
    404: function() {
      alert( "page not found" );
    }
  }
});

$.ajax({
  method: "POST",
  url: "some.php",
  data: { name: "John", location: "Boston" }
})
  .done(function( msg ) {
    alert( "Data Saved: " + msg );
  });

$.ajax({
  url: "test.html",
  cache: false
})
  .done(function( html ) {
    $( "#results" ).append( html );
  });

$.getJSON( "test.js", function( json ) {
  console.log( "JSON Data: " + json.users[ 3 ].name );
 });


```

<script src="https://gist.github.com/LoTimmy/a59c54a9b903d7c7c5db0cef38a36467.js"></script>


```js
$( "#result" ).load( "ajax/test.html" );
$( "#result" ).load( "ajax/test.html", function() {
  alert( "Load was performed." );
});

```

```js
$( "#result" ).load( "ajax/test.html" );
$( "#result" ).load( "ajax/test.html", function() {
  alert( "Load was performed." );
});

```

---

### :books: 參考網站：
- [lazyload](http://www.appelsiini.net/projects/lazyload)
- [dummyimage](http://dummyimage.com/)
- [jquery-dateFormat](https://github.com/phstc/jquery-dateFormat)
- [jquery-number](https://github.com/customd/jquery-number)
- [jQuery.formError](https://github.com/GarethElms/jQuery.formError)



---

```js
$(function() {
});

```

---

```html
<!doctype html>
<html lang="en">
<head>
  <meta charset="utf-8">
  <title>scrollTop demo</title>
  <style>
  pre {
    height: 600px;
  }
  </style>
</head>
<body>
 
<a href="#" id="header">Header</a>
<pre></pre>
Go to <a href="#header">Header</a>
<pre></pre>
Go to <a href="#header">Header</a>
<pre></pre>
Go to <a href="#header">Header</a>
 
<script src="https://code.jquery.com/jquery-1.10.2.js"></script>
<script src="https://cdnjs.cloudflare.com/ajax/libs/jquery-easing/1.3/jquery.easing.min.js"></script> 
<script>
  $(function() {
    $('a').click(function() {
      $('html,body').animate({
        scrollTop: $('#header').offset().top
      }, 2000, 'easeOutBounce');
	  	
      return false;
    });
  });
</script>
 
</body>
</html>
```

### :books: 參考網站：

- http://gsgd.co.uk/sandbox/jquery/easing/
- [animate](http://api.jquery.com/animate/)
- [offset](http://api.jquery.com/offset/)

---

```
<script src="http://ajax.googleapis.com/ajax/libs/jquery/1/jquery.min.js"></script>
<script src="http://malsup.github.com/jquery.cycle2.js"></script>
```


### :books: 參考網站：
- http://jquery.malsup.com/cycle2/
- http://jquery.malsup.com/cycle2/demo/background.php