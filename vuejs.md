上次更新日期： 2016-11-02    

![](https://vuejs.org/images/logo.png)

---

```html
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="utf-8">
  <title></title>
</head>
<body>
  <div id="app">
    {{ message }}
  </div>

  <div id="app-6">
    <p>{{ message }}</p>
    <input v-model="message">
    <pre>{{$data | json}}</pre>
  </div>

  <div id="app-7">
    <div v-if="Math.random() > 0.5">      Now you see me    </div>
    <div v-else>      Now you don't    </div>
  </div>
   
  <script src="https://cdnjs.cloudflare.com/ajax/libs/vue/2.0.3/vue.js"></script> 
  <script>
    var app = new Vue({
      el: '#app',
      data: {
        message: 'Hello Vue!'
      }
    })

    var app6 = new Vue({
      el: '#app-6',
      data: {
        message: 'Hello Vue!'
      }
    })

    var app7 = new Vue({
      el: '#app-7',
      data: {
        message: ''
      }
    })
  </script>
</body>
</html>
```
---

### :books: 參考網站：
- [vuejs](https://vuejs.org/)
