
最後更新： 2015-09-16        

Sencha Ext JS

---
```html
<!DOCTYPE HTML>
<html>
  <head>
    <title>Untitled</title>
    <meta http-equiv="Content-Type" content="text/html; charset=utf-8" />
    <meta http-equiv="Cache-Control" content="no-cache">
    <meta http-equiv="Pragma" content="no-cache">
    <meta http-equiv="Expires" content="-1"/>
    <meta http-equiv="X-UA-Compatible" content="IE=edge,chrome=1"> 

    <!--[if lt IE 9]>
    <script src="//html5shim.googlecode.com/svn/trunk/html5.js"></script>
    <![endif]-->

    <!-- Ext JS 4.2.1 -->
    <link href="//cdn.sencha.com/ext/gpl/4.2.1/resources/css/ext-all.css" type="text/css" rel="stylesheet" />
    <script type="text/javascript" charset="utf-8" src="//cdn.sencha.com/ext/gpl/4.2.1/ext-all.js"></script>
    <script type="text/javascript" charset="utf-8" src="//cdn.sencha.com/ext/gpl/4.2.1/locale/ext-lang-zh_TW.js"></script>

    <script type="text/javascript" charset="utf-8" src="grid.js"></script>
  </head>
  <body>
    <div id="grid"></div>
  </body>
</html>

```

grid.js

```js
Ext.onReady(function() {
  // Ext.Msg.alert('Congratulations!  You have Ext configured correctly!');

  var myData = {'items':[
    { 'name': 'Lisa',  "email":"lisa@simpsons.com",  "phone":"555-111-1224"  },
    { 'name': 'Bart',  "email":"bart@simpsons.com",  "phone":"555-222-1234" },
    { 'name': 'Homer', "email":"homer@simpsons.com",  "phone":"555-222-1244"  },
    { 'name': 'Marge', "email":"marge@simpsons.com", "phone":"555-222-1254"  }
    ]};

  // create the Data Store
  var myStore = new Ext.data.Store({
    storeId:'simpsonsStore',
    fields:['name', 'email', 'phone'],
    data: myData,
    proxy: {
      type: 'memory',
      reader: {
        type: 'json',
        root: 'items'
      }
    }
  });

  var colModel = [
  { header: 'Name',  dataIndex: 'name' },
  { header: 'Email', dataIndex: 'email', flex: 1 },
  { header: 'Phone', dataIndex: 'phone' }
  ];

  // create the Grid
  new Ext.grid.Panel({
    title: 'Simpsons',
    store: Ext.data.StoreManager.lookup('simpsonsStore'),
    columns: colModel,
    padding :  '10 5 3 10', // 邊框間距
    height: 200,  // 高度
    width: 400,
    renderTo: grid
  });      
});

```

---

users.json
```
{'items':[
    { 'name': 'Lisa',  "email":"lisa@simpsons.com",  "phone":"555-111-1224"  },
    { 'name': 'Bart',  "email":"bart@simpsons.com",  "phone":"555-222-1234" },
    { 'name': 'Homer', "email":"homer@simpsons.com",  "phone":"555-222-1244"  },
    { 'name': 'Marge', "email":"marge@simpsons.com", "phone":"555-222-1254"  }
    ]}
```

```js
Ext.onReady(function() {
  // Ext.Msg.alert('Congratulations!  You have Ext configured correctly!');

  // create the Data Store
  var myStore = new Ext.data.Store({
    storeId:'simpsonsStore',
    fields:['name', 'email', 'phone'],
    proxy: {
        type: 'ajax',
        url : '/users.json',
        reader: {
            type: 'json',
            root: 'items'
        }
    },
    autoLoad: true
  });

  var colModel = [
  { header: 'Name',  dataIndex: 'name' },
  { header: 'Email', dataIndex: 'email', flex: 1 },
  { header: 'Phone', dataIndex: 'phone' }
  ];

  // create the Grid
  new Ext.grid.Panel({
    title: 'Simpsons',
    store: Ext.data.StoreManager.lookup('simpsonsStore'),
    columns: colModel,
    padding :  '10 5 3 10', // 邊框間距
    height: 200,  // 高度
    width: 400,
    renderTo: grid
  });
});
```

---

```js
Ext.onReady(function() {

  // create the Data Store
  var myStore = new Ext.data.Store({
    storeId:'simpsonsStore',
    fields:['name', 'email', 'phone'],
    proxy: {
        type: 'ajax',
        actionMethods: {read: 'POST'},
        paramsAsJson: true, 
        url : '//172.24.9.101:3000/users',
        reader: {
            type: 'json',
            root: 'items'
        }
    },
  });

  myStore.load({
    params: {}
  });

  var colModel = [
  { header: 'Name',  dataIndex: 'name' },
  { header: 'Email', dataIndex: 'email', flex: 1 },
  { header: 'Phone', dataIndex: 'phone' }
  ];

  // create the Grid
  new Ext.grid.Panel({
    title: 'Simpsons',
    store: Ext.data.StoreManager.lookup('simpsonsStore'),
    columns: colModel,
    padding :  '10 5 3 10', // 邊框間距
    height: 200,  // 高度
    width: 400,
    renderTo: grid
  });
});
```

```
paramsAsJson: true
actionMethods: {create: 'POST', read: 'POST', update: 'POST', destroy: 'POST'}
```

### :books: 參考網站：
- [Ext.data.proxy.Ajax](https://docs.sencha.com/extjs/4.2.2/#!/api/Ext.data.proxy.Ajax-cfg-model)
- [Ajax](https://docs.sencha.com/extjs/5.0/5.0.1-apidocs/source/Ajax.html)

---

### :books: 參考網站：
- [Column](http://dev.sencha.com/deploy/ChartsDemo/examples/chart/Column.html)
- [Pie](http://dev.sencha.com/deploy/ChartsDemo/examples/chart/Pie.html)
- [Bar](http://dev.sencha.com/deploy/ChartsDemo/examples/chart/Bar.html)
- [BarGrouped](http://dev.sencha.com/deploy/ChartsDemo/examples/chart/BarGrouped.html)
- [extjs](http://docs.sencha.com/extjs/4.2.4/)


---

```js
Ext.onReady(function() {
  // Ext.getBody().mask("Please wait...");
  Ext.Msg.show({title: 'Built using Sencha Ext JS ' + Ext.getVersion('extjs'),
    closable: false});
});
```

---


```js
Ext.onReady(function() {
  // Ext.getBody().mask("Please wait...");
  Ext.Msg.show({title: 'Built using Sencha Ext JS ' + Ext.getVersion('extjs'),
    closable: false});
});

Ext.onReady(function() {
  var viewport = new Ext.Viewport({
    layout:'anchor',
    anchorSize: {width:800, height:600},
    items:[{
      title:'Item 1',
      html:'Content 1',
      width:800,
      anchor:'right 20%'
    },{
      title:'Item 2',
      html:'Content 2',
      width:300,
      anchor:'50% 30%'
    },{
      title:'Item 3',
      html:'Content 3',
      width:600,
      anchor:'-100 50%'
    }]
  });
});
```



### :books: 參考網站：
- [extjs](http://docs.sencha.com/extjs/4.2.2/)
- [extjs 4.2.1](http://cdn.sencha.com/ext/gpl/4.2.1/ext-all.js)
- [extjs 4.2.2](http://cdn.sencha.com/downloads/docs/extjs-docs-4.2.2.zip)
