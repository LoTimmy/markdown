---

```js
<div>
 <label>Name:</label>
 {{input type="text" value=name placeholder="Enter your name"}}
</div>
<div class="text">
<h3>My name is {{name}} and I want to learn Ember!</h3>
</div>

```

### :books: 參考網站：
- [emberjs](http://emberjs.com/)

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

$( "#book" )
  .error(function() {
    alert( "Handler for .error() called." )
  })
  .attr( "src", "missing.png" ).height(145).width(145);





---

### :books: 參考網站：
- [lazyload](http://www.appelsiini.net/projects/lazyload)
- [dummyimage](http://dummyimage.com/)
- [jquery-dateFormat](https://github.com/phstc/jquery-dateFormat)
- [jquery-number](https://github.com/customd/jquery-number)
