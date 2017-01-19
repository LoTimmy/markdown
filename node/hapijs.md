<img src="https://hapijs.com/public/img/logo.svg" width="200">


```console
shell> npm install hapi
shell> npm install hapi --save
```

`server.js`
```js
'use strict';

const Hapi = require('hapi');

// Create a server with a host and port
const server = new Hapi.Server();
server.connection({
  host: 'localhost',
  port: 8000
});

server.route({
  method: 'GET',
  path: '/',
  handler: function(request, reply) {
    reply('Hello, world!');
  }
});


// Add the route
server.route({
  method: 'GET',
  path: '/hello',
  handler: function(request, reply) {

    return reply('hello world');
  }
});

// Start the server
server.start((err) => {

  if (err) {
    throw err;
  }
  console.log('Server running at:', server.info.uri);
});
```


### :books: 參考網站：
- [hapijs](https://hapijs.com/)

