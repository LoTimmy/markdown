```html
<script type="text/javascript">
  $.ajax({
    url: 'data/content.xml',
    success: function(xml) {
      // Parse the response
    }
  });
</script>
```

```js
$.ajax({
  dataType: 'mycustomtype',
  dataType: "script",
  dataType: "html",
  dataType: "json",
  dataType: "jsonp",
  dataType: "xml",
  dataType: "text",

  url: "test.html",
  url: "test.js",
  url: "script.php",

  method: "POST",
  method: "GET",

  type: "GET",
  type: "POST",

  data: { name: "John", location: "Boston" },
  data: { id : menuId },

  global: false,

  cache: false,
  success:
  complete:

  success: doSuccess,
  error: doError

  success: function(xml) {
    // Parse the response
  }

});

error_func
```

```js
$.ajax({
  statusCode: {
    404: function() {
      alert("page not found");
    }
  }
});

$.ajax({
  url: "script.php",
  dataType: "json",
  method: "POST",
});

$.ajax({
    method: "POST",
    url: "some.php",
    data: {
      name: "John",
      location: "Boston"
    }
  })
  .done(function(msg) {
    alert("Data Saved: " + msg);
  });

$.ajax({
  url: fileurl,
  type: "GET",
  dataType: "xml",
  complete: xml_ready,
  error: error_func
});
```

```js
$("#target").click(function() {
  // get the value from the username field                              
  var username = $('#username').val();

  // post a JSON payload:
  $.ajax({
    url: "script.php",
    contentType: 'application/json',
    data: JSON.stringify({
      'username': username,
      'location': $("#location").val()
    }),
    method: "POST",
    dataType: "json",
    success: function() {},
    error: function() {},
    complete: function() {}
  });
});


function doSuccess() {
  window.location.href = "";
}

setTimeout(function() {
  window.location.href = "";
}, 2000);

setTimeout(() => {myArray.myMethod()}, 2000);




if(result === "no_errors") location.href = "http://www.example.com/ThankYou.html"


```



```
myArray.myMethod();
arg1
```
---

```html
<!doctype html>
<html lang="en">
  <head>
    <meta charset="utf-8">
    <title>Demo</title>
    <meta name="author" content="">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <link rel="stylesheet" href="_assets/css/style.css">
  </head>

  <body>
    <div id="main">
    </div>
    <script src="_assets/js/ajax.js"></script>
  </body>
</html>
```
---

```html
<input type="button" value="Click Me!" id="my_button" />
```
```js
$("my_button").observe("click", buttonPressed);
```
```css
#my_button { background-color: #999; }
```

```
function buttonPressed() {
    $("my_div").setStyle({
        backgroundColor: "#FF6600",
        fontSize: "12px"
    })
}
```

---


### :books: 參考網站：
- https://api.jquery.com/jquery.ajax/
- https://api.jquery.com/Ajax_Events/
- https://api.jquery.com/click/
- https://api.jquery.com/val/
- https://api.jquery.com/find/
- http://api.jquery.com/ajaxerror/
- https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/JSON/stringify
- https://developer.mozilla.org/en-US/docs/Web/API/WindowOrWorkerGlobalScope/setTimeout
- http://www.ibm.com/developerworks/cn/web/wa-aj-unobtrusive/