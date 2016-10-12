
最後更新： 2016-04-22          

![](http://i.imgur.com/DLXM8Fu.jpg)

![](http://i.imgur.com/awT9YJm.png)
![](http://i.imgur.com/ilXr55d.gif)

https://github.com/argon/node-apn
https://github.com/ToothlessGear/node-gcm
https://github.com/NodeRedis/node_redis
https://github.com/petkaantonov/bluebird
https://github.com/substack/node-mkdirp
https://github.com/request/request
https://github.com/expressjs/serve-favicon
https://nodejs.org/api/util.html#util_util
https://github.com/ctavan/node-validator
https://github.com/coopernurse/node-pool
https://github.com/pvorb/node-md5

http://pomelo.netease.com/
https://github.com/NetEase/pomelo-globalchannel-plugin
https://www.npmjs.com/package/pomelo-logger
https://github.com/NetEase/pomelo-monitor




RackTables
- [racktables](http://racktables.org/)


- [ocsinventory-ng](http://www.ocsinventory-ng.org/en/)
- [glpi-project](http://www.glpi-project.org/?lang=en)

http://download-cf.jetbrains.com/webstorm/WebStorm-10.0.4.exe

```js
function foo(x, y, z) {
  bar(1, b);
  var i = 0;
  var x = {0: "zero", 1: "one"};
  var a = [0, 1, 2];
  var foo = function () {
  }
  if (!i > 10) {
    for (var j = 0; j < 10; j++) {
      switch (j) {
        case 0:
          value = "zero";
          break;
        case 1:
          value = "one";
          break;
      }
      var c = j > 5 ? "GT 5" : "LE 5";
    }
  } else {
    var j = 0;
    try {
      while (j < 10) {
        if (i == j || j > 5) {
          a[j] = i + j * 12;
        }
        i = (j << 2) & 4;
        j++;
      }
      do {
        j--;
      } while (j > 0)
    } catch (e) {
      alert("Failure: " + e.message);
    } finally {
      reset(a, i);
    }
  }
}
```

---

```js
var shortid = require('shortid');
 
console.log(shortid.generate());
//PPBqWA9 
```

- [shortid](https://www.npmjs.com/package/shortid)

```js
var phonetic = require('phonetic');

phonetic.generate();
// "Stratulis"
phonetic.generate();
// "Quibapop"
```

- [phonetic](https://www.npmjs.com/package/phonetic)

---

https://github.com/chilts/node-coupon-code
```js
var cc = require('coupon-code');

// generate a 3 part code
cc.generate();
=> '55G2-DHM0-50NN'

// generate a 4 part code
cc.generate({ parts : 4 });
=> 'U5H9-HKDH-8RNX-1EX7'

// generate a code with partLen of 6
cc.generate({ partLen : 6 });
=> WYLKQM-U35V40-9N84DA
```



https://github.com/IonicaBizau/match.js


---

![](http://i.imgur.com/XNOpeMw.png)
![](http://i.imgur.com/tHTKvDF.png)


- `Agile Development`: 有效率的溝通，做最有價值的事
- `Continuous Integration`: 自動化測試，自動化建置，讓重覆的事情可以自動執行
- `Continuous Delivery`: 讓專案可以自動發布，隨時有穩定版本可以運作，加速 test 驗證
- `DevOps`: 確保運行環境正常，負責將上述各個機制建置及維護，還有一旦 production deploy 之後的維運。


- [](http://www.ithome.com.tw/guest-post/98457)



---
MVC
![](http://i.imgur.com/hAOxMXT.png)

![](http://i.imgur.com/v8AMbYT.png)

![](http://i.imgur.com/PIJ0rYS.png)

![](http://i.imgur.com/BrEuAsx.png)
---
- [stepify](https://www.npmjs.com/package/stepify)

```js
```
---

```console
shell> 
```

```js
var nanoId = require('nano-id');
 
console.log(nanoId(13));
// → ZyLYucKjwBngU 

console.log(nanoId.verify('it4wVGtjvm'));
// → true 

```

```js
var fs = require('fs');
var officegen = require('officegen');

var xlsx = officegen('xlsx');
xlsx.name = 'My Excel Data';

var sheet = xlsx.makeNewSheet();
sheet.name = 'My Excel Data';


sheet.setCell('E7', 340);
sheet.setCell('G102', 'Hello World!');

sheet.data[0] = [];
sheet.data[0][0] = 1;
sheet.data[0][1] = 2;
sheet.data[1] = [];
sheet.data[1][3] = 'abc';

var out = fs.createWriteStream('out.xlsx');
xlsx.generate(out);

```

```js
var zpipe = require("zpipe");
 
var deflated = zpipe.deflate("the balloon");
var inflated = zpipe.inflate(deflated); 
```

```js
var chalk = require('chalk');

// style a string 
chalk.blue('Hello world!');

// combine styled and normal strings 
chalk.blue('Hello') + 'World' + chalk.red('!');

```

```
http://cachefly.cachefly.net/100mb.test
http://cachefly.cachefly.net/10mb.test
```


[cdnjs](https://cdnjs.com/)

---

`格林威治標準時間`「`GMT`」(`Greenwich Mean Time`)
由於地球每天自轉並不均勻的影響，傳統由英國格林威治天文台，觀測太陽穿越格林威治上空的時間來作為基準的計算方式早已有偏差，科學家希望能有更加精準的計算方式。

事實上，目前我們電腦校時的標準，是根據國際度量衡局提出以「`原子鐘時間`」和「`格林威治時間`」折衷的辦法，稱作「`國際協調標準時間`」，也就是「`UTC`」，只是大家習慣上還是會稱為`GMT`。而這個「`UTC`」的縮寫也已經是英國人與法國人大吵一架的協調結果，原因是這個法文原名是「Temps Universel Cordonne」，應縮寫成「TUC」；而英文則是「Coordinated Universal Time」，應縮寫成「CUT」，後來雙方各讓一步，才縮寫成「UTC」。

### :books: 參考網站：

- [格林威治標準時間恐被廢　英法度量衡爭議再起](http://www.appledaily.com.tw/realtimenews/article/international/20111002/78220/applesearch/%E6%A0%BC%E6%9E%97%E5%A8%81%E6%B2%BB%E6%A8%99%E6%BA%96%E6%99%82%E9%96%93%E6%81%90%E8%A2%AB%E5%BB%A2%E3%80%80%E8%8B%B1%E6%B3%95%E5%BA%A6%E9%87%8F%E8%A1%A1%E7%88%AD%E8%AD%B0%E5%86%8D%E8%B5%B7)

---

<kbd>Ctrl</kbd>+<kbd>C</kbd>
<kbd>Ctrl</kbd>+<kbd>V</kbd>

---

### :books: 參考網站：


- [node-mysql](https://github.com/felixge/node-mysql/)
- [knexjs](http://knexjs.org/)
- [string.format](https://www.npmjs.com/package/string.format)

- [Response_codes](https://developer.mozilla.org/en-US/docs/Web/HTTP/Response_codes)
- [sql-database-develop-nodejs-simple-windows](https://azure.microsoft.com/en-us/documentation/articles/sql-database-develop-nodejs-simple-windows/)
- [node-netstat](https://www.npmjs.com/package/node-netstat)
- [nano-id](https://www.npmjs.com/package/nano-id)
- [get-server-port](https://www.npmjs.com/package/get-server-port)
- [officegen](https://www.npmjs.com/package/officegen)
- [zpipe](https://www.npmjs.com/package/zpipe)
- [commander](https://www.npmjs.com/package/commander)

- [taipei-mrt](https://www.npmjs.com/package/taipei-mrt)
- [chalk](https://www.npmjs.com/package/chalk)
- [multistream](https://www.npmjs.com/package/multistream)
- [romanize-names](https://www.npmjs.com/package/romanize-names)
- [addrtozip](https://www.npmjs.com/package/addrtozip)
- [string-table-fixed-chinese](https://www.npmjs.com/package/string-table-fixed-chinese)
- [cli-table-zh](https://www.npmjs.com/package/cli-table-zh)
- [health-monitor](https://www.npmjs.com/package/health-monitor)
- [validatejs](http://validatejs.org/)

- [Controlling_DNS_prefetching](https://developer.mozilla.org/en-US/docs/Web/HTTP/Controlling_DNS_prefetching)
- [dns-prefetching](http://www.chromium.org/developers/design-documents/dns-prefetching)
- [PreResolveDns](https://developers.google.com/speed/pagespeed/service/PreResolveDns)