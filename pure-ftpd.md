
上次更新日期： 6/8/2016 11:25:16 AM       

---

```console
shell> apt-get install pure-ftpd
shell> mkdir /home/ftpusers
shell> groupadd ftpgroup
shell> useradd -g ftpgroup -d /dev/null -s /etc ftpuser
```

```console
shell> vim /etc/pure-ftpd/conf/PAMAuthentication
```

```
no
```

```console
shell> cd /etc/pure-ftpd/auth; ln -s ../conf/PureDB 60puredb
shell> chown -R ftpuser:ftpgroup /home/ftpusers
```

```console
shell> mkdir /home/ftpusers/joe
shell> pure-pw useradd <login> -u uid -d <home directory> # CREATING A NEW USER
shell> pure-pw useradd joe -u ftpuser -d /home/ftpusers/joe
shell> pure-pw mkdb
shell> pure-pw list
shell> pure-pw userdel <login>
shell> pure-pw show <login>        # DISPLAYING INFO
shell> pure-pw userdel <login> -m  # DELETING USERS

shell> pure-pw useradd joe -u ftpuser -d /home/ftpusers/joe
```

---
### :books: 參考網站：

