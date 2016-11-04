最後更新： 2016-09-07    

**screen - terminal multiplexer with VT100/ANSI terminal emulation**


卸離 (Detach)

<kbd>Ctrl</kbd>+<kbd>a</kbd> <kbd>d</kbd>

Create

<kbd>Ctrl</kbd>+<kbd>a</kbd> <kbd>c</kbd>

Next

<kbd>Ctrl</kbd>+<kbd>a</kbd> <kbd>n</kbd>

前一 (Previous)

<kbd>Ctrl</kbd>+<kbd>a</kbd> <kbd>p</kbd>


```console
shell> apt-get install screen
shell> screen
shell> screen -d -m aria2c http://example.org/mylinux.torrent
shell> screen -r
shell> screen -ls
shell> screen -d -S foo -m bash -c ""

```

### :books: 參考網站：
- [screen](https://www.gnu.org/software/screen/)
