![](http://i.imgur.com/66fTC7N.jpg)

<a name="getstarted"></a>

`訊息管理服務` (`RabbitMQ`)


![](http://www.rabbitmq.com/img/tutorials/python-one.png)

producer
![](http://www.rabbitmq.com/img/tutorials/producer.png)
queue
![](http://www.rabbitmq.com/img/tutorials/queue.png)
consumer
![](http://www.rabbitmq.com/img/tutorials/consumer.png)

----------    

安裝作業系統及`rabbitmq-server`相關套件。
因本文主要介紹`rabbitmq`如何安裝及設定，作業系統方面就不再詳述。

```console 
shell> lsb_release -a
```
```
No LSB modules are available.
Distributor ID:	Ubuntu
Description:	Ubuntu 12.04.4 LTS
Release:	12.04
Codename:	precise
```

----------
:warning: 不要停用 IPv6
 
----------


### 安裝 rabbitmq-server 
```console
shell> vim /etc/apt/sources.list
```
```
deb http://www.rabbitmq.com/debian/ testing main
```

```console
shell> wget http://www.rabbitmq.com/rabbitmq-signing-key-public.asc
shell> sudo apt-key add rabbitmq-signing-key-public.asc
shell> apt-get update
shell> sudo apt-get install rabbitmq-server
```
```console
shell> vim /etc/default/rabbitmq-server
```
### Controlling system limits ###
```console
shell> ulimit -n 1024
```

```console
shell> rabbitmqctl stop
shell> rabbitmqctl status
shell> rabbitmqctl list_users
shell> rabbitmqctl change_password guest 340$Uuxwp7Mcxo7Khy
```


```
/var/log/rabbitmq
```

```console
shell> apt-cache policy rabbitmq-server
shell> apt-cache policy erlang-base
```

----------
### :books: 參考網站：

- [http://www.rabbitmq.com/](http://www.rabbitmq.com/)
- [http://www.rabbitmq.com/install-debian.html](http://www.rabbitmq.com/install-debian.html)
- [rabbitmqctl](http://manpages.ubuntu.com/manpages/natty/man1/rabbitmqctl.1.html)
- [rabbitmqctl](http://www.rabbitmq.com/man/rabbitmqctl.1.man.html)
- [tutorial-one-python](http://www.rabbitmq.com/tutorials/tutorial-one-python.html)


<!--
http://www.gtwang.org/2014/01/ubuntu-linux-install-rabbitmq.html
-->