![](http://www.ntop.org/wp-content/uploads/2011/08/logo_new_m.png)


----------

##### 安裝`ntop`

安裝`ntop`套件。
```console 
shell> apt-get install ntop -y
```
```console
shell> ntop --set-admin-password=<pass>
```

切換至「/var/lib/ntop」目錄下。
```console
shell> cd /var/lib/ntop
```
```console
shell> vi init.cfg
```
```ini
USER="ntop"
INTERFACES="eth1"
```
```console
shell> service ntop restart
```

### :books: 參考網站：