<img src="https://pbs.twimg.com/media/CZGHPChUAAA3jqE.png:thumb" alt="">        

![Imgur](http://i.imgur.com/TFg9kMXt.png)
![Imgur](http://i.imgur.com/sOfjAiH.png)

---

```console
shell> gpg --keyserver hkp://keys.gnupg.net --recv-keys 409B6B1796C275462A1703113804BB82D39DC0E3
shell> curl -sSL https://get.rvm.io | bash -s stable --ruby
shell> source /usr/local/rvm/scripts/rvm
shell> rvm install 2.3.1
shell> rvm --default use 2.3.1
```
--- 

```console
shell> gem update --system
shell> gem --version
shell> gem install rails
shell> gem install rails -v 5.0.0
shell> rails -v 
```

```console
shell> apt-get install libmysqlclient-dev
shell> gem install mysql2
```

### 安裝 Percona Server 5.7
```console
shell> sudo apt-key adv --keyserver keys.gnupg.net --recv-keys 8507EFA5
shell> echo "deb http://repo.percona.com/apt "$(lsb_release -sc)" main" | sudo tee /etc/apt/sources.list.d/percona.list
shell> sudo apt-get update
shell> sudo apt-get install percona-server-server-5.7
```

```sql
CREATE USER 'root'@'%' IDENTIFIED BY 'mypass';
GRANT ALL ON *.* TO 'root'@'%';
CREATE DATABASE foo_development;
CREATE DATABASE foo_test;
```

```console
shell> rails new foo -d mysql
```

config/database.yml

```
development:
  <<: *default
  database: foo_development
  username: root
  password: mypass
  host: 10.197.134.8

test:
  <<: *default
  database: foo_test
  username: root
  password: mypass
  host: 10.197.134.8
```

```
Usage: rails server [mongrel, thin etc] [options]
    -p, --port=port                  Runs Rails on the specified port.
                                     Default: 3000
    -b, --binding=IP                 Binds Rails to the specified IP.
                                     Default: localhost
    -c, --config=file                Uses a custom rackup configuration.
    -d, --daemon                     Runs server as a Daemon.
    -e, --environment=name           Specifies the environment to run this server under (test/development/production).
                                     Default: development
    -P, --pid=pid                    Specifies the PID file.
                                     Default: tmp/pids/server.pid
    -C, --[no-]dev-caching           Specifies whether to perform caching in development.
                                     true or false

    -h, --help                       Shows this help message.
```
```console
shell> rails server -b 10.195.38.90 -p 8080
```

```
* Environment: development
* Listening on tcp://localhost:8080
Use Ctrl-C to stop
```



/usr/local/rvm/

### :books: 參考網站：
- https://www.ruby-lang.org/en/
- [rubyonrails](http://rubyonrails.org/)
- [getting_started](http://guides.rubyonrails.org/getting_started.html)
- [rvm](https://rvm.io/)