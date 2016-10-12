
最後更新： 2015-08-21          


```console
shell> npm install request
shell> npm install progress
```

```js
const request = require('request');
request('http://www.google.com', function (error, response, body) {
  if (!error && response.statusCode == 200) {
    console.log(body) // Show the HTML for the Google homepage. 
  }
})
```
```js
const request = require('request');
const ProgressBar = require('progress');
const fs = require('fs');

var req = request('http://nodejs.org/dist/v0.10.28/node.exe');
var bar;

req
.on('data', function(chunk) {
  var len = parseInt(res.headers['content-length'], 10);
  bar = new ProgressBar('  downloading [:bar] :percent :etas', {
    complete: '=',
    incomplete: ' ',
    width: 20,
    total: len
  });
  bar.tick(chunk.length);
})
.on('end', function(err) {
    console.log(err)
})

```

### :books: 參考網站：

- [request](https://www.npmjs.com/package/request)
- [progress](https://www.npmjs.com/package/progress)