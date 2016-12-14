
上次更新日期： 5/19/2016 2:05:01 PM    

```console
shell> npm install moment --save
```

```js
const moment = require('moment');
moment().format();

moment().format('L');    // 11/04/2015
moment().format('dddd');                    // Wednesday
moment("20111031", "YYYYMMDD").fromNow(); // 4 years ago
moment().format("dddd, MMMM Do YYYY, h:mm:ss a"); // "Sunday, February 14th 2010, 3:25:50 pm"


moment.locale('zh-tw');
moment().format('L'); // 2016年5月19日
moment().format('LLLL'); // 2016年5月19日星期四中午11點52分
```

---

### :books: 參考網站：
- [moment](https://www.npmjs.com/package/moment)
- [momentjs](http://momentjs.com/)
- [momentjs](http://momentjs.com/docs/)