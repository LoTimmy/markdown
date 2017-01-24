**`Atom`**

<img src="http://i.imgur.com/Je0OrHU.png" alt="atom" width=58 height=58>

```
切換、開關 (Toggle)
重複、複製 (Duplicate) 
```

---
Keystroke    | Command
------------ | -------------
ctrl-,       |
ctrl-↑       |
ctrl-↓       |


Keystroke    | Command
------------ | -------------
ctrl-\       | tree-view:toggle
ctrl-n       | application:new-file
cmd-s        | core:save
ctrl-s       | core:save
ctrl-shift-s	 | core:save-as	
⌘-shift-s        | core:save-as
ctrl-shift-m	 | markdown-preview:toggle
ctrl-shift-p	 | command-palette:toggle	
ctrl-shift-K	 | editor:delete-line	
ctrl-shift-d     | editor:duplicate-lines
---

`keymap.cson`
```
'atom-text-editor:not([mini])':
  'ctrl-shift-K': 'editor:delete-line'
```
```
'atom-text-editor:not([mini])':
  'ctrl-e': 'editor:delete-line'
```


<img src="http://i.imgur.com/WS9X0Xs.gif" alt="atom" width=500>

<img src="https://github-atom-io-herokuapp-com.global.ssl.fastly.net/assets/screenshot-main-80d8c9841da6ed11c9d87f31136a4ca9.png" alt="atom" width=500>

`vim-mode`
```console 
shell> apm install vim-mode
```

### :books: 參考網站：
- [google](https://atom.io/users/google)



---

![Imgur](http://i.imgur.com/y931f3M.png)


### :books: 參考網站：
- [atom](https://atom.io/)
- [emmet-atom](https://github.com/emmetio/emmet-atom)
