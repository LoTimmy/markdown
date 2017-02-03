![git](http://git-scm.com/images/logo@2x.png)

> 在軟體開發過程中，程式碼的保存一直是不容忽視的工作事項，而這常受到許多不可抗力因素影響，像是硬碟故障、檔案被誤刪或覆蓋，而造成事後甚高的補救成本。

> 人有失足，馬有亂蹄，因為程式總會寫錯，需求規畫也可能隨時變更內容，所以，系統總是會需要回復到先前開發的版本。

> 然而版本控管當然不只是程式碼備份，它可以詳盡記錄程式碼內容異動歷程，是這種工具最基本的功能，以最少的檔案空間記錄最完整的版本資訊，讓開發者可以實際找出所想要的程式碼版本內容。

> 軟體開發通常需要多人協同運作，此時就會團隊運作必須解決同一份程式碼同時被多人編輯的問題。版本控管工具提供了成熟良好的機制，發出警訊提醒管理者及相關開發人員及早處理，以避免未預計的狀況不斷發生而延誤開發時程。

> 程式碼在開發過程中，有**版本控制**(`Version Control`)和**協同合作**的需求，因此需要程式碼管理的工具，`Git`就是其中一個選項。

> `Git`本身是個分散式版本控制系統，由`Linux`創建者`Linus Torvalds`於2005年開始打造，它是基於`P2P`（Peer-To-Peer）架構開發，每個開發者手上的`檔案庫`（`Repository`）地位相等且可獨立運作。

> 當版本控制系統開始出現時，開發團隊中開發者之間合作的方式，是共用同一個「`檔案庫`（`Repository`）」，無論這個檔案庫是在同一部工作站，或可透過網路存取的檔案系統上的本地端檔案庫，還是透過一個特定的通訊協定可以存取的遠端檔案庫，所有的成員都是共同存取同一份檔案庫。這種方式，就被稱為`集中式`（`Centralized`）的版本控制系統。

> 分散式的版本控制系統和集中式的版本控制系統，最大的差別在於，分散式的版本控制系統的檔案庫允許不只一份，事實上，每個開發者都可以在自己的一部或多部開發機器上建立檔案庫。

> `GitHub`是存放`Git`程式碼管理的資料庫。
> `GitHub`上還加入社群的概念，跟臉書一樣，你可以跟隨其他開發朋友，或觀看其他開發專案進度。

> 對開發人員而言，版本控制與原始碼編譯器與編譯器一樣，就像是吃飯與呼吸，是日常開發生活的一部分。
> 版本控制是管理一組檔案的許多版本的流程。它們通常是軟體系統的原始檔案（所以它通常被稱為原始碼控制），但是它也可以是簡單的文件樹改版，或任何其他你想要在檔案系統中儲存的東西。

> 這幾年來出現許多不同的`VCS`（Version Control Systems，版本控制系統）系統，從`Unix`的`rcs`指令開始（1980年代初），經歷集中式的`CVS`（在1990年代流行），它的現代化兄弟`Subversion`（2000年代當道），最後進入現代離散系統的世界，如`Git`與`Mercurial`（現在統治2010年代）。有些工具是商業性的，許多其他的都是開放原始碼的。它們的認證、價格、易用性、支援平台、成熟度、可擴充性及功能各有不同。
> 最重要的差異是運作的模式。已成為歷史的集中系統透過一個中央伺服器來管理存放所有被控制版本的檔案的存儲庫，並用它來掌控所有通訊。這是一個簡單的模式，但任何操作都需要存取伺服器。最近的VCS是離散模式，一種端對端的方式，讓每一台電腦都可以儲存它自己的存儲庫副本。這可產生更多令人印象深刻的工作流，並且讓你可以與存儲庫互動，就算你沒有連結網路。

> 使用版本控制。它不是一個選項，或是最好可以擁有的工具。它是開發的骨幹。如果沒有它，你的工作會很危險。

> 對開發新手而言，想要善用`GitHub`平臺提供的`Git`版本控管服務，上手不難，但隨著開發專案開始衍生分支版本後，不少新手往往很容易發生越管版本越混亂的窘況。新手最大的迷思是「**直接將集中式版本控制軟體的觀念套用在`Git`上。**」，新手要先了解分散式版本控制系統的運作原理，否則「即便有再好的工具，如果觀念不清楚也沒有用。」

> 在`Git`工作流程中，使用者先從儲存庫下載某一版本到工作目錄，檔案修改完後，把檔案快照新增到暫存區域，執行提交後檔案就永久存到儲存庫內。

---

```console
shell> brew install git
shell> brew cask install sourcetree
```

---

<img src="http://i.imgur.com/2V2g0Sx.png" width="500">

<img src="http://i.imgur.com/unRQXHr.png" width="500">

<img src="http://i.imgur.com/UAfIe37.png" width="300">

<img src="http://i.imgur.com/pf5uNCz.png" width="300">

<img src="http://i.imgur.com/Z6gnVPv.png" width="300">

<img src="http://i.imgur.com/eBmGfJb.png" width="300">


```console
shell> mkdir helloworld 
shell> git init
shell> edit hello.c
shell> git add hello.c
shell> git status
shell> git commit -m "initial commit" --author "A U Thor <author@example.com>"
shell> git log
shell> git commit --amend -m "Initial commit" --author "A U Thor <author@example.com>"
shell> git log
```

```console
shell> git add .
shell> git commit -m "initial revision"
```

- **`Revision`** `[rɪˋvɪʒən]` `修訂` `re・vi・sion`
- **`Initial`** `[ɪˋnɪʃəl]` `初始` `起始` `i・ni・tial`
- **`Commit`** `[kəˋmɪt]` `認可` `交付` `確認` `com・mit`

### :books: 參考網站：
- [git-log](https://git-scm.com/docs/git-log)
- [git-init](https://git-scm.com/docs/git-init)
- [git-add](https://git-scm.com/docs/git-add)
- [git-status](https://git-scm.com/docs/git-status)
- [git-commit](https://git-scm.com/docs/git-commit)

---


```console
shell> git config -l
shell> git config --system -l
shell> git config --global -l
shell> git config --local -l

shell> git config --system user.name "Your Name"
shell> git config --system user.email you@example.com

shell> git config --global user.name "Your Name"
shell> git config --global user.email you@example.com
shell> git config --global color.ui true
shell> git config --global push.default simple

shell> git config --local user.name "Your Name"
shell> git config --local user.email you@example.com
shell> git config --local color.ui true

shell> git config --unset user.name

shell> git config --global --edit
shell> git commit --amend --reset-author
```

### :books: 參考網站：
- [git-config](https://git-scm.com/docs/git-config)

---

```console
shell> edit hello.c hello.h
shell> git add hello.c
shell> git status
shell> touch .gitignore
shell> edit .gitignore
shell> git commit -m "My changes"
shell> git log
```
`.gitignore`

```
.gitignore
*.h
```

### :books: 參考網站：
- [gitignore](https://git-scm.com/docs/gitignore)
- [ignoring-files](https://help.github.com/articles/ignoring-files/)


---
```console
shell> git add .
```

```
warning: CRLF will be replaced by LF in myfile.txt.
The file will have its original line endings in your working directory.
```

```console
shell> git config --global core.autocrlf
shell> git config --global core.autocrlf input
shell> git config --global core.autocrlf true
shell> git config --global core.autocrlf false
```

```
shell> git config --global core.eol
```

```console
shell> echo "* text=auto" >.gitattributes
```

`.gitattributes`
```
* text=auto

*.txt text
*.vcproj text eol=crlf
*.sh text eol=lf
*.jpg -text
*.jpg -text -diff

*.md text eol=lf
*.markdown text eol=lf

*.c	filter=indent

manual.pdf	-text
weirdchars.txt	text
```

- [gitattributes](https://git-scm.com/docs/gitattributes)

---

```console
shell> edit hello.c
shell> git add hello.c
shell> git rm hello.c
shell> git rm --cached hello.c
shell> git reset HEAD hello.c
```

### :books: 參考網站：
- [git-reset](https://git-scm.com/docs/git-reset)
- [git-rm](https://git-scm.com/docs/git-rm)

---

```console
shell> bfg --no-blob-protection --delete-files YOUR-FILE-WITH-SENSITIVE-DATA
```

```console
shell> bfg --no-blob-protection --delete-files id_{dsa,rsa}  my-repo.git
```

```console
shell> git reflog expire --expire=now --all && git gc --prune=now --aggressive
```


```console
shell> git clone --bare https://github.com/you/HelloWorld.git HelloWorld.git
shell> bfg --no-blob-protection --delete-files id_{dsa,rsa} HelloWorld.git
```


### :books: 參考網站：
- [remove-sensitive-data](https://help.github.com/articles/remove-sensitive-data/)
- [bfg](https://rtyley.github.io/bfg-repo-cleaner/)

---


```console
shell> git log --pretty=oneline
shell> git log --pretty=oneline --abbrev-commit
shell> git remote add origin YOUR_GIT_CLONE_URL_HERE
shell> git remote add origin https://github.com/you/HelloWorld.git
```

### :books: 參考網站：
- [changing-a-remote-s-url](https://help.github.com/articles/changing-a-remote-s-url/)

---

```console
shell> git add -A
shell> git add .
shell> git add -u
```

---

```console
shell> mkdir helloworld 
shell> git init
shell> git add .
shell> git commit -m "initial commit"
shell> git remote add azure [URL for remote repository]
shell> git push azure master
```
---

```console
shell> mkdir HelloWorld
shell> cd HelloWorld
shell> git init
shell> echo HelloWorld > testfile.txt
shell> git status

shell> git add . -n
shell> git add .

shell> git status
shell> git commit -a
shell> git log
shell> git commit -a -m "Initial commit"
shell> git commit -m "Demo"
shell> git commit -m "My changes"
shell> git commit -am "disable node_modules cache" --allow-empty
shell> git push heroku master

shell> git add package.json
shell> git commit -m "Added package.json"

shell> git diff HEAD testfile.txt  
shell> git show

shell> git diff 0fcd2baef5b6741412db6eb3bd2c2b559a02b64f fd7f63f055f2e6ecc23be1a9a3b33a438ae68ead

shell> git remote add origin https://username@your-azure-website.scm.azurewebsites.net:443/your-azure-website.git
shell> git push
```

```
Aborting commit due to empty commit message.
```
- **`Aborting`** `正在中止`
- **`Empty`** `[ˋɛmptɪ]` `空的` `空` `空白` `emp・ty`


```console
shell> git clone --bare HelloWorld HelloWorld.git
shell> scp -r HelloWorld.git user@git.example.com:/opt/git
shell> git clone user@git.example.com:/opt/git/HelloWorld.git

shell> git remote -v
shell> git push origin master
shell> git remote set-url origin user@git.example.com:/opt/git/HelloWorld.git
shell> git remote show origin
```

```console
shell> git remote add azure https://username@your-azure-website.scm.azurewebsites.net:443/your-azure-website.git
shell> git push azure master
```

---
```console
shell> mkdir HelloWorld.git
shell> cd HelloWorld.git
shell> git init --bare
```

```console
shell> mkdir HelloWorld
shell> cd HelloWorld
shell> git init
shell> echo HelloWorld > testfile.txt
shell> git commit -a -m "Initial commit"
shell> git commit -a -m "My changes"

shell> git remote add origin /opt/git/HelloWorld.git
shell> git push origin master
```

```console
shell> git clone /opt/git/HelloWorld.git
```

```console
shell> git clone user@git.example.com:/opt/git/HelloWorld.git

shell> git remote set-url origin user@git.example.com:/opt/git/HelloWorld.git
shell> git remote -v
shell> git commit -a -m "My changes"
shell> git push origin master
```

```console
shell> git pull origin master
shell> git pull --progress
```

---

```console
shell> git branch
shell> git branch -vv
shell> git branch --remotes
```

```console
shell> git push origin --delete Branch_df65c30a8bb632955646b90f778c0cb5a7c5b28f
```
---

```console
shell> mkdir web.git
shell> cd web.git
shell> git init --bare
```

`hooks/post-receive`


```sh
#!/bin/sh
git --work-tree=/var/www/html clean -fd
git --work-tree=/var/www/html checkout --force

chown -R www:www /var/www/html
```
```console
shell> chmod -x hooks/post-receive
```
```console
shell> git remote add prd 192.168.8.88:/opt/web.git
shell> git remote add tst 192.168.8.88:/opt/web-tst.git
shell> git add *
shell> git commit -m ''
shell> git push tst master
shell> git push prd master
```

### :books: 參考網站：
- [githooks](https://git-scm.com/docs/githooks)
- [git-checkout](https://git-scm.com/docs/git-checkout)
- [git-clean](https://git-scm.com/docs/git-clean)
- [git](https://git-scm.com/docs/git)
- https://git-scm.com/book/en/v2/Customizing-Git-Git-Hooks

`hooks/pre-commit`

```console
shell> git add .
shell> git diff --cached --name-only --diff-filter=ACM
```

```sh
#!/bin/sh

if `git diff --cached --name-only --diff-filter=ACM | grep '.js'`
then
  jshint --verbose 
fi
exit $?
```

---

- [gist](https://gist.github.com/)
---

```console
shell> git mv JavaScript javascript
```

### :books: 參考網站：
- [git-mv](https://git-scm.com/docs/git-mv)
---

### :books: 參考網站：
- [4.2 伺服器上的 Git - 在伺服器上部署 Git](https://git-scm.com/book/zh-tw/v1/%E4%BC%BA%E6%9C%8D%E5%99%A8%E4%B8%8A%E7%9A%84-Git-%E5%9C%A8%E4%BC%BA%E6%9C%8D%E5%99%A8%E4%B8%8A%E9%83%A8%E7%BD%B2-Git)

---

### :books: 參考網站：
- [git-remote](http://git-scm.com/docs/git-remote)
- [Customizing-Git-Git-Configuration](http://git-scm.com/book/en/Customizing-Git-Git-Configuration)
- [Git for Windows](https://msysgit.github.io/)
- [程式開發者的社群網路新世界](http://www.ithome.com.tw/node/79439)
- [從集中版本控制到分散式版本控制](http://www.ithome.com.tw/node/77088)
- [持續整合下的版本控管做法](http://www.ithome.com.tw/node/67969)
- [語意明確的版本變更](http://www.ithome.com.tw/voice/85505)
- [軟體開發過程中不能缺少的系統](http://www.ithome.com.tw/node/76548)


---

### :books: 參考網站：
- https://git-scm.com/book/be/v2/Git-Tools-Credential-Storage
- [caching-your-github-password-in-git](https://help.github.com/articles/caching-your-github-password-in-git/)
- [connecting-to-github-with-ssh](https://help.github.com/articles/connecting-to-github-with-ssh/)

---

### :books: 參考網站：
- [hello-world](https://guides.github.com/activities/hello-world/)

