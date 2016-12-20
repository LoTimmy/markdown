<img src="https://vuejs.org/images/logo.png" width="10%">

---

```
<!DOCTYPE html>
<html>
<head>
    <meta charset="UTF-8">
    <title>vue 异步获取数据</title>
    <style type="text/css">
        div{
            margin: 20px;
            border: 1px solid red;
        }
    </style>
</head>
<body>
 
<!-- vue ajax获取数据 -->
<div class="vue-box">
    <h1>{{ posts.category }}</h1>
    <ul v-for="item in posts.article">
        <li>{{ item.title }}</li>
        <li>{{ item.author }}</li>
    </ul>
</div>
 
<!-- 引入veujs -->
<script src="./js/vue.js"></script>
<!-- 引入用于配合vuejs执行ajax操作的插件 -->
<script src="./js/vue-resource.min.js"></script>
 
<script>
// ajax 获取数据
var vm2=new Vue({
    el: '.vue-ajax',
    data: {
        posts:{}
    },
    // 页面加载的时候会自动执行ready
    ready: function(){
        // 等同于jquery的$.ajax
        this.$http.get('data.php').then(function(response){
                this.posts=response.data;
            })
    }
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
  <title></title>
</head>
<body>
  <script src="https://cdnjs.cloudflare.com/ajax/libs/vue/2.0.3/vue.js"></script>
  <script src="https://cdn.jsdelivr.net/vue.resource/1.0.3/vue-resource.min.js"></script>


  <script>
  var app6 = new Vue({
    el: '#app-6',
    data: {
      message: 'Hello Vue!'
    }
  })
  </script>

</body>
</html>
```

```js
{
  // GET /someUrl
  this.$http.get('/someUrl').then((response) => {
    // success callback
  }, (response) => {
    // error callback
  });
}
```

### :books: 參考網站：
- https://github.com/pagekit/vue-resource

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

  <div id="app-2">
    <span v-for="n in 10">{{ n }}</span>
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

    var app2 = new Vue({
      el: '#app-2'   
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

```html
<ul id="example-1">
  <li v-for="item in items">
    {{ item.message }}
  </li>
</ul>
```

```js
var example1 = new Vue({
  el: '#example-1',
  data: {
    items: [
      { message: 'Foo' },
      { message: 'Bar' }
    ]
  }
})
```

```html
<ul id="example-2">
  <li v-for="(item, index) in items">
    {{ parentMessage }} - {{ index }} - {{ item.message }}
  </li>
</ul>
```


```js
var example2 = new Vue({
  el: '#example-2',
  data: {
    parentMessage: 'Parent',
    items: [
      { message: 'Foo' },
      { message: 'Bar' }
    ]
  }
})
```

```html
<ul id="repeat-object" class="demo">
  <li v-for="value in object">
    {{ value }}
  </li>
</ul>
```
```html
<div v-for="(value, key) in object">
  {{ key }} : {{ value }}
</div>
```
```html
<div v-for="(value, key, index) in object">
  {{ index }}. {{ key }} : {{ value }}
</div>
```


```js
new Vue({
  el: '#repeat-object',
  data: {
    object: {
      FirstName: 'John',
      LastName: 'Doe',
      Age: 30
    }
  }
})
```

---

```html
<div id="example-1">
  <div v-for="item in items">
    <!-- bind an attribute -->
    <img v-bind:src="item.imageSrc">

    <!-- shorthand -->
    <img :src="item.imageSrc">
  </div>
</div>
```

```js
var example1 = new Vue({
  el: '#example-1',
  data: {
    items: [
      { imageSrc: 'http://placehold.it/263x184' },
      { imageSrc: 'http://placehold.it/263x184' }
    ]
  }
})
```
---

```html
<div id="example">
  <span v-for="n in 10">{{ n }}</span>
</div>
```
```js
new Vue({
  el: '#example'
})
```
### :books: 參考網站：
- [list](https://vuejs.org/v2/guide/list.html)
- https://vuejs.org/v2/api/

---
```html
<div id="example">
  <my-component></my-component>
</div>
```


```js
// register
Vue.component('my-component', {
  template: '<div>A custom component!</div>'
})
// create a root instance
new Vue({
  el: '#example'
})
```

---

```html
<div id="example-1">
  <button v-on:click="counter += 1">Add 1</button>
  <p>The button above has been clicked {{ counter }} times.</p>
</div>
```

```js
var example1 = new Vue({
  el: '#example-1',
  data: {
    counter: 0
  }
})
```

### :books: 參考網站：
- [events](https://vuejs.org/v2/guide/events.html)

---

```js
const NotFound = { template: '<p>Page not found</p>' }
const Home = { template: '<p>home page</p>' }
const About = { template: '<p>about page</p>' }
```

---

### :books: 參考網站：
- [vuejs](https://vuejs.org/)

