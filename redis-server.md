![](https://raw.githubusercontent.com/docker-library/docs/master/redis/logo.png)

- 高效能的記憶體式`NoSQL`資料庫`Redis`。
- **`Redis`是近年來出現`NoSQL`開源資料庫的一種，並且將資料存放在記憶體中，以提升讀取的效率。**
- **`記憶體資料庫` (`In-memory Database`) 就是將資料儲存在記憶體的`NoSQL`資料庫**，包括了`Memcached`、`Redis`、`Velocity`、`Tuple space`等。**其實像`Memcached`、`Redis`都是一種`Key-Value`資料架構的資料庫，只是這類資料庫改將資料儲存在記憶體中來提高讀取效率，大多用來快取常用網頁，加快傳遞網頁的速度，減少讀取硬碟的次數，不過系統關機後就無法保存。**
- `Redis`優點之一是具備防止雪崩效應機制且不會遺失資料。
- `Redis`具備防止雪崩效應機制且不會遺失資料，比起`Memcached`與`AeroSpike`是較好的記憶體資料庫。
- **像`Redis`這種記憶體式資料庫，主要的功能還是提供快取，而非完整的正規SQL關聯式資料庫替代品。**
- **像`Redis`這種記憶體式資料庫，主要的功能除了提供快取外，還可額外提供運算處理，所以非常適合輔助關聯式資料庫。**
- 應用方式，**全部資料還是放在資料庫，真正需要加快速度的資料或額外特別的處理時，也會放一份在`Redis`處理**。全部資料還是放在`MySQL`，真正需要加快速度的資料，才會放一份在`Redis`裡面。
- 較於同為`NoSQL`記憶體資料庫的`Memcached`，**`Redis`通常只會使用處理器的單一執行緒，若真的想要利用多核處理器，建議，在建置上可以採多個`Redis`實例(`Instance`)，以充分應用CPU硬體資源，但設定及操作上有許多需要注意之處，效果有好有壞。**`Redis`使用`jemalloc`及`tcmalloc`模式降低記憶體碎片化的情況，而不採用`Free-list`或其他方法，是為了維持其簡單、單純、較有效率的設計原則，相較之下，`Memcached`採用預先分配的方式，雖然較能有效降低記憶體碎片化問題，卻會帶來浪費空間的情況。
- `Redis`雖然只支援單一處理器單一執行緒，然而還是有變通的方法可以充分使用硬體效能，就是同時執行多個`Redis`程式。實務上一個`Redis`，通常還要再保留一個執行緒給它的外掛使用，故雖然最多可以執行與處理器執行緒同樣的數量，仍建議最大開啟`Redis`的數量為執行緒的一半。
- `Memcached`與`Redis`有許多的架構上的差異，例如`Memcached`支援多個處理器核心和執行緖，較能充分利用現代處理器的效能，並且採用預先分配的記憶體池零碎空間，減少記憶碎片，而使得實際的記憶體使用量較`Redis`要少，以及記憶體分配壓力也同時減少。
- `Memcached`支援處理器的多執行緒，因此較能善用現代處理器多核心與多執行緒的效能。這件事情因為`Redis`只會使用單一執行緒的資源，變成了優點。
- **`Redis`與`Memcached`各有其長處，以數據量做分界，在10KB以下，或是10MB以上，`Redis`的效能比`Memcached`來得要好。**
- **假如`Redis`的記憶體設定值太高，有可能演變成記憶體使用量超過實體記憶體，造成作業系統強制關掉`Redis`的情況。**
- `Redis`的長處，在於提供豐富的資料型態操作，例如`Hashs`、`Lists`、`Sets`、`Sorted Sets`、`HyperLogLog`等，並內建複寫(`replication`)與叢集功能，以及能夠直接就地更新作業的特性。
- 除了老牌的`Memcached`以外，2009年出現了一個新的開源記憶體資料庫`Redis`。除了提供分散式的快取以外，`Redis`和`Memcached`最大的不同點是，`Redis`提供了一個資料架構，可以自動排序那些儲存在`Redis`中的資料，讓開發者取得排序後的資料。
- `Redis` 是一種進階的索引鍵值存放區，其中的索引鍵可以包含類似`字串`、`雜湊`、`清單`、`集合`和`排序的集合`等資料結構。`Redis` 針對這些資料類型支援一組不可部分完成的作業。

---

### 在 `Ubuntu` 14.04 LTS 上建置 `redis-server`

安裝作業系統及`redis-server`相關套件。
因本文主要介紹`redis-server`如何安裝及設定，作業系統方面就不再詳述。

```console
shell> lsb_release -a

No LSB modules are available.
Distributor ID:	Ubuntu
Description:	Ubuntu 14.04 LTS
Release:	14.04
Codename:	trusty
```


```
net.core.somaxconn = 128

net.core.somaxconn = 3000

```


### 安裝 Redis 
```console
shell> aptitude install redis-server

shell> /etc/redis/redis.conf
```
```
[...]
daemonize yes
[...]
pidfile /var/run/redis/redis-server.pid
[...]
port 6379
[...]
# bind 127.0.0.1 # ★★★
[...]
tcp-keepalive 300 # ★★★
[...]
requirepass foobared # ★★★
[...]
maxmemory 100mb  # ★★★
[...]
maxmemory-policy volatile-lru # Maxmemory 原則是指示 Redis 在達到 maxmemory (建立快取時選取的快取供應大小) 時該如何選取要移除之項目的設定。預設設定為 volatile-lru，代表要移除具有以 LRU 演算法設定之到期時間的金鑰。
[...]
maxmemory-samples 3 #
```
```console
shell> service redis-server restart
```

```console
shell> wget http://download.redis.io/releases/redis-2.8.19.tar.gz
shell> wget http://download.redis.io/redis-stable.tar.gz
shell> tar xzf redis-2.8.19.tar.gz
shell> cd redis-2.8.19
shell> make

shell> src/redis-server
shell> src/redis-server /etc/redis.conf
shell> src/redis-cli

shell> sudo mkdir /etc/redis
shell> sudo mkdir /var/redis
shell> sudo cp utils/redis_init_script /etc/init.d/redis_6379
shell> sudo vi /etc/init.d/redis_6379
shell> sudo cp redis.conf /etc/redis/6379.conf
shell> sudo mkdir /var/redis/6379

[...]
daemonize yes
[...]
pidfile /var/run/redis_6379.pid
pidfile /var/run/redis/redis-server.pid
[...]
logfile /var/log/redis_6379.log
logfile /var/log/redis/redis-server.log
[...]
dir /var/lib/redis
dir /var/redis/6379

shell> sudo update-rc.d redis_6379 defaults
shell> /etc/init.d/redis_6379 start
```

```
shell> redis-cli ping
```

---

### cluster

redis.conf
```
port 7000
daemonize yes
tcp-keepalive 300
cluster-enabled yes
cluster-config-file nodes-7000.conf
cluster-node-timeout 15000
maxclients 10000
requirepass foobared
appendonly yes
protected-mode no
```


```
protected-mode no
port 6379

pidfile /var/run/redis_6379.pid

```

```
slave-serve-stale-data yes
slave-read-only yes
```

```console
shell> wget http://download.redis.io/releases/redis-3.2.1.tar.gz
shell> tar xzf redis-3.2.1.tar.gz
shell> cd redis-3.2.1  
shell> make

shell> sudo mkdir -p /srv/redis/bin
shell> sudo mkdir -p /srv/redis/etc

shell> sudo cp src/redis-server /srv/redis/bin
shell> sudo cp src/redis-cli /srv/redis/bin
shell> sudo cp src/redis-trib.rb /srv/redis/bin 

shell> sudo vi /srv/redis/etc/7000.conf
shell> sudo vi /srv/redis/etc/7001.conf
shell> sudo vi /srv/redis/etc/7002.conf
shell> sudo vi /srv/redis/etc/7003.conf
shell> sudo vi /srv/redis/etc/7004.conf
shell> sudo vi /srv/redis/etc/7005.conf

shell> /srv/redis/bin/redis-server /srv/redis/etc/7000.conf 
shell> /srv/redis/bin/redis-server /srv/redis/etc/7001.conf
shell> /srv/redis/bin/redis-server /srv/redis/etc/7002.conf
shell> /srv/redis/bin/redis-server /srv/redis/etc/7003.conf 
shell> /srv/redis/bin/redis-server /srv/redis/etc/7004.conf
shell> /srv/redis/bin/redis-server /srv/redis/etc/7005.conf

shell> /srv/redis/bin/redis-cli -p 7000 shutdown
shell> /srv/redis/bin/redis-cli -p 7001 shutdown
shell> /srv/redis/bin/redis-cli -p 7002 shutdown
shell> /srv/redis/bin/redis-cli -p 7003 shutdown
shell> /srv/redis/bin/redis-cli -p 7004 shutdown
shell> /srv/redis/bin/redis-cli -p 7005 shutdown

shell> apt-get install ruby
shell> gem install redis
shell> gem install --http-proxy http://172.24.1.10:3128 redis
shell> /srv/redis/bin/redis-trib.rb create --replicas 1 127.0.0.1:7000 127.0.0.1:7001 127.0.0.1:7002 127.0.0.1:7003 127.0.0.1:7004 127.0.0.1:7005
```


start.sh
```
#! /bin/sh

/srv/redis/bin/redis-server /srv/redis/etc/7000.conf 
/srv/redis/bin/redis-server /srv/redis/etc/7001.conf
/srv/redis/bin/redis-server /srv/redis/etc/7002.conf
/srv/redis/bin/redis-server /srv/redis/etc/7003.conf 
/srv/redis/bin/redis-server /srv/redis/etc/7004.conf
/srv/redis/bin/redis-server /srv/redis/etc/7005.conf
```

shutdown.sh
```
#! /bin/sh

/srv/redis/bin/redis-cli -p 7000 shutdown
/srv/redis/bin/redis-cli -p 7001 shutdown
/srv/redis/bin/redis-cli -p 7002 shutdown
/srv/redis/bin/redis-cli -p 7003 shutdown
/srv/redis/bin/redis-cli -p 7004 shutdown
/srv/redis/bin/redis-cli -p 7005 shutdown
```

```console
shell> /srv/redis/bin/redis-trib.rb check 127.0.0.1:7000
shell> /srv/redis/bin/redis-trib.rb info 127.0.0.1:7000
```


```
>>> Creating cluster
>>> Performing hash slots allocation on 6 nodes...
Using 3 masters:
127.0.0.1:7000
127.0.0.1:7001
127.0.0.1:7002
Adding replica 127.0.0.1:7003 to 127.0.0.1:7000
Adding replica 127.0.0.1:7004 to 127.0.0.1:7001
Adding replica 127.0.0.1:7005 to 127.0.0.1:7002
M: fec1fc65dcf5332b28e10bc94c76fda326140a20 127.0.0.1:7000
   slots:0-5460 (5461 slots) master
M: b6e221ef3b8fcf37c89360430bd9dabbec971e08 127.0.0.1:7001
   slots:5461-10922 (5462 slots) master
M: dbe32f240f94d28c281d19715ed2db9422e0da5c 127.0.0.1:7002
   slots:10923-16383 (5461 slots) master
S: 0a5d8b993bcd64fb89e6fbf6688e06e4255de322 127.0.0.1:7003
   replicates fec1fc65dcf5332b28e10bc94c76fda326140a20
S: fac1248283a706fa1310521c32754b9273b4f87d 127.0.0.1:7004
   replicates b6e221ef3b8fcf37c89360430bd9dabbec971e08
S: 54d420a1359f60f8bdfffafa2547eb4211fe574b 127.0.0.1:7005
   replicates dbe32f240f94d28c281d19715ed2db9422e0da5c
Can I set the above configuration? (type 'yes' to accept): yes
>>> Nodes configuration updated
>>> Assign a different config epoch to each node
>>> Sending CLUSTER MEET messages to join the cluster
Waiting for the cluster to join......
>>> Performing Cluster Check (using node 127.0.0.1:7000)
M: fec1fc65dcf5332b28e10bc94c76fda326140a20 127.0.0.1:7000
   slots:0-5460 (5461 slots) master
M: b6e221ef3b8fcf37c89360430bd9dabbec971e08 127.0.0.1:7001
   slots:5461-10922 (5462 slots) master
M: dbe32f240f94d28c281d19715ed2db9422e0da5c 127.0.0.1:7002
   slots:10923-16383 (5461 slots) master
M: 0a5d8b993bcd64fb89e6fbf6688e06e4255de322 127.0.0.1:7003
   slots: (0 slots) master
   replicates fec1fc65dcf5332b28e10bc94c76fda326140a20
M: fac1248283a706fa1310521c32754b9273b4f87d 127.0.0.1:7004
   slots: (0 slots) master
   replicates b6e221ef3b8fcf37c89360430bd9dabbec971e08
M: 54d420a1359f60f8bdfffafa2547eb4211fe574b 127.0.0.1:7005
   slots: (0 slots) master
   replicates dbe32f240f94d28c281d19715ed2db9422e0da5c
[OK] All nodes agree about slots configuration.
>>> Check for open slots...
>>> Check slots coverage...
[OK] All 16384 slots covered.
```

```console
shell> /srv/redis/bin/redis-trib.rb reshard 127.0.0.1:7000 
```


```console
127.0.0.1:6379> CLUSTER NODES
127.0.0.1:6379> cluster slots
```

```
1797e4a0c9e5e2c421bf18a00e455042e875140d 127.0.0.1:6384 slave ef1f99298df438efab16dd8b73a2f720eb6f6679 0 1466648732408 6 connected
39cf404caf30b44c0dc4659c0e3d6230dda2656c 127.0.0.1:6379 myself,master - 0 0 1 connected 0-5460
861c190a2fa1ff4fb401d346bedf4896f573aed7 127.0.0.1:6380 master - 0 1466648731405 2 connected 5461-10922
ef1f99298df438efab16dd8b73a2f720eb6f6679 127.0.0.1:6381 master - 0 1466648733409 3 connected 10923-16383
f00887b917cc03729d0e1f67f5dab4a2d2625779 127.0.0.1:6383 slave 861c190a2fa1ff4fb401d346bedf4896f573aed7 0 1466648734412 5 connected
67a635eacde3ed74a2c43de133f0566ed42f4afd 127.0.0.1:6382 slave 39cf404caf30b44c0dc4659c0e3d6230dda2656c 0 1466648728397 4 connected
```

```console
127.0.0.1:6379> set mykey somevalue
```
```
-> Redirected to slot [14687] located at 127.0.0.1:6381
OK
```

```console
127.0.0.1:6381> SET count 1
```
```
-> Redirected to slot [8188] located at 127.0.0.1:6380
OK
```

```console
127.0.0.1:6380> get mykey
```
```
-> Redirected to slot [14687] located at 127.0.0.1:6381
"somevalue"
```

```console
127.0.0.1:6381> get count
```
```
-> Redirected to slot [8188] located at 127.0.0.1:6380
"1"
```

```
>>> Creating cluster
*** ERROR: Invalid configuration for cluster creation.
*** Redis Cluster requires at least 3 master nodes.
*** This is not possible with 3 nodes and 1 replicas per node.
*** At least 6 nodes are required.
```

- [cluster-nodes](http://redis.io/commands/cluster-nodes)

---

### Pub/Sub

```console
redis 127.0.0.1:6379> SUBSCRIBE first
```

```console
redis 127.0.0.1:6379> PSUBSCRIBE f*
```

```console
redis 127.0.0.1:6379> PUBLISH first Hello
```

```console
redis 127.0.0.1:6379> MONITOR
```

```console
shell> redis-cli monitor
```


- [pubsub](http://redis.io/topics/pubsub)

---

```console
shell> redis-benchmark -c 10 -n 100000 -q
shell> redis-benchmark -h 127.0.0.1 -p 6379 -q -d 100
shell> redis-benchmark -h 127.0.0.1 -p 6379 -c 5000 -n 100000  
```

```
Could not connect to Redis at 127.0.0.1:7000: Can't create socket: Too many open files
```
```console
shell> ulimit -n 100000
shell> sysctl -w fs.file-max=100000
```


```
Usage: redis-benchmark [-h <host>] [-p <port>] [-c <clients>] [-n <requests]> [-k <boolean>]

 -h <hostname>      Server hostname (default 127.0.0.1)
 -p <port>          Server port (default 6379)
 -a <password>      Password for Redis Auth
 -c <clients>       Number of parallel connections (default 50)
 -n <requests>      Total number of requests (default 100000)
 -d <size>          Data size of SET/GET value in bytes (default 2)
```

- [commands](http://redis.io/commands)
- [topics](http://redis.io/topics/clients)

---



### redis-cli
```console

shell> redis-cli -h 10.27.55.209
shell> redis-cli -a password

shell> redis-cli
redis 127.0.0.1:6379> AUTH password
OK
redis 127.0.0.1:6379> ping
PONG

#
redis 127.0.0.1:6379> set mykey somevalue
OK
redis 127.0.0.1:6379> get mykey
"somevalue"

# 刪除 key  
redis 127.0.0.1:6379> DEL mykey
(integer) 1
redis 127.0.0.1:6379> get mykey
(nil)

#
redis 127.0.0.1:6379> SETEX mykey 10 somevalue
redis 127.0.0.1:6379> TTL mykey

#
redis 127.0.0.1:6379> SET count 1
redis 127.0.0.1:6379> INCR count
(integer) 2
redis 127.0.0.1:6379> INCR count
(integer) 3
redis 127.0.0.1:6379> INCR count
(integer) 4
redis 127.0.0.1:6379> get count
"4"

redis 127.0.0.1:6379> DECR count
(integer) 3
redis 127.0.0.1:6379> get count
"3"

#
redis 127.0.0.1:6379> set mykey1 1
redis 127.0.0.1:6379> set mykey2 2
redis 127.0.0.1:6379> set mykey3 3
redis 127.0.0.1:6379> set mykey4 4
redis 127.0.0.1:6379> KEYS *
1) "mykey3"
2) "mykey1"
3) "mykey4"
4) "mykey2"

# 判斷 key 是否存在。
redis 127.0.0.1:6379> EXISTS mykey1 
(integer) 1
redis 127.0.0.1:6379> EXISTS mykey9 
(integer) 0

#
redis 127.0.0.1:6379> TYPE mykey1
string
redis 127.0.0.1:6379> LPUSH mykey 1
(integer) 1

redis 127.0.0.1:6379> TYPE mykey
list


client list

```
---

### :books: 參考網站：

- [topics](http://redis.io/topics/admin)
- [5.4. 微調處理能力](https://access.redhat.com/documentation/zh-TW/Red_Hat_Enterprise_Linux/6/html/Performance_Tuning_Guide/s-memory-captun.html)
- [【直擊Modern Web 2015】開源資料庫Redis實戰經驗大公開](http://www.ithome.com.tw/news/96109)
- [加速網站存取的殺手級應用：Redis記憶體資料庫實戰訣竅大公開](http://www.ithome.com.tw/news/96023)
- [Redis Quick Start](http://redis.io/topics/quickstart)
- [Command reference](http://redis.io/commands)
- [redis](https://registry.hub.docker.com/_/redis/)
- [在 Azure Redis 快取中設定快取](http://msdn.microsoft.com/zh-tw/library/azure/dn793612.aspx)
- [http://redis.io/download](http://redis.io/download)
- [Redis Quick Start](http://redis.io/topics/quickstart)
- [如何使用 Azure Redis Cache](https://www.azure.cn/documentation/articles/cache-dotnet-how-to-use-azure-redis-cache)