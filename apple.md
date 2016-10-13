![](http://i.imgur.com/Dd0Sffn.png)
<!-- ![](http://i.imgur.com/t51VWq9.png) -->

最後更新： 2016-10-13


<kbd>Command ⌘</kbd>

<kbd>Option ⌥</kbd>

<kbd>Caps Lock ⇪</kbd>

<kbd>Control ⌃</kbd>

<kbd>Shift ⇧</kbd>

<kbd>Fn</kbd>

- [Keyboard_Shortcuts](http://www.sequelpro.com/docs/Keyboard_Shortcuts)

---

<kbd>Command ⌘</kbd> + <kbd>Shift ⇧</kbd> + <kbd>+</kbd> 放大所選項目。
  
<kbd>Command ⌘</kbd> + <kbd>Shift ⇧</kbd> + <kbd>-</kbd> 縮小所選項目。

<kbd>Command ⌘</kbd> + <kbd>0</kbd>


**睡眠、登出和關機快速鍵**

<kbd>Shift ⇧</kbd> + <kbd>Control ⌃</kbd> + <kbd>電源按鈕</kbd> 使顯示器進入睡眠。 

<kbd>Command ⌘</kbd> + <kbd>Control ⌃</kbd> + <kbd>電源按鈕</kbd> 強制 Mac 重新啟動。 

<kbd>Command ⌘</kbd> + <kbd>Shift ⇧</kbd> + <kbd>Option ⌥</kbd> + <kbd>Q</kbd> 立即登出 OS X 使用者帳號，系統不會要求確認。   

<kbd>Command ⌘</kbd> + <kbd>Shift ⇧</kbd> + <kbd>Q</kbd> 登出 OS X 使用者帳號。系統會要求您確認。 

<kbd>Command ⌘</kbd> + <kbd>Option ⌥</kbd> + <kbd>Control ⌃</kbd> + <kbd>電源按鈕</kbd> 結束所有 app，然後將 Mac 關機。如果任何開啟中文件尚有未儲存的變更，系統會詢問您是否要儲存。  

---


**Finder 快速鍵**

<kbd>Command ⌘</kbd> + <kbd>E</kbd> 退出所選磁碟或卷宗。

<kbd>Command ⌘</kbd> + <kbd>Shift ⇧</kbd> + <kbd>Delete</kbd> 清空垃圾桶。

<kbd>Command ⌘</kbd> + <kbd>Shift ⇧</kbd> + <kbd>Option ⌥</kbd> + <kbd>Delete</kbd> 不顯示確認對話框便直接清空垃圾桶。

---

- `OS X`是`蘋果公司`以`Unix`為基礎所開發的圖形化使用者介面作業系統，專屬於`Macintosh`電腦，是`Mac OS`的最終版本。
- `OS X`作業系統包含兩個主要的部分：核心名為「`Darwin`」，是以`FreeBSD`原始碼和`Mach`微核心為基礎，由`蘋果公司`和獨立開發者社群協力開發，以及一個名為「`Aqua`」之專有版權的圖形使用者介面，由蘋果電腦自行開發。 
- 以往的`OS X`版本是以大型貓科動物命名，例如Mac OS X v10.7被稱為「`Lion`」，隨著2013年6月OS X Mavericks的公布，命名方式開始轉為採用加州地標。 


OS X作業系統
山獅 (Mountain Lion, 10.8)
小牛 (Mavericks, 10.9)
優勝美地 (Yosemite, 10.10)

---

**在 OS X 重置 DNS 快取**

```console
shell> sudo killall -HUP mDNSResponder
shell> sudo discoveryutil mdnsflushcache
shell> sudo dscacheutil -flushcache
```

- [在 OS X 重置 DNS 快取](https://support.apple.com/zh-tw/HT202516)

---

```console
shell> echo Hello, World | pbcopy
shell> pbpaste
```

- [pbcopy](https://developer.apple.com/legacy/library/documentation/Darwin/Reference/ManPages/man1/pbcopy.1.html)

---

```console
shell> say Hello, World
shell> say -v Alex -o hi -f hello_world.txt
shell> say -v ting-ting Hello, World
shell> say -v mei-jia Hello, World
shell> say -v sin-ji Hello, World
shell> say Hello, World
```

- [say](https://developer.apple.com/legacy/library/documentation/Darwin/Reference/ManPages/man1/say.1.html)

---

```console
shell> hdiutil imageinfo ubuntu-16.04-server-i386.iso
shell> hdiutil imageinfo 2016-09-23-raspbian-jessie-lite.img
shell> hdiutil burn ubuntu-16.04-server-i386.iso
```

- [hdiutil](https://developer.apple.com/legacy/library/documentation/Darwin/Reference/ManPages/man1/hdiutil.1.html)

---

/private/etc/hosts


---

```console
shell> ditto src dst_directory 
```

- [ditto](https://developer.apple.com/library/mac/documentation/Darwin/Reference/ManPages/man1/ditto.1.html)

---

```console
shell> softwareupdate --list 
```

```
Software Update Tool
Copyright 2002-2015 Apple Inc.

Finding available software
Software Update found the following new or updated software:
   * OS X El Capitan Update-10.11.6
	OS X El Capitan 更新 (10.11.6), 471282K [recommended] [restart]
```

```console
shell> softwareupdate --install Safari8.0.6Yosemite-8.0.6
shell> softwareupdate --install --all 
```

- [softwareupdate](https://developer.apple.com/legacy/library/documentation/Darwin/Reference/ManPages/man8/softwareupdate.8.html)

---

```console
shell> system_profiler SPSoftwareDataType
```

```
Software:

    System Software Overview:

      System Version: OS X 10.11.5 (15F34)
      Kernel Version: Darwin 15.5.0
      Boot Volume: Untitled
      Boot Mode: Normal
      Computer Name: Apple’s MacBook Air
      User Name: Apple (apple)
      Secure Virtual Memory: Enabled
      System Integrity Protection: Enabled
      Time since boot: 6 days 5:24
```

```console
shell> sw_vers
shell> sw_vers -productName
shell> sw_vers -productVersion
shell> sw_vers -buildVersion
```

```
ProductName:	Mac OS X
ProductVersion:	10.11.5
BuildVersion:	15F34
```

- [system_profiler](https://developer.apple.com/legacy/library/documentation/Darwin/Reference/ManPages/man8/system_profiler.8.html)
- [sw_vers](https://developer.apple.com/legacy/library/documentation/Darwin/Reference/ManPages/man1/sw_vers.1.html)

---

```console
shell> defaults read com.apple.desktopservices 
shell> defaults write com.apple.desktopservices DSDontWriteNetworkStores true
```

```console
shell> defaults read com.apple.appstore
shell> defaults write com.apple.appstore ShowDebugMenus true
shell> defaults delete com.apple.appstore ShowDebugMenus 
```

```console
shell> defaults read com.apple.finder
shell> defaults write com.apple.finder ShowHardDrivesOnDesktop true
```

- [defaults](https://developer.apple.com/legacy/library/documentation/Darwin/Reference/ManPages/man1/defaults.1.html)

---

### 磁碟工具程式
```console
shell> diskutil list
shell> diskutil info /dev/disk2

shell> diskutil unmount /Volumes/Untitled

shell> diskutil unmountDisk /dev/disk2
shell> diskutil eject /dev/disk2
```

```console
shell> disktype
```

- [diskutil](https://developer.apple.com/legacy/library/documentation/Darwin/Reference/ManPages/man8/diskutil.8.html)

---
```console
shell> df -hl
```
---

> 如果管理者帳號沒有密碼（空密碼），必須先提供密碼給該使用者，然後才使用 sudo 指令。
使用 sudo 指令完畢之後，可以再次變更帳號密碼，不過建議管理者帳號最好還是要設定非空白密碼。

```console
shell> sudo -i
shell> visudo
```
```
[...]
# User privilege specification
root    ALL=(ALL) ALL
%admin  ALL=(ALL) NOPASSWD: ALL
[...]
```

---

```console
shell> xcodebuild

shell> xcode-select --version
shell> xcode-select --install
```
- [xcode-select](https://developer.apple.com/legacy/library/documentation/Darwin/Reference/ManPages/man1/xcode-select.1.html)
- [xcodebuild](https://developer.apple.com/legacy/library/documentation/Darwin/Reference/ManPages/man1/xcodebuild.1.html)

---

```console
shell> tell application "Finder" to quit
shell> tell application "Finder" to launch
```

---

```console
shell> brew doctor
shell> brew help
shell> brew update
shell> brew upgrade --all
shell> brew install
shell> brew search
shell> brew list

shell> brew install bash-completion
shell> brew install lftp
shell> brew install wget
shell> brew install aria2

shell> brew cask install Caskroom/cask/osxfuse
shell> brew install homebrew/fuse/sshfs
```

```console
shell> brew install nvm

shell> mkdir ~/.nvm
shell> cp $(brew --prefix nvm)/nvm-exec ~/.nvm/

shell> export NVM_DIR=~/.nvm
shell> source $(brew --prefix nvm)/nvm.sh
```

```console
shell> nvm install v0.12.2
shell> nvm use 0.12.2
shell> nvm alias default 0.12.2

shell> npm install -g npm@latest

shell> npm install -g bower
```

<!--
Fusion 8 Pro
```
FA3RK-FHGD5-M88TZ-V4WEZ-MVAW0
FU75U-4KD5L-0845Z-JEXNZ-MLKD8
UV7XK-4PXEJ-080WY-4WXQT-NC0ZF
VC79R-6NF81-M84XZ-VNW5G-NKUW8
GC1HA-01Z14-H8D2P-04NNZ-Z6RY0
```
-->

---

### :books: 參考網站：
[http://support.apple.com/kb/HT1629](http://support.apple.com/kb/HT1629)
[https://developer.apple.com/library/mac/documentation/Darwin/Reference/Manpages/man8/diskutil.8.html](https://developer.apple.com/library/mac/documentation/Darwin/Reference/Manpages/man8/diskutil.8.html)
[http://developer.apple.com/library/mac/#documentation/AppleScript/Conceptual/AppleScriptLangGuide/reference/ASLR_cmds.html](http://developer.apple.com/library/mac/#documentation/AppleScript/Conceptual/AppleScriptLangGuide/reference/ASLR_cmds.html)
