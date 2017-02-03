<img src="https://hapijs.com/public/img/logo.svg" width="200">


```console
shell> npm install hapi
shell> npm install hapi --save
```

---

**`Creating a server`**

<img src="http://i.imgur.com/fiyZJux.png" width="50" alt="Example">

`server.js`
```js
'use strict';

const Hapi = require('hapi');

const server = new Hapi.Server();
server.connection({
  port: 3000,
  host: 'localhost'
});

server.start((err) => {

  if (err) {
    throw err;
  }
  console.log(`Server running at: ${server.info.uri}`);
});
```

---

**`Adding routes`**

<img src="http://i.imgur.com/fiyZJux.png" width="50" alt="Example">

```js
'use strict';

const Hapi = require('hapi');

const server = new Hapi.Server();
server.connection({
  port: 3000,
  host: 'localhost'
});

server.route({
  method: 'GET',
  path: '/',
  handler: function(request, reply) {
    reply('Hello, world!');
  }
});

server.route({
  method: 'GET',
  path: '/{name}',
  handler: function(request, reply) {
    reply('Hello, ' + encodeURIComponent(request.params.name) + '!');
  }
});

server.start((err) => {

  if (err) {
    throw err;
  }
  console.log(`Server running at: ${server.info.uri}`);
});
```

---

**`Creating static pages and content`**

<img src="http://i.imgur.com/fiyZJux.png" width="50" alt="Example">

```js
server.register(require('inert'), (err) => {

  if (err) {
    throw err;
  }

  server.route({
    method: 'GET',
    path: '/hello',
    handler: function(request, reply) {
      reply.file('./public/hello.html');
    }
  });
});
```

---

**`Using plugins`**

```console
shell> npm install --save good
shell> npm install --save good-console
shell> npm install --save good-squeeze
```

`server.js`

```js
'use strict';

const Hapi = require('hapi');
const Good = require('good');

const server = new Hapi.Server();
server.connection({ port: 3000, host: 'localhost' });

server.route({
  method: 'GET',
  path: '/',
  handler: function(request, reply) {
    reply('Hello, world!');
  }
});

server.route({
  method: 'GET',
  path: '/{name}',
  handler: function(request, reply) {
    reply('Hello, ' + encodeURIComponent(request.params.name) + '!');
  }
});

server.register({
  register: Good,
  options: {
    reporters: {
      console: [{
        module: 'good-squeeze',
        name: 'Squeeze',
        args: [{
          response: '*',
          log: '*'
        }]
      }, {
        module: 'good-console'
      }, 'stdout']
    }
  }
}, (err) => {

  if (err) {
    throw err; // something bad happened loading the plugin
  }

  server.start((err) => {

    if (err) {
      throw err;
    }
    server.log('info', 'Server running at: ' + server.info.uri);
  });
});

```

```
140625/143008.751, [log,info], data: Server running at: http://localhost:3000

140625/143205.774, [response], http://localhost:3000: get / {} 200 (10ms)
```


---

npm install hapi-swagger --save
npm install inert --save
npm install vision --save

```
const Hapi = require('hapi');
const Inert = require('inert');
const Vision = require('vision');
const HapiSwagger = require('hapi-swagger');
const Pack = require('./package');

const server = new Hapi.Server();
server.connection({
  host: 'localhost',
  port: 3000
});

const options = {
  info: {
    'title': 'Test API Documentation',
    'version': Pack.version,
  }
};

server.register([
  Inert,
  Vision, {
    'register': HapiSwagger,
    'options': options
  }
], (err) => {
  server.start((err) => {
    if (err) {
      console.log(err);
    } else {
      console.log('Server running at:', server.info.uri);
    }
  });
});

server.route(Routes);
```



### :books: 參考網站：
- [hapi-swagger](https://github.com/glennjones/hapi-swagger)


---

- `Tutorials` `[tjuˋtorɪəl]` `教學課程` `tu・to・ri・als`

### :books: 參考網站：
- [hapijs](https://hapijs.com/)
- [tutorials](https://hapijs.com/tutorials)
- [api](https://hapijs.com/api)

