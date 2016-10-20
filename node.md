![](https://raw.githubusercontent.com/docker-library/docs/master/node/logo.png)

上次更新日期： 2016-10-20     

# Table of Contents

- [install](#install)
- [變數 (Variable)](#var)
- [布林值 (Boolean)](#boolean) 
- [函數 (Function)](#function)
- [物件 (Object)](#object)
- [Lambda](#lambda)
- [closure-compiler](#closure-compiler)
- [經過時間](#elapsed)

---

- `JavaScrip`在1995年5月問世。
- `JavaScript`在1996年進行標準化，第一個標準化版本`ECMA-262`於1997年採納，因為`Java`名稱上具有商標問題，`ECMA-262`採用了`ECMAScript`作為語言名稱，`JavaScript`此後成為了`ECMA-262`標準的實作語言，現在的瀏覽器，幾乎都能支援1999年發布的`ECMA-262`第三版以上的實作，又稱`ECMAScript 3`，對應的實作為`JavaScript 1.5`。
> 由於一些政治因素，`ECMAScript 4`發展意見發生分岐，原有規範中的一小部份是就現有功能作了改進，被發布為`ECMAScript 3.1`。後來`ECMAScript 4`被中止，`ECMAScript 3.1`被改名`ECMAScript 5`，並於2009年發布，後續2011年又發布了`ECMAscript 5.1`。
- `ECMAScript 5`的主要特點之一是可宣告`嚴格模式`（`Strict mode`），透過在程式碼中加入'use strict'字串，一些過去被認為不良實踐的語法就會無法使用，嚴格模式下有許多規範，是關於識別字名稱使用上的限制，像是沒有使用var宣告的變數無法使用，不能使用with，不能有重複的參數或特性名稱，不能與保留字或既存的識別字名稱衝突（像是arguments），eval函式評估出來的變數不能在外部使用等，很顯然地，這反映了過去語言在`範疇`（`Scope`）與`名稱空間`（`Namespace`）管理上過於鬆散，因而必須加強範疇與名稱空間管理上的約束。
- 像是`ECMAScript 5`之前，如果this沒有實際對象，也就是this實際上是null或undefined時，會自動轉換為全域物件，這又會造成許多誤判或誤用的問題，嚴格模式下禁止了這個行為，實際上，為了讓開發者能明確掌握this，函式新增了bind函式，可以讓你固定this的對象傳回新函式，讓this不會隨著呼叫者自動變換。在這之前，開發者為了要能更精確掌握this實際對象，避免不清不楚下發生問題，亦會明確地在使用call或apply函式時，指定this的對象。
- `JavaScript`之父`Brendan Eich`（音：艾可，德國姓）。`Brendan Eich`在1995年僅花了10天就開發出`JavaScript`。之所以命名使用了`Java`這四個字母，完全是行銷上考量，他想藉由`Java`的名氣使更多人注意到`JavaScript`。`Brendan Eich`想讓`JavaScript`乍看之下很像是`Java`，但是其實與`Java`非常不一樣。而`Java`和`JavaScript`雖然都屬於物件導向語言，語法和物件的繼承方式卻不同。`Brendan Eich`強調，其中一個很大的差異在於型別，`Java`是靜態型別，也就是說在撰寫`Java`程式碼時，開發者需要先定義變數的型別，`JavaScript`卻不需要，這使得`JavaScript`的程式在開發上，更為彈性且容易，不過這卻也是`JavaScript`的致命傷，動態型別使得`JavaScript`的執行效能受到影響。
- `Java`是由被`Oracle`買下的`Sun`發表，`JavaScript`則是由`Netscape`發表，原本名字叫`LiveScript`，因為`Netscape`在自己的瀏覽器支援`Java Applet`，`Java`又名氣大噪，就把`LiveScript`改名`JavaScript`一起打知名度。而`Netscape`後來把`JavaScript`提交給`ECMA`制定為國際標準，稱做`ECMAScript`，真正跟`JavaScript`是兄弟的是`Adobe Flash`的`ActionScript`和`Microsoft`的`JScript`，因為一樣都是依`ECMAScript`標準建制。
- **`Node.js`是一個可用來開發伺服器端網路應用程式的跨平台運作環境**，允許開發人員以各式`應用程式介面`（`API`）來撰寫應用程式，被視為是全球成長最快的`API`開發框架之一。
- 2009年釋出的`Node.js`為一開放源碼的跨平台運作環境，主要用來開發伺服器端的網路應用程式，包括`IBM`、`微軟`、`Yahoo`、`SAP`、`PayPal`或`GoDaddy`都是Node.js的用戶，雖然在2014年底時，`Node.js`社群因內部意見不合導致有人出走並另創了同類型的`io.js`，不過雙方在今年6月同意透過中立的`Node.js`基金會重新合併，並由`Linux`基金會負責管理。`Node.js 4.0`即是`Node.js`與`io.js`整併後的第一個產品，也是`Node.js`的第一個穩定版，版本別則自7月的0.12.7直接跳到4.0。`Node.js 4.0`採用與最新`Chrome`瀏覽器一致的4.5版V8 `JavaScript`引擎，亦建立了涵蓋`OS X`、`Windows`、`FreeBSD`與`SmartOS`等多種作業系統的測試叢集，並對`ARM`處理器有一流的支援，包含`ARM6`、`ARM7`與最新的64位元`ARM8`等處理器，意味著它已正式準備好要供應給業餘的科技愛好者及`ARM`伺服器用戶來使用。
- `ES6`是`JavaScript`現在2015年標準，與之前版本的語法及概念不同，有相當大的變動。
- 知名開發框架`Node.js`在2014年底鬧內鬨，最後分裂出了`io.js`，歷經了9個月的分手，社群重修舊好，兩個專案再次合併為`Node.js`，並全然納入`io.js`過去更新的程式碼，版本號從0.12一躍到了4.0，在2015年9月時，對外釋出`Node.js 4.0`正式版。這次的更新除了支援新`JavaScript`解析引擎V8外，也支援最新版本`ES6`（`ECMAScript6`）的`JavaScript`規格，另外，`Node.js`也在0.12版開始提供`長期支援`（`Long Term Support`，`LTS`）版本，顯示`Node.js`進入成熟發展階段。由於新版`JavaScript`解析引擎V8完全支援`ES6`的新功能，因此`Node.js`在搶先支援`ES6`後，也開始可以使用諸多`ES6`才有的新特色，像是習慣C++的開發者，在`Node.js`終於能夠使用`類別`（`Class`）。另外，`ES6`還支援了`Generator`，因此新版`Node.js`的開發者可以用更高效率的方法處理遞迴問題。`Node.js`經過一段時間的發展，逐漸趨於成熟與穩定，而提供長期支援版本便是一個重要的指標，因為企業能夠有計畫的掌握版本更新時程，`Node.js`每12個月會釋出一個長期支援版本，而這個版本會被維護18個月。另外，`Node.js 4.0`在效能上也有長足的進步，經國外開發者以`Apache HTTP`伺服器指標工具測試後，發現`Node.js 4.0`能比前一版本少用一半以上的記憶體，但仍維持同樣的效能。
- 網頁語言`JavaScript`不只用於前端網頁，進幾年越來越多伺服器端程式採用`Node.js`框架來開發後端需要的應用程式
- `Node.js`是基於`Google`所開發出名為`V8`的`JavaScript`引擎所創造出來的`Framework`。它特別的地方在於，一般由`JavaScript`開發出來的套件，通常都是應用在網路前端平臺上，像是`jQuery`等，而`Node.js`卻可以用來開發後端的應用程式。以往`JavaScript`都是運行在瀏覽器上，而`Node.js`的出現，可以將`JavaScript`變成一個通用平臺的語言使用，因此可以讓它做任何事情。而`Node.js`在伺服器應用上的效能不錯，反應速度也很快。`Python`及`Ruby`等語言在這方面的效率，就比不上`Node.js`了，而這也是它的優勢。
- `回呼` (`Callback`)，當實作程式出現許多重複流程，僅小部份需要特定實作時，可以將重複流程實作為樣版，而特定實作由呼叫者提供回呼物件或函式，例如對`JavaScript`的陣列排序可以寫為[1, 3, 2, 5, 4].sort(function(a, b) { return a - b; })。
- `NW.js`為一結合`Node.js`與`Chromium`專案的`JavaScript`應用程式開發框架，可用來打造支援`Windows`、`Mac OS X`與`Linux`的應用程式，有別於瀏覽器對`JavaScript`程式碼的沙箱執行限制，`NW.js`移除了相關的限制，並允許程式直接與作業系統互動。`NW.js`除了允許程式在不同的平台上運作之外，也讓開發人員更容易把網路程式轉成桌面程式。
- `NW.js`的最大優勢在於它所需的`.Net`或`Java`運行環境都已經安裝在各個系統上了。

![](https://i-msdn.sec.s-msft.com/dynimg/IC736472.png)

---
<a name="install"></a>

```console
shell> apt-get install nodejs
```

```console
shell> git clone https://github.com/creationix/nvm.git ~/.nvm && cd ~/.nvm && git checkout `git describe --abbrev=0 --tags`
shell> echo "source ~/.nvm/nvm.sh" >> .bashrc

shell> nvm ls-remote
shell> nvm install v0.12.0
shell> nvm install v4.2.2
shell> nvm install v6.1.0

shell> nvm ls
shell> nvm alias default 0.12.0
shell> nvm alias default 4.2.2
```

```console
shell> node --version
v4.1.1
```

**Specifying a Node.js Version**
``` .json
{
  "name": "myapp",
  "description": "a really cool app",
  "version": "1.0.0",
  "private": true,
  "engines": {
    "node": "4.1.1"
  }
}
```

``` .json
"engines": {
  "node": ">= 0.12.0"
}
```

**Specifying an Npm Version**
``` .json
{
  "name": "myapp",
  "description": "a really cool app",
  "version": "0.0.1",
  "private": true,
  "engines": {
    "npm": "2.1.x"
  }
}
```

---
``` .js
'use strict';
```

---
<a name="var"></a>

**變數 (Variable)** 
```js
var a;
var a = 1;
var a = 0, b = 0;

var u = undefined;
var mytext = 'Hello World!';
var mynumber = 99;
var myboolean = true, myFalse = false;
var myFunc = function() {};
var text = null;
var myObj = {}, myobject = { nickname: 'Jack', "registration_date": new Date(1995, 11, 25), "privileged_user": true };
var myarray = [], someArray = [ 1, 2, 3 ];
```

```js
var mynumber = 99;
console.log(`my favorite number is: ${mynumber}`);
```

```js
// define MY_FAV as a constant and give it the value 7
const MY_FAV = 7;

MY_FAV = 20;

// will print 7
console.log("my favorite number is: " + MY_FAV);

var MY_FAV = 20; 

// MY_FAV is still 7
console.log("my favorite number is " + MY_FAV);
```

``` .js
'use strict';

function varTest() {
  var x = 31;
  if (true) {
    var x = 71;  // same variable!
    console.log(x);  // 71
  }
  console.log(x);  // 71
}

function letTest() {
  let x = 31;
  if (true) {
    let x = 71;  // different variable
    console.log(x);  // 71
  }
  console.log(x);  // 31
}
```



- [let](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Statements/let)
- [const](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Statements/const)

---

<a name="boolean"></a>

**布林值 (Boolean)**
``` .js
x = new Boolean(false);
if (x) {
  // this code is executed
}

x = false;
if (x) {
  // this code is not executed
}

x = true;
x = false;
```
---

<a name="function"></a>

**函數 (Function)**
``` .js
function myFunc() {
  console.log("foo");
}

myFunc(); // → "foo"

function calc_sales(units_a, units_b, units_c) {
   return units_a*79 + units_b * 129 + units_c * 699;
}

var mynumber = calc_sales( 1, 2, 3 );
console.log(mynumber);
```
---

<a name="object"></a>

**物件 (Object)**
``` .js
var myObj = new Object();
myObj.nickname = 'Jack';
myObj.registration_date = new Date(1995, 11, 25);
myObj.privileged_user = true; 
```

``` .js
var myObj = new Object();
myObj.name = "Fred";
myObj.count = 42;

delete myObj.name;
delete myObj["count"];

console.log(myObj);  // → {}
```

``` .js
var myObj = new Object();
console.log(myObj);  // → {}

myObj.name = "Fred";
myObj.toString = function() {
  return this.name;
} 

console.log(myObj.toString());  // → "Fred"
 
```
---

陣列 (Array)
``` .js
// Create an array.
var myArray = new Array();

myArray.nickname = 'Jack';
myArray.registration_date = new Date(1995, 11, 25);
myArray.privileged_user = true;
myArray[0] = 'Hello World!';

for (var i in myArray) {
  console.log( i + " = " + myArray[i] );
}

[2, 5, , 9].forEach(function(element, index) {
  console.log('a[' + index + '] = ' + element);
});
```

``` .js
// Create an array.
var fruits = ["Apple", "Banana"];
console.log(fruits.length); // → 2

var first = fruits[0]; // → "Apple"
var last = fruits[fruits.length - 1]; // → "Banana"

fruits.forEach(function(element, index) {
  console.log(element, index);
}); 

// → Apple 0
// → Banana 1

fruits.push("Orange");
console.log(fruits); // → [ 'Apple', 'Banana', 'Orange' ]

var popped = fruits.pop();
console.log(popped); // → "Orange"
console.log(fruits); // → [ 'Apple', 'Banana' ]

var shifted = fruits.shift(); 
console.log(shifted); // → "Apple"
console.log(fruits); // → [ 'Banana' ]

fruits.unshift("Pear");
console.log(fruits); // → [ 'Pear', 'Banana' ]


fruits.push("Peach"); // → [ 'Pear', 'Banana', 'Peach' ]
var idx = fruits.indexOf("Banana");  // → 1

var removed = fruits.splice(idx, 1);
console.log(removed); // → [ 'Banana' ]
console.log(fruits); // → [ 'Pear', 'Peach' ]

var cloned = fruits.slice();
console.log(removed); // → [ 'Pear', 'Peach' ]

```

``` .js
var alpha = ['a', 'b', 'c'],
    numeric = [1, 2, 3];

var alphaNumeric = alpha.concat(numeric);

console.log(alphaNumeric); // Result: ['a', 'b', 'c', 1, 2, 3]

var num1 = [1, 2, 3],
    num2 = [4, 5, 6],
    num3 = [7, 8, 9];

var nums = num1.concat(num2, num3);

console.log(nums); // Result: [1, 2, 3, 4, 5, 6, 7, 8, 9]

var alpha = ['a', 'b', 'c'];

var alphaNumeric = alpha.concat(1, [2, 3]);

console.log(alphaNumeric); 
// Result: ['a', 'b', 'c', 1, 2, 3]

```


``` .js
// Create an array.
var ar = new Array (10, 11, 12, 13, 14);

// Remove an element from the array.
delete ar[1];
console.log(ar); // → [ 10, , 12, 13, 14 ]
```

``` .js
// all following calls return true
Array.isArray([]);
Array.isArray([1]);
Array.isArray(new Array());
```

###  參考網站：

- [pop](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array/pop)
- [shift](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array/shift)
- [unshift](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array/unshift)
- [indexOf](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array/indexOf)
- [splice](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array/splice)
- [slice](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array/slice)
- [concat](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array/concat)
- [isArray](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array/isArray)

---
typeof
parseInt
``` .js

var mytext = '123';
console.log(typeof parseInt(mytext, 10)); // → "number"

parseInt("abc");     // → "NaN"
parseInt("12abc");   // → "12"

```

###  參考網站：
- [typeof 運算子 (JavaScript)](https://msdn.microsoft.com/zh-tw/library/259s7zc1(v=vs.94).aspx)
- [parseInt 函式 (JavaScript)](https://msdn.microsoft.com/zh-tw/library/x53yedee(v=vs.94).aspx)
- [parseFloat 函式 (JavaScript)](https://msdn.microsoft.com/zh-tw/library/d5hbbd4z(v=vs.94).aspx)

---
null
undefined
``` .js

var text = null;
console.log(text); // → null

var u;
console.log(u); // → undefined

console.log(typeof null); // object
console.log(typeof undefined); // undefined
```

---
條件 (三元) 運算子 (?:)

```
test ? expression1 : expression2
```
test 任何布林運算式。
expression1 如果 test 為 true，則傳回運算式。可以是逗號運算子。
expression2 如果 test 為 false，則傳回運算式。多個運算式可藉由逗號運算式連結。

``` .js
var status = (age >= 18) ? "adult" : "minor";
```

``` .js
var now = new Date();
var greeting = "Good" + ((now.getHours() > 17) ? " evening." : " day.");
```

上述範例會在下午 6 點後建立包含 "Good evening." 的字串。 使用 if...else 陳述式的同等程式碼看起來會像這樣：

``` .js
var now = new Date();
var greeting = "Good";
if (now.getHours() > 17)
   greeting += " evening.";
else
   greeting += " day.";
```

``` .js
if (err) console.log("Error: ", err);
```

###  參考網站：
- [條件 (三元) 運算子 (?:) (JavaScript)](https://msdn.microsoft.com/zh-tw/library/be21c7hw(v=vs.94).aspx)
- [Conditional_Operator](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Operators/Conditional_Operator)

---

JSON
``` .js
var myArray = [5, 2, 16, 4, 3, 18, 20];
var myObj = { nickname: 'Jack', "registration_date": new Date(1995, 11, 25), "privileged_user": true };


// JSON.stringify(): Object/Array → JSON  
var JavascriptObject = {name: "George", lastname: "Batalinski"};
var ValidJSON = JSON.stringify({name: "George", lastname: "Batalinski"});

// JSON.stringify(): JSON → Object/Array
var myArray = JSON.parse('[1, 5, "false"]');
var myObj = JSON.parse('{name: "George", lastname: "Batalinski"}');
```

---
``` .js
var mynumber = "99";
console.log(++mynumber); // → "100"
console.log(mynumber -1); // → "99"
console.log(1 -mynumber); // → "-99"
```

``` .js
var mynumber = "str99";
console.log(++mynumber); // → NaN
console.log(mynumber -1); // → NaN
console.log(1 -mynumber); // → NaN
```

---

``` .js
for(var i = 0; i < 10; i++) console.log(i);
for(var i = 0, j=10; i < 10; i++,j console.log(i*j);
```

``` .js
j=25;
for (i = 0; i < 10; i++, j++)
{
   k = i + j;
}
```
---
``` .js
if (x = y) {
}

if (x > 5) {
} else {
}

if (x > 5) {
} else if (x > 50) {
} else {
}
```

**閉包 (Closure)**
``` .js
var mynumber = 99;

function myFunc() {
  var mynumber = 9999;
  return mynumber;
}
console.log(mynumber); // → 99 
console.log(myFunc()); // → 9999


function makeAdder(x) {
  return function(y) {
    return x + y;
  };
}

var add5 = makeAdder(5);
var add10 = makeAdder(10);

console.log(add5(2));  // → 7
console.log(add10(2)); // → 12
```


---

<a name="elapsed"></a>
**Calculating elapsed time**

``` .js
// using Date objects
var start = Date.now();

// the event to time goes here:
doSomethingForALongTime();
var end = Date.now();
var elapsed = end - start; // elapsed time in milliseconds
```


``` .js
console.time('100-elements');
for (var i = 0; i < 100; i++) {
  ;
}
console.timeEnd('100-elements');
// prints 100-elements: 262ms
```

###  參考網站：
- [Date](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Date)

---

<a name="lambda"></a>

**Lambda**

> 函數f(x) = x * 2可匿名地表達為x -> x * 2
> (x -> x * 2)(2)以`JavaScript`來表達則為function(x) {return x * 2;}(2)



``` .js
(function() {
})();
```

``` .js
function(num) { return num * num; };
```

``` .js
console.log((function(num) { return num * num; })(2));
```

``` .js
var fn = function(num) { return num * num; };
console.log(fn(function(num) { return num + num; } (2))); // → 16
```

``` .js
console.log([1, 4, 9].map(function(num) { return num * num; })); // → [ 1, 16, 81 ]
```

###  參考網站：
- [map](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array/map)

---

```
myString
myRe
myArray
myFalse 
myFunc
myObj

myboolean
mytext
mynumber
myobject
myarray
my-nodejs-app

doSomething();
doSomethingElse();
 
str 
newstr 
```
---
``` .js
var log = console.log.bind(console);
log('Hello World!');
```
---

``` .js
var createPet = function(name) {
  var sex;
  
  return {
    setName: function(newName) {
      name = newName;
    },
    
    getName: function() {
      return name;
    },
    
    getSex: function() {
      return sex;
    },
    
    setSex: function(newSex) {
      if(typeof newSex == "string" && (newSex.toLowerCase() == "male" || newSex.toLowerCase() == "female")) {
        sex = newSex;
      }
    }
  }
}

var pet = createPet("Vivie");
pet.getName();                  // → Vivie

pet.setName("Oliver");
pet.setSex("male");
pet.getSex();                   // → male
pet.getName();                  // → Oliver
```

---
``` .js
var myObj = {
  a: 37,
  f1: function(){
    console.log(this.a);
  }
};

myObj.f1(); // → 37

myObj.obj = {
  a: 111,
  f1: function(){
    console.log(this.a);
  }
};

myObj.obj.f1(); // → 111
```

``` .js
var a = 37;
var myObj = {
  a: 111,
  f1: function(){
    console.log(this.a);
    var self = this;
    var f2 = function(){ console.log(self.a); }
    f2();
  }
};

myObj.f1();
```

``` .js
var obj1 = {
  a: 37,
  f1: function(){
    console.log(this.a);
  }
};

var obj2 = {
  a: 111
};

obj1.f1.call(obj2); // → 111
```


``` .js
var eric = new Object();
eric.age = 33;
eric.sex = 'male';
console.log(eric); // → { age: 33, sex: 'male' }
```

``` .js
var eric = new Object();
eric.age = 33;
eric.sex = 'male';
eric.getSex = function() { return eric.sex; };
console.log(eric.getSex()); // → male
```

``` .js
var Person = function(name, age, sex) {
  this.name = name;
  this.age = age;
  this.sex = sex;
  this.getSex = function() { return this.sex; };
  this.sayHello = function(){ console.log('hello'); };
  this.sayGoodBye = function(){ console.log('goodBye'); };
  this.walk = function(){ console.log('I am walking!'); };
};

var eric = new Person('eric', 33, 'male');
console.log(eric); // → { name: 'eric', age: 33, sex: 'male', getSex: [Function] }

var wendy = new Person('wendy', 18, 'female');
console.log(wendy); // → { name: 'wendy', age: 18, sex: 'female', getSex: [Function] }

```

``` .js
var Person = function(name, age, sex) {
  this.name = name;
  this.age = age;
  this.sex = sex;
  this.getSex = function() { return this.sex; };
  this.sayHello = function(){ console.log('hello'); };
  this.sayGoodBye = function(){ console.log('goodBye'); };
  this.walk = function(){ console.log('I am walking!'); };
  this.doAction = function(){
    console.log(this.getSex());
    this.sayHello();
    this.walk();
    this.sayGoodBye();
  }; 
};

var eric = new Person('eric', 33, 'male');
eric.doAction();
```

``` .js
'use strict';
var util = require('util');

// 建構函式 (Constructor)
function Person() {
  this.name = 'N/A';
}

// Method
Person.prototype.SetName = function(name) {
  this.name = name;
}

// Method
Person.prototype.getSex = function() {
  return this.sex;
}

// Method
Person.prototype.greet = function() {
  console.log('Hi, I am ' + this.name);
};

// Method
Person.prototype.SayHello = function() {
  console.log("Hello, World!");
}

var Employee = function(name, title, sex, age) {
  Person.call(this);
  this.name = name;
  this.title = title;
  this.sex = sex;
  this.age = age;
};

var Customer = function(name) {
  Person.call(this);
  this.name = name;
};

util.inherits(Employee, Person);
util.inherits(Customer, Person);

Employee.prototype.greet = function() {
  console.log('Hi, I am ' + this.name + ', the ' + this.title);
};

var bob = new Employee('Bob', 'Builder', 'male', 33);
var joe = new Customer('Joe');
var rg = new Employee('Red Green', 'Handyman');


bob.greet();
rg.greet();

```

###  參考網站：
-  [prototype](https://developer.mozilla.org/en/docs/Web/JavaScript/Reference/Global_Objects/Object/prototype)
- [this] (https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Operators/this)
- [JavaScript 物件導向介紹](https://developer.mozilla.org/zh-TW/docs/JavaScript_物件導向介紹)
- [Introduction to Object-Oriented JavaScript](https://developer.mozilla.org/en-US/docs/Talk:JavaScript/Introduction_to_Object-Oriented_JavaScript)

---
``` .js
try {
  throw "myException";
}
catch(e) {
  logMyErrors(e);
}
```
---
``` .js
var http = require("http");
http.createServer(function(request, response) {
  response.writeHead(200, {"Content-Type": "text/plain"});
  response.write("Hello MSDN");
  response.end();
}).listen(8080);
```

---
``` .js
var x = 'Mozilla';
var empty = '';
console.log('Mozilla is ' + x.length + ' code units long');
// → "Mozilla is 7 code units long" 

console.log('The empty string has a length of ' + empty.length);
// → "The empty string has a length of 0"
```

---

``` .js
var EventEmitter = require('events').EventEmitter;
var emitter = new EventEmitter(); 

emitter.on('test', function () {
  console.log('test'); 
});

emitter.emit('test');
```

``` .js
var EventEmitter = require('events').EventEmitter;
var em = new EventEmitter();

em.on('hello', function (arg1, arg2) {
    console.log(arg1 + ' ' + arg2);
});

em.emit('hello', 'Hello', 'World');
```


``` .js
var EventEmitter = require('events').EventEmitter;
var em = new EventEmitter();

em.on('sayHello', function(name) {
  console.log("Hello" + " " + name);
});

em.on('sayHello', function(name) {
  console.log(name + " " + "您好");
});

em.emit('sayHello', 'Eric');
```
---

###  參考網站：
- [length](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/String/length)

---
<a name="closure-compiler"></a>

hello.js
``` .js
// A simple function.
function hello(longName) {
  alert('Hello, ' + longName);
}
hello('New User');
```

```console
shell> wget -q https://dl.google.com/closure-compiler/compiler-latest.zip
shell> unzip compiler-latest.zip
shell> java -jar compiler.jar --js hello.js --js_output_file hello-compiled.js
```

hello-compiled.js
``` .js
function hello(a){alert("Hello, "+a)}hello("New User");
```

###  參考網站：
- [Closure Compiler](https://developers.google.com/closure/compiler/docs/gettingstarted_app)

---

``` .js
var crypto = require('crypto');
var hashes = crypto.getHashes();
console.log(hashes);
var ciphers = crypto.getCiphers();
console.log(ciphers);
```

``` .js
var crypto = require('crypto');

// Encrypt using AES
function aes_encrypt(str, key_str) {
  var cipher = crypto.createCipher('aes192', key_str);
  var crypt_str = cipher.update(str, 'utf8', 'hex');
  crypt_str += cipher.final('hex');
  return crypt_str;
}

// Decrypt using AES
function aes_decrypt(crypt_str, key_str) {
  var decipher = crypto.createDecipher('aes192', key_str);
  var str = decipher.update(crypt_str, 'hex', 'utf8');
  str += decipher.final('utf8');
  return str;
}

var crypt_str = aes_encrypt('cleartext', 'my_secret_password'); 
console.log(crypt_str);

var str = aes_decrypt(crypt_str, 'my_secret_password'); 
console.log(str);
```

###  參考網站：
- [aes_encrypt](https://mariadb.com/kb/en/mariadb/aes_encrypt/)

---

``` .js
  if (err) throw err;
```

---

``` .js
function main() {
  return 'Hello, World!';
}

main();
```

---

Iterator 迭代器

``` .js
function makeIterator(array){
    var nextIndex = 0;
    
    return {
       next: function(){
           return nextIndex < array.length ?
               {value: array[nextIndex++], done: false} :
               {done: true};
       }
    }
}

var it = makeIterator(['yo', 'ya']);
console.log(it.next().value); // 'yo'
console.log(it.next().value); // 'ya'
console.log(it.next().done);  // true

```

- [Iterators_and_Generators](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Guide/Iterators_and_Generators)

---

``` .js
setInterval(function() {
  doSomething();
}, 1800000 * Math.random() + 1200000); // between 20 and 50 min
```

---

###  參考網站：

- [runnable](http://code.runnable.com/)
- [新版Node.js終於支援類別](http://www.ithome.com.tw/news/98663)
- [從ECMAScript看語言約束](http://www.ithome.com.tw/voice/89425)
- [Installing Node.js and Express](https://www.vultr.com/docs/installing-node-js-and-express)
- [非同步操作的多種模式](http://www.ithome.com.tw/node/82486)
- [Visual Studio也能寫Node.js，擴充套件NTVS 1.0正式版釋出](http://www.ithome.com.tw/news/94807)
- [建立 Node.js 和 MongoDB Web 服務](https://msdn.microsoft.com/zh-tw/library/dn754378.aspx)

- [try...- catch](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Statements/try...catch)
- [var](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Statements/var)
- [Boolean](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Boolean)
- [function](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Statements/function)
- [Function](https://developer.mozilla.org/en-US/docs/Glossary/Function)
- [Array](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array)
- [for](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Statements/for)
- [for...in](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Statements/for...in)
- [if...else](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Statements/if...else)

- [JSON.stringify()](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/JSON/stringify)
- [JSON.parse()](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/JSON/parse)


