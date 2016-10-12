上次更新日期： 2016/06/29   

---

```console
shell> npm install exit
```

package.json
```json
{
  "name": "application-name",
  "version": "0.0.1",
  "private": true,
  "scripts": {
    "start": "node app.js"
  }
}
```

```js
//  Created by Timmy on 2015/2/24.
//  Copyright (c) 2015年 Timmy. All rights reserved.
'use strict';

// 导入所需模块
```


```js
//  Created by Timmy on 2016/06/29.
//  Copyright (c) 2015年 Timmy. All rights reserved.
'use strict';

// 导入所需模块
var exit = require('exit');
 
// These lines should appear in the output, EVEN ON WINDOWS. 
console.log("omg");
console.error("yay");
 
// process.exit(5); 
exit(5);
 
// These lines shouldn't appear in the output. 
console.log("wtf");
console.error("bro");
```

---

### :books: 參考網站：
- [exit](https://www.npmjs.com/package/exit)