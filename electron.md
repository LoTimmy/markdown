最後更新： 2015-07-28


http://electron.atom.io/docs/v0.30.0/tutorial/quick-start/


http://electron.atom.io/docs/v0.36.3/api/browser-window/
http://electron.atom.io/docs/v0.36.3/api/frameless-window/
http://electron.atom.io/docs/v0.36.0/tutorial/application-packaging/

https://github.com/maxogden/electron-packager


electron-packager . FooBar --platform=darwin --arch=x64 --version=0.28.2


```console
shell> electron-packager . FooBar --platform=darwin --arch=x64 --version=0.36.3
shell> electron-packager . FooBar --platform=win32 --arch=x64 --version=0.36.3
```

```console
shell> electron-builder FooBar --platform=win --out=. --config=config.json
```



```js
'use strict';

const electron = require('electron');
const app = electron.app;
const BrowserWindow = electron.BrowserWindow;

function createWindow() {
// var win = new BrowserWindow({ width: 800, height: 600, frame: true });
// var win = new BrowserWindow({ width: 800, height: 600, frame: false });
   var win = new BrowserWindow({ width: 800, height: 600, frame: true, resizable: false });

  var win = new BrowserWindow({ transparent: true, frame: false });
  win.loadURL('file://' + __dirname + '/index.html');

  // mainWindow.webContents.openDevTools();

  win.on('closed', function() {
    win = null;
  });
}

app.on('ready', createWindow);

app.on('window-all-closed', function() {
  if (process.platform !== 'darwin') {
    app.quit();
  }
});

app.on('activate', function() {
  if (win === null) {
    createWindow();
  }
});




```
<!--
-->

### :books: 參考網站：
