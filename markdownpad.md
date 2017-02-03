![](https://markdownpad.com/img/markdownpad2-weblogo.png)

- 以目前來說，**最受鎂光燈關注的輕量標記語言是`Markdown`，雖然原因最主要還是來自`GitHub`對`Markdown`的支援**，像是可在評論或.md檔中使用`Markdown`語法，幾乎算是`GitHub`的官方標記語言。**`Markdown`目標是「易讀易寫」，語法最大靈感來源就是純文字的電子郵件格式**，想想你會在純文字的電子郵件中如何標註，就會知道為何`Markdown`的標註都是由標點符號所組成，這些符號不難，也不會過於干擾閱讀，就如同你不會在純文字電子郵件中，搞些很難撰寫或障礙閱讀的符號。
- 有些標記語言易於從文字轉為`HTML`，`Markdown`也受到這類語言的影響，因而在`Markdown`中對`HTML`是很親切的，你甚至可以在`Markdown`文件中直接撰寫`HTML`（不過不鼓勵）。
- 若沒有搭配所視即所得編輯器，`HTML`語法本身並不適合書寫，因此，就文字書寫來說，可以選擇一個輕量標記語言，像是`Markdown`，再透過程式轉換為`HTML`，之後也能達到在各個格式間轉換之目的。

---

---
First Header  | Second Header
------------- | -------------
Content Cell  | Content Cell
Content Cell  | Content Cell

```
First Header  | Second Header
------------- | -------------
Content Cell  | Content Cell
Content Cell  | Content Cell
```

---
<kbd>Ctrl</kbd>+<kbd>v</kbd>
<kbd>⌘</kbd>+<kbd>v</kbd>

```
<kbd>Ctrl</kbd>+<kbd>v</kbd>
<kbd>⌘</kbd>+<kbd>v</kbd>
```
---
:star: [Emoji](http://www.emoji-cheat-sheet.com/)

:smile: `:smile:`
:cry: `:cry:`

---
Task Lists

``````````````````
- [x] @mentions, #refs, [links](), **formatting**, and <del>tags</del> are supported
- [x] list syntax is required (any unordered or ordered list supported)
- [x] this is a complete item
- [ ] this is an incomplete item

- [ ] a bigger project
  - [ ] first subtask #1234
  - [ ] follow up subtask #4321
  - [ ] final subtask cc @mention
- [ ] a separate task
``````````````````

- [x] @mentions, #refs, [links](), **formatting**, and <del>tags</del> are supported
- [x] list syntax is required (any unordered or ordered list supported)
- [x] this is a complete item
- [ ] this is an incomplete item

- [ ] a bigger project
  - [ ] first subtask #1234
  - [ ] follow up subtask #4321
  - [ ] final subtask cc @mention
- [ ] a separate task

---
刪除線 (Strikeout)

``````````````````
~~刪除線~~
``````````````````

~~刪除線~~

---

```html
<!doctype html>
<html lang="en">
<head>
  <meta charset="utf-8">
  <title></title>	
  <link rel="stylesheet" href="style.css">
  <script type="text/javascript"></script>
</head>
<body>
  <img src="mygraphic.bmp">
</body>
</html>
```

---

- **Bold** (`Ctrl+B`) and *Italic* (`Ctrl+I`)
- Quotes (`Ctrl+Q`)
- Code blocks (`Ctrl+K`)
- Headings 1, 2, 3 (`Ctrl+1`, `Ctrl+2`, `Ctrl+3`)
- Lists (`Ctrl+U` and `Ctrl+Shift+O`)

---

# Table of Contents

- [Go to Section One](#sectionOne)
- [Go to Section Two](#sectionTwo)

<a name="sectionOne"></a>
## My First Header ##
This is some content in my first section.

<a name="sectionTwo"></a>
## My Second Header ##
This is some content in my second section.


```
# Table of Contents

- [Go to Section One](#sectionOne)
- [Go to Section Two](#sectionTwo)

<a name="sectionOne"></a>
## My First Header ##
This is some content in my first section.

<a name="sectionTwo"></a>
## My Second Header ##
This is some content in my second section.
```

---

Don't guess if your [hyperlink syntax](http://markdownpad.com) is correct; LivePreview will show you exactly what your document looks like every time you press a key.

---

.bash
.html
.csharp
.apacheconf

---


CommonMark

---


### :books: 參考網站：
- [Mastering Markdown](https://guides.github.com/features/mastering-markdown/)
- [MarkdownPad Feature Comparison](http://markdownpad.com/compare.html)
- [https://markdownpad.com/news/](https://markdownpad.com/news/)
- [https://help.github.com/articles/github-flavored-markdown/](https://help.github.com/articles/github-flavored-markdown/)
- [手不離鍵盤的輕量標記語言](http://www.ithome.com.tw/node/84872)