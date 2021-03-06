![](https://raw.githubusercontent.com/docker-library/docs/master/mysql/logo.png)

# Table of Contents

- [getstarted](#getstarted)
- [install](#install)
- [mysqltuner](#mysqltuner)
- [storage-engines](#storage-engines)
- [federated](#federated)
- [merge-storage-engine](#merge-storage-engine)
- [create-user](#create-user) 
- [create-table](#create-table) 
- [create-view](#create-view)
- [partitioning](#partitioning)
- [trigger-syntax](#trigger-syntax)
- [sql-syntax-prepared-statements](#sql-syntax-prepared-statements)
- [sql-syntax-transactions](#sql-syntax-transactions)
- [event_scheduler](#event_scheduler)
- [find_in_set](#find_in_set)
- [mysql-config-editor](#mysql-config-editor)
- [cursors](#cursors)
- [procedure-analyse](#procedure-analyse)
- [insert-on-duplicate](#insert-on-duplicate)
- [mysql-proxy](#mysql-proxy)
- [mydumper](#mydumper)
- [replication](#replication)



---
<a name="getstarted"></a>

> **`MySQL`是一開放源碼資料庫軟體**，除了有免費下載版可用之外，也提供商用版的訂閱服務。

> `MySQL`的姊妹資料庫`MariaDB`。

> **`瑪莉亞資料庫` (`MariaDB`)如同`MySQL`的影子版本，`瑪莉亞資料庫` (`MariaDB`)是`MySQL`的一個`分支版本` (`Branch`)，而不是`衍生版本` (`Fork`)，提供的功能可和`MySQL`完全相容**。

> `MySQL`作者兼聯合創辦人`Michael Widenius` (代號`Monty`) 和其他創始人在1994年開始開發`MySQL`，2008年將`MySQL`賣給了`昇陽電腦`(`Sun`)，傳為開源軟體商業化的經典案例。

> `Michael Widenius`(網路代號：`Monty`)同為`MySQL`與`MariaDB`的創辦人，2008年他以10億美元的代價將`MySQL`出售給昇陽，兩年後甲骨文併購昇陽，`MySQL`經二度轉手。在甲骨文的經營下，原本主張開源的`MySQL`轉趨封閉，由於`Michael Widenius`對此策略不認同，因而分支出與`MySQL` 5.5完全相容的`MariaDB` 5.5。

> 2010年，`MySQL`更推出大受歡迎的5.5版，但`甲骨文` (`Oracle`)卻收購了`昇陽電腦`(`Sun`)。`MySQL`二度易主，`MySQL`社群擔心`甲骨文` (`Oracle`)箝制而紛紛出走，Michael Widenius因而推出了與`MySQL`相容的`瑪莉亞資料庫` (`MariaDB`)，而`MySQL`原有高層則成立了`SkySQL`公司，廣納舊版`MySQL`的開發工程師，來與`甲骨文` (`Oracle`)主導的`MySQL`分庭抗禮。

> 主導`MySQL`的`甲骨文` (`Oracle`)著重於追加一些華麗的新功能，而忽視了`MySQL`的穩定性與整體效率。`甲骨文` (`Oracle`)主導下的`MySQL`，在正式釋出可用版，對外揭露的資訊不足，十分缺乏透明度，而且，`甲骨文` (`Oracle`)較少修正來自使用者回報的臭蟲、也不常聽取開發社群的討論、意見與對新功能的需求，雖然`MySQL`是開放源碼的資料庫，`甲骨文` (`Oracle`)的作為，讓`MySQL`的封閉性色彩逐漸濃厚。

> 而`瑪莉亞資料庫` (`MariaDB`) 雖然`MySQL`是同源所生的程式碼，但運作的理念卻有很大的不同。`MariaDB`是由Michael Widenius領導，並囊括了許多最初開發`MySQL`的開發人員，創立目的就是為了擺脫`甲骨文` (`Oracle`)的控制。

> `甲骨文` (`Oracle`)對`MySQL`的封閉態度，加上`瑪莉亞資料庫` (`MariaDB`)和`MySQL`到目前為止其資料格式可以互通，導致許多企業都有將資料庫系統轉換的打算，例如，`維基百科`早已將資料庫從`MySQL`換成`瑪莉亞資料庫` (`MariaDB`)、而`Linux`作業系統`Red Hat`、`SUSE`也採用了`瑪莉亞資料庫` (`MariaDB`)作為其網站資料庫。

> **`瑪莉亞資料庫` (`MariaDB`)在因應複雜的查詢上，效率高過`MySQL`，而在`複製設定` (`Replication Setup`) 上的速度，`瑪莉亞資料庫` (`MariaDB`)也比`MySQL`高出許多**。

> **`MySQL`適合用管理小於1.5TB的資料，或者作為大量資料的後端備份系統**。

> **`MySQL`的優點是，簡易查詢的效率較高，對於一個簡易查詢的要求，通常能以小於500微秒 (μs) 的時間回應，此外，`MySQL`也有一個相對穩定的資料儲存層`InnoDB`，最後，`MySQL`的安裝與操作都相對容易，同時也有許多網路上的學習資源可供利用**。

> `MySQL` 5.7主要強化效能、可擴充性，與管理能力。在`SysBench`標竿測試中，基於1204個連結的Read-only Point-Selects每秒傳遞160萬次的查詢(`QPS`)，為`MySQL` 5.6的3倍。另有優化的`InnoDB`、更強大的複製能力、新的優化器、支援`JSON`、新的效能綱要(`performance schema`)與SYS綱要，改善了安全性，強化`NoSQL`能力，並擴充行動應用對地理資訊系統(`GIS`)的支援 。全新的`MySQL Router`則可藉由智慧型的`MySQL`資料庫路徑查詢以增加效能與上線時間，進而簡化應用的開發，亦針對`MySQL Fabric`提供跨語言的支援，能更方便地管理`MySQL`資料庫群組，自動化的`資料切分`(`data sharding`)則帶來高可得性與擴充性。

> `MySQL` 埠號 `3306`

### 在 `Ubuntu` 14.04 LTS 上建置 `MySQL`

<a name="install"></a>

![](https://hub.docker.com/public/images/official/ubuntu.png) + ![](https://hub.docker.com/public/images/official/mysql.png)

安裝作業系統及`MySQL`相關套件。
因本文主要介紹`MySQL`如何安裝及設定，作業系統方面就不再詳述。

```console 
shell> lsb_release -a
No LSB modules are available.
Distributor ID:	Ubuntu
Description:	Ubuntu 14.04 LTS
Release:	14.04
Codename:	trusty
```

```console
shell> MYSQL_PASSWORD=MYSQL_PASSWORD
shell> echo "mysql-server-5.5 mysql-server/root_password password ${MYSQL_PASSWORD}
mysql-server-5.5 mysql-server/root_password seen true
mysql-server-5.5 mysql-server/root_password_again password ${MYSQL_PASSWORD}
mysql-server-5.5 mysql-server/root_password_again seen true
" | debconf-set-selections
shell> DEBIAN_FRONTEND=noninteractive apt-get install -y --force-yes mysql-server
```

---

![](http://i.imgur.com/HS5iAz1.png)

### 安裝 Percona Server 5.7
```console
shell> sudo apt-key adv --keyserver keys.gnupg.net --recv-keys 8507EFA5
shell> echo "deb http://repo.percona.com/apt "$(lsb_release -sc)" main" | sudo tee /etc/apt/sources.list.d/percona.list
shell> sudo apt-get update
shell> sudo apt-get install percona-server-server-5.6
shell> sudo apt-get install percona-server-server-5.7

shell> mysql -e "CREATE FUNCTION fnv1a_64 RETURNS INTEGER SONAME 'libfnv1a_udf.so'"
shell> mysql -e "CREATE FUNCTION fnv_64 RETURNS INTEGER SONAME 'libfnv_udf.so'"
shell> mysql -e "CREATE FUNCTION murmur_hash RETURNS INTEGER SONAME 'libmurmur_udf.so'"
```

- [percona-server-server-5.7](https://www.percona.com/doc/percona-server/5.7/installation/apt_repo.html)


![](http://i.imgur.com/wtp11Uj.png)

### 安裝 
```console
shell> sudo apt-get install software-properties-common
shell> sudo apt-key adv --recv-keys --keyserver hkp://keyserver.ubuntu.com:80 0xcbcb082a1bb943db
shell> sudo add-apt-repository 'deb [arch=amd64,i386] http://nyc2.mirrors.digitalocean.com/mariadb/repo/10.1/ubuntu trusty main'

shell> sudo apt-get update
shell> sudo apt-get install mariadb-server
shell> sudo apt-get install mariadb-connect-engine-10.1
```
### :books: 參考網站： 
- [Installing Percona Server on Debian and Ubuntu](https://www.percona.com/doc/percona-server/5.6/installation/apt_repo.html)
- [mariadb](http://downloads.mariadb.org/mariadb/repositories/)
- [Adding the MariaDB YUM Repository](https://mariadb.com/kb/en/mariadb/yum/)
- [installing-and-using-mariadb-via-docker](https://mariadb.com/kb/en/mariadb/installing-and-using-mariadb-via-docker/)
- [installing-mariadb-deb-files](https://mariadb.com/kb/en/mariadb/installing-mariadb-deb-files/)

### 安裝 MySQL 5.6
```console
shell> apt-get install mysql-server-5.6
shell> netstat -tap | grep mysql

shell> sudo service mysql status
shell> sudo service mysql stop
shell> sudo service mysql start

shell> vim /etc/mysql/my.cnf
```
註解掉「bind-address」
```ini
[mysqld]
...
bind-address            = 127.0.0.1
#bind-address            = 127.0.0.1
bind-address = 10.0.0.11
```

```ini
[mysqld]
...
default-storage-engine = innodb
innodb_file_per_table
collation-server = utf8_general_ci
init-connect = 'SET NAMES utf8'
character-set-server = utf8
```

```console
shell> dpkg-reconfigure mysql-server-5.6
shell> mysql -p
```

```sql
SELECT VERSION();
```

```
+-------------------------+
| version()               |
+-------------------------+
| 5.6.17-0ubuntu0.14.04.1 |
+-------------------------+
1 row in set (0.00 sec)
```

```sql
SHOW VARIABLES LIKE "%version%";
SHOW STATUS;
```

---

<a name="mysqltuner"></a>

```console
shell> apt-get install mysqltuner
shell> mysqltuner
```

```
 >>  MySQLTuner 1.1.1 - Major Hayden <major@mhtx.net>
 >>  Bug reports, feature requests, and downloads at http://mysqltuner.com/
 >>  Run with '--help' for additional options and output filtering
Please enter your MySQL administrative login: root
Please enter your MySQL administrative password: 
Warning: Using a password on the command line interface can be insecure.
Warning: Using a password on the command line interface can be insecure.
Warning: Using a password on the command line interface can be insecure.

-------- General Statistics -------------------------
[--] Skipped version check for MySQLTuner script
[OK] Currently running supported MySQL version 5.6.19-0ubuntu0.14.04.1
[OK] Operating on 64-bit architecture

-------- Storage Engine Statistics ------------------
[--] Status: +Archive -BDB -Federated +InnoDB -ISAM -NDBCluster 
Warning: Using a password on the command line interface can be insecure.
Warning: Using a password on the command line interface can be insecure.
[--] Data in InnoDB tables: 670M (Tables: 12)
[--] Data in PERFORMANCE_SCHEMA tables: 0B (Tables: 52)
[!!] Total fragmented tables: 3

-------- Security Recommendations  ------------------
Warning: Using a password on the command line interface can be insecure.
[OK] All database users have passwords assigned
Warning: Using a password on the command line interface can be insecure.

-------- Performance Metrics ------------------------
[--] Up for: 26d 0h 8m 17s (30K q [0.014 qps], 2K conn, TX: 472M, RX: 13B)
[--] Reads / Writes: 99% / 1%
[--] Total buffers: 192.0M global + 1.1M per thread (151 max threads)
[OK] Maximum possible memory usage: 352.4M (4% of installed RAM)
[OK] Slow queries: 0% (30/30K)
[OK] Highest usage of available connections: 27% (41/151)
[OK] Key buffer size / total MyISAM indexes: 16.0M/97.0K
[OK] Key buffer hit rate: 100.0% (6M cached / 2 reads)
[!!] Query cache efficiency: 0.0% (0 cached / 39K selects)
[OK] Query cache prunes per day: 0
[OK] Sorts requiring temporary tables: 0% (35 temp sorts / 14K sorts)
[OK] Temporary tables created on disk: 1% (859 on disk / 63K total)
[OK] Thread cache hit rate: 63% (853 created / 2K connections)
[!!] Table cache hit rate: 2% (122 open / 5K opened)
[OK] Open file limit used: 0% (48/5K)
[OK] Table locks acquired immediately: 100% (69K immediate / 69K locks)
[!!] InnoDB data size / buffer pool: 670.2M/128.0M

-------- Recommendations ---
General recommendations:
    Run OPTIMIZE TABLE to defragment tables for better performance
    Increase table_cache gradually to avoid file descriptor limits
Variables to adjust:
    query_cache_limit (> 1M, or use smaller result sets)
    table_cache (> 2000)
    innodb_buffer_pool_size (>= 670M)
```

```sql
SHOW TABLE STATUS;
SELECT TABLE_SCHEMA, TABLE_NAME, DATA_FREE / 1024 / 1024 FROM information_schema.TABLES WHERE ENGINE LIKE 'InnoDB' AND DATA_FREE > 0;


SELECT TABLE_NAME, (DATA_LENGTH + INDEX_LENGTH) / 1024 / 1024 / 1024 FROM information_schema.TABLES WHERE TABLE_SCHEMA='';

OPTIMIZE TABLE foo;
ALTER TABLE test.t1 ENGINE='InnoDB'; 
```

### :books: 參考網站：
- [mysqltuner](http://mysqltuner.com/)

---
<a name="create-user"></a>

```sql
CREATE USER 'jeffrey'@'localhost' IDENTIFIED BY 'mypass';
SET PASSWORD FOR 'jeffrey'@'localhost' = PASSWORD('mypass');
GRANT ALL ON db1.* TO 'jeffrey'@'localhost';
GRANT SELECT ON db2.invoice TO 'jeffrey'@'localhost';
GRANT USAGE ON *.* TO 'jeffrey'@'localhost' WITH MAX_QUERIES_PER_HOUR 90;

CREATE USER 'root'@'%' IDENTIFIED BY 'mypass';
```

```sql
SHOW GRANTS FOR 'root'@'localhost';
SHOW GRANTS;
SHOW GRANTS FOR CURRENT_USER;
SHOW GRANTS FOR CURRENT_USER();

```

### :books: 參考網站：
- [create-user](https://dev.mysql.com/doc/refman/5.7/en/create-user.html)
- [show-grants](http://dev.mysql.com/doc/refman/5.7/en/show-grants.html)

---
<a name="storage-engines"></a>

**認識`MySQL`資料庫引擎**

- `MySQL`資料庫軟體有一個與其他資料庫軟體不同的特色，在於它提供了不同類型的資料庫引擎，以供使用者根據不同的需求來選擇，藉此提高資料庫應用的效能。
- 如果想知道`MySQL`資料庫支援那些資料庫引擎，可在登入至`MySQL`資料庫後，以`SHOW ENGINES;`指令來查詢所使用的`MySQL`資料庫能夠支援那些資料庫引擎，其中最常見的預設資料庫引擎是`MyISAM`。 
- 在`MySQL 5.5`之前的版本，當使用者新建資料庫時，預設使用的資料庫引擎為`MyISAM`，而之後則更改為`InnoDB`。

**MyISAM** 
`MyISAM`是早期`MySQL`所支援的資料庫引擎之一，其優勢在於連結執行速度快，但此種資料庫引擎並不支援`交易`(`Transaction`)功能，所謂的交易指的是資料庫確保一筆交易可完整執行的機制。 
假如一筆交易可能需要多次的資料庫動作（如新增或更新）才能完成，交易機制就需要確保當所有的資料庫動作均成功執行時才以`提交`(`Commit`)的方式來完成此項交易。 
反之，如果交易在執行途中發生問題，以致於無法完成交易，即可回復到交易之前的狀態(`Rollback`)用來回復為執行此筆交易之前所執行的動作，如更新(`Update`)、刪除(`Delete`)、新增(`Insert`)等資料庫動作。 
此種資料庫引擎主要是應用在對於無需交易要求或以查詢(`Select`)、新增(`Insert`)為主的應用，這時就可以選用此種類型。 
`MyISAM`資料表在建立後會在磁碟上新增三種類型的檔案，相關類型說明如下所述：
`.frm`：儲存資料庫表格的定義
`.MYD`：儲存資料庫表格內的記錄資料
`.MYI`：儲存資料庫表格內`索引`(`Index`)的資料 

**InnoDB**
`InnoDB`資料庫引擎提供`交易`(`Transaction`)安全的機制，可在交易無法完全執行成功時，提供`回復`(`Rollback`)功能來回復之前所執行的資料庫動作。此種的資料庫類型通常運用在對於交易的完整性有嚴格要求的應用上。 

**Memory** 
就純粹以速度來比較，記憶體的運算速度是遠超過以磁碟來運算的速度，因此`MySQL`資料庫特別提供利用`記憶體`(`Memory`)的容量來儲存資料庫表格(`Table`)的相關資料。 
使用系統記憶體來當成資料庫表格的儲存空間，最大的好處是運算速度快，但由於記憶體揮發的特性，一旦系統關機，所有儲存在記憶體的資料庫表格紀錄也會隨之被抹除。而使用記憶體來儲存，另外還有一個很大的缺點，為其可儲存的容量遠小於以磁碟來儲存。 

`TokuDB`是一種**支援交易功能且具有高效能的插入(`Insert`)功能及高資料壓縮比的資料庫引擎**，可與`MySQL`資料庫結合，提供特定的應用，通常**適用於需要經常大量寫入的應用上**。 

「工欲善其事，必先利其器」，對於資料庫的運用也是如此。以`MySQL`為例，它提供了不同的資料庫引擎來滿足不同的應用，如果**需要嚴謹之保證交易成功的機制，即可選用`InnoDB`型態**。但如果**要求的是快速的運算能力且預期資料量並不大的話，也可考慮使用`Memory`型態**。而**`TokuDB`型態，就適用於有大量的插入要求及有效縮小資料庫容量的需求**。 

![](http://i.imgur.com/GKHGeWI.png)

```sql
INSTALL SONAME 'ha_connect';
SHOW ENGINES;
```

```
+--------------------+---------+-----------------------+--------------+------+------------+
| Engine             | Support | Comment                                                                                          | Transactions | XA   | Savepoints |
+--------------------+---------+-----------------------+--------------+------+------------+
| CSV                | YES     | CSV storage engine                                                                               | NO           | NO   | NO         |
| MRG_MyISAM         | YES     | Collection of identical MyISAM tables                                                            | NO           | NO   | NO         |
| MyISAM             | YES     | MyISAM storage engine                                                                            | NO           | NO   | NO         |
| SEQUENCE           | YES     | Generated tables filled with sequential values                                                   | YES          | NO   | YES        |
| CONNECT            | YES     | Management of External Data (SQL/MED), including many file formats                               | NO           | NO   | NO         |
| MEMORY             | YES     | Hash based, stored in memory, useful for temporary tables                                        | NO           | NO   | NO         |
| PERFORMANCE_SCHEMA | YES     | Performance Schema                                                                               | NO           | NO   | NO         |
| Aria               | YES     | Crash-safe tables with MyISAM heritage                                                           | NO           | NO   | NO         |
| InnoDB             | DEFAULT | Percona-XtraDB, Supports transactions, row-level locking, foreign keys and encryption for tables | YES          | YES  | YES        |
+--------------------+---------+-----------------------+--------------+------+------------+
9 rows in set (0.00 sec)
```

```sql
CREATE TABLE t (
) ENGINE=CONNECT DEFAULT CHARSET big5 tabname='Customers' table_type=ODBC block_size=10 
CONNECTION='Driver={SQL Server Native Client 11.0};Server=192.168.31.33;Database=database;UID=UID;PWD=PWD'; 



CREATE TABLE Customer (
  CustomerID VARCHAR(5),
  CompanyName VARCHAR(40),
  ContactName VARCHAR(30),
  ContactTitle VARCHAR(30),
  Address VARCHAR(60),
  City VARCHAR(15),
  Region VARCHAR(15),
  PostalCode VARCHAR(10),
  Country VARCHAR(15),
  Phone VARCHAR(24),
  Fax VARCHAR(24))
ENGINE=connect table_type=ODBC block_size=10
tabname='Customers'
CONNECTION='DSN=MS Access Database;DBQ=C:/ProgramFiles/Microsoft Office/Office/1033/FPNWIND.MDB;';

CREATE TABLE XLCONT
ENGINE=CONNECT table_type=ODBC tabname='CONTACT'
CONNECTION='DSN=Excel Files;DBQ=D:/Ber/Doc/Contact_BP.xls;';

CREATE TABLE essai (
  num INTEGER(4) NOT NULL,
  line CHAR(15) NOT NULL)
ENGINE=CONNECT table_type=MYSQL
CONNECTION='mysql://root@localhost/test/people';

CREATE TABLE xyz (
id int(10) NOT NULL ,
name VARCHAR(50)
) ENGINE=CONNECT DEFAULT CHARSET big5 CONNECTION='Driver={SQL Server Native Client 11.0};Server=localhost;Database=MS_ABC;Uid=sa;Pwd=1234;' table_type=ODBC block_size=10 tabname='TB_XYZ'

```


```sql
CREATE TABLE t (i INT) ENGINE = INNODB;
CREATE TABLE t (i INT) TYPE = MEMORY;
CREATE TABLE t (i INT) ENGINE = MYISAM;

```

```sql
ALTER TABLE t ENGINE = MYISAM;
ALTER TABLE t TYPE = BDB;
```

### :books: 參考網站：
- [storage-engines](https://dev.mysql.com/doc/refman/5.0/en/storage-engines.html)
- [innodb-configuration](https://dev.mysql.com/doc/refman/5.0/en/innodb-configuration.html)

---

<a name="merge-storage-engine"></a>
##### The MERGE Storage Engine
```sql
CREATE DATABASE test;
USE test;

CREATE TABLE t1 (
   a INT NOT NULL AUTO_INCREMENT PRIMARY KEY,
   message CHAR(20)) ENGINE=MyISAM;
CREATE TABLE t2 (
   a INT NOT NULL AUTO_INCREMENT PRIMARY KEY,
   message CHAR(20)) ENGINE=MyISAM;
INSERT INTO t1 (message) VALUES ('Testing'),('table'),('t1');
INSERT INTO t2 (message) VALUES ('Testing'),('table'),('t2');
CREATE TABLE total (
   a INT NOT NULL AUTO_INCREMENT,
   message CHAR(20), INDEX(a))
   ENGINE=MERGE UNION=(t1,t2) INSERT_METHOD=LAST;

SELECT * FROM total;
```
```
+---+---------+
| a | message |
+---+---------+
| 1 | Testing |
| 2 | table   |
| 3 | t1      |
| 1 | Testing |
| 2 | table   |
| 3 | t2      |
+---+---------+
```

### :books: 參考網站：
- [merge-storage-engine](https://dev.mysql.com/doc/refman/5.0/en/merge-storage-engine.html)

---

<a name="federated"></a>
##### The FEDERATED Storage Engine

![FEDERATED Table Structure](http://dev.mysql.com/doc/refman/5.7/en/images/se-federated-structure.png)

表格統合 (`FEDERATED`)

```sql
SHOW PLUGINS;
```
```
+---+----------+--------------------+---------+---------+
| Name                       | Status   | Type               | Library | License |
+---+----------+--------------------+---------+---------+
| binlog                     | ACTIVE   | STORAGE ENGINE     | NULL    | GPL     |
| mysql_native_password      | ACTIVE   | AUTHENTICATION     | NULL    | GPL     |
| mysql_old_password         | ACTIVE   | AUTHENTICATION     | NULL    | GPL     |
| sha256_password            | ACTIVE   | AUTHENTICATION     | NULL    | GPL     |
| MEMORY                     | ACTIVE   | STORAGE ENGINE     | NULL    | GPL     |
| MyISAM                     | ACTIVE   | STORAGE ENGINE     | NULL    | GPL     |
| MRG_MYISAM                 | ACTIVE   | STORAGE ENGINE     | NULL    | GPL     |
| CSV                        | ACTIVE   | STORAGE ENGINE     | NULL    | GPL     |
| FEDERATED                  | DISABLED | STORAGE ENGINE     | NULL    | GPL     |
| ARCHIVE                    | ACTIVE   | STORAGE ENGINE     | NULL    | GPL     |
| BLACKHOLE                  | ACTIVE   | STORAGE ENGINE     | NULL    | GPL     |
| InnoDB                     | ACTIVE   | STORAGE ENGINE     | NULL    | GPL     |
| INNODB_TRX                 | ACTIVE   | INFORMATION SCHEMA | NULL    | GPL     |
| INNODB_LOCKS               | ACTIVE   | INFORMATION SCHEMA | NULL    | GPL     |
| INNODB_LOCK_WAITS          | ACTIVE   | INFORMATION SCHEMA | NULL    | GPL     |
| INNODB_CMP                 | ACTIVE   | INFORMATION SCHEMA | NULL    | GPL     |
| INNODB_CMP_RESET           | ACTIVE   | INFORMATION SCHEMA | NULL    | GPL     |
| INNODB_CMPMEM              | ACTIVE   | INFORMATION SCHEMA | NULL    | GPL     |
| INNODB_CMPMEM_RESET        | ACTIVE   | INFORMATION SCHEMA | NULL    | GPL     |
| INNODB_CMP_PER_INDEX       | ACTIVE   | INFORMATION SCHEMA | NULL    | GPL     |
| INNODB_CMP_PER_INDEX_RESET | ACTIVE   | INFORMATION SCHEMA | NULL    | GPL     |
| INNODB_BUFFER_PAGE         | ACTIVE   | INFORMATION SCHEMA | NULL    | GPL     |
| INNODB_BUFFER_PAGE_LRU     | ACTIVE   | INFORMATION SCHEMA | NULL    | GPL     |
| INNODB_BUFFER_POOL_STATS   | ACTIVE   | INFORMATION SCHEMA | NULL    | GPL     |
| INNODB_METRICS             | ACTIVE   | INFORMATION SCHEMA | NULL    | GPL     |
| INNODB_FT_DEFAULT_STOPWORD | ACTIVE   | INFORMATION SCHEMA | NULL    | GPL     |
| INNODB_FT_DELETED          | ACTIVE   | INFORMATION SCHEMA | NULL    | GPL     |
| INNODB_FT_BEING_DELETED    | ACTIVE   | INFORMATION SCHEMA | NULL    | GPL     |
| INNODB_FT_CONFIG           | ACTIVE   | INFORMATION SCHEMA | NULL    | GPL     |
| INNODB_FT_INDEX_CACHE      | ACTIVE   | INFORMATION SCHEMA | NULL    | GPL     |
| INNODB_FT_INDEX_TABLE      | ACTIVE   | INFORMATION SCHEMA | NULL    | GPL     |
| INNODB_SYS_TABLES          | ACTIVE   | INFORMATION SCHEMA | NULL    | GPL     |
| INNODB_SYS_TABLESTATS      | ACTIVE   | INFORMATION SCHEMA | NULL    | GPL     |
| INNODB_SYS_INDEXES         | ACTIVE   | INFORMATION SCHEMA | NULL    | GPL     |
| INNODB_SYS_COLUMNS         | ACTIVE   | INFORMATION SCHEMA | NULL    | GPL     |
| INNODB_SYS_FIELDS          | ACTIVE   | INFORMATION SCHEMA | NULL    | GPL     |
| INNODB_SYS_FOREIGN         | ACTIVE   | INFORMATION SCHEMA | NULL    | GPL     |
| INNODB_SYS_FOREIGN_COLS    | ACTIVE   | INFORMATION SCHEMA | NULL    | GPL     |
| INNODB_SYS_TABLESPACES     | ACTIVE   | INFORMATION SCHEMA | NULL    | GPL     |
| INNODB_SYS_DATAFILES       | ACTIVE   | INFORMATION SCHEMA | NULL    | GPL     |
| PERFORMANCE_SCHEMA         | ACTIVE   | STORAGE ENGINE     | NULL    | GPL     |
| partition                  | ACTIVE   | STORAGE ENGINE     | NULL    | GPL     |
+---+----------+--------------------+---------+---------+
```

```console
shell> vim /etc/mysql/my.cnf
```
```ini
[mysqld]
federated=ON
archive=OFF
```

```sql
CREATE TABLE test_table (
    id     INT(20) NOT NULL AUTO_INCREMENT,
    name   VARCHAR(32) NOT NULL DEFAULT '',
    other  INT(20) NOT NULL DEFAULT '0',
    PRIMARY KEY  (id),
    INDEX name (name),
    INDEX other_key (other)
)
ENGINE=MyISAM
DEFAULT CHARSET=latin1;
```

```sql
CREATE TABLE federated_table (
    id     INT(20) NOT NULL AUTO_INCREMENT,
    name   VARCHAR(32) NOT NULL DEFAULT '',
    other  INT(20) NOT NULL DEFAULT '0',
    PRIMARY KEY  (id),
    INDEX name (name),
    INDEX other_key (other)
)
ENGINE=FEDERATED
DEFAULT CHARSET=latin1
CONNECTION='mysql://fed_user@remote_host:9306/federated/test_table';
```

```
CONNECTION='mysql://username:password@hostname:port/database/tablename'
CONNECTION='mysql://username@hostname/database/tablename'
CONNECTION='mysql://username:password@hostname/database/tablename'
```

```sql
CREATE SERVER fedlink
FOREIGN DATA WRAPPER mysql
OPTIONS (USER 'fed_user', HOST 'remote_host', PORT 9306, DATABASE 'federated');
```
```sql
CREATE TABLE test_table (
    id     INT(20) NOT NULL AUTO_INCREMENT,
    name   VARCHAR(32) NOT NULL DEFAULT '',
    other  INT(20) NOT NULL DEFAULT '0',
    PRIMARY KEY  (id),
    INDEX name (name),
    INDEX other_key (other)
)
ENGINE=FEDERATED
DEFAULT CHARSET=latin1
CONNECTION='fedlink/test_table';
```

----------
<a name="create-table"></a>

```sql
CREATE TABLE new_tbl LIKE orig_tbl;
```

```sql
CREATE TABLE new_tbl SELECT * FROM orig_tbl;
```

```sql
CREATE TABLE t1 (t TIME(3), dt DATETIME(6));
INSERT INTO t1 VALUES (NOW(), CURRENT_TIMESTAMP);
SELECT * FROM  t1;
```

```sql
CREATE TABLE t
(
    c1 VARCHAR(20) CHARACTER SET utf8,
    c2 TEXT CHARACTER SET latin1 COLLATE latin1_general_cs
);

CREATE TABLE t
(
  c1 VARBINARY(10),
  c2 BLOB,
  c3 ENUM('a','b','c') CHARACTER SET binary
);

salary DECIMAL(5,2)


CREATE TABLE t (qty INT, price INT);

CREATE TABLE t1 (
  ts TIMESTAMP DEFAULT CURRENT_TIMESTAMP,
  dt DATETIME DEFAULT CURRENT_TIMESTAMP
);
```

```sql
CREATE TEMPORARY TABLE IF NOT EXISTS t (i INT) ENGINE = INNODB;
```

### :books: 參考網站：
- [create-table](http://dev.mysql.com/doc/refman/5.1/en/create-table.html)
- [integer-types](http://dev.mysql.com/doc/refman/5.7/en/integer-types.html)

---

```sql
CREATE TABLE t1 (jdoc JSON);
INSERT INTO t1 VALUES('{"key1": "value1", "key2": "value2"}');

SELECT JSON_TYPE('["a", "b", 1]');
SELECT JSON_TYPE('"hello"');

SELECT JSON_ARRAY('a', 1, NOW());

SELECT JSON_OBJECT('key1', 1, 'key2', 'abc');

SELECT JSON_MERGE('["a", 1]', '{"key": "value"}');

SET @j = JSON_OBJECT('key', 'value');
SELECT @j;
SELECT CHARSET(@j), COLLATION(@j);

SELECT JSON_MERGE('[1, 2]', '["a", "b"]', '[true, false]');
SELECT JSON_MERGE('{"a": 1, "b": 2}', '{"c": 3, "a": 4}');

SELECT JSON_EXTRACT('{"id": 14, "name": "Aztalan"}', '$.name');
SELECT JSON_EXTRACT('{"a": 1, "b": 2, "c": [3, 4, 5]}', '$.*');
SELECT JSON_EXTRACT('{"a": 1, "b": 2, "c": [3, 4, 5]}', '$.c[*]');
SELECT JSON_EXTRACT('{"a": {"b": 1}, "c": {"b": 2}}', '$**.b');

SET @j = '"abc"';
SELECT @j, JSON_UNQUOTE(@j);
```

```sql
CREATE TABLE jemp (
     c JSON,
     g INT GENERATED ALWAYS AS (JSON_EXTRACT(c, '$.id')),
     INDEX i (g)
);     

INSERT INTO jemp (c) VALUES
  ('{"id": "1", "name": "Fred"}'), ('{"id": "2", "name": "Wilma"}'),
  ('{"id": "3", "name": "Barney"}'), ('{"id": "4", "name": "Betty"}');

ALTER TABLE jemp ADD COLUMN `name` VARCHAR(30) GENERATED ALWAYS AS (JSON_UNQUOTE(JSON_EXTRACT(c, '$.name'))) VIRTUAL;
ALTER TABLE jemp ADD KEY `name` (`name`);

SELECT JSON_UNQUOTE(JSON_EXTRACT(c, '$.name')) AS name
     FROM jemp WHERE g > 2;
```

### :books: 參考網站：
- [json](https://dev.mysql.com/doc/refman/5.7/en/json.html)
- [json-modification-functions](https://dev.mysql.com/doc/refman/5.7/en/json-modification-functions.html)

---

```sql
USE TEST;

CREATE TABLE table1 (
     a INT NOT NULL,
     b VARCHAR(32),
     c INT AS (a mod 10) VIRTUAL,
     d VARCHAR(5) AS (left(b,5)) VIRTUAL);

INSERT INTO table1 VALUES (1, 'some text',DEFAULT,DEFAULT);
```


- [virtual-computed-columns](https://mariadb.com/kb/en/mariadb/virtual-computed-columns/)
- [data-type-defaults](https://dev.mysql.com/doc/refman/5.7/en/data-type-defaults.html)

---

<a name="trigger-syntax"></a>

```sql
CREATE TABLE account (acct_num INT, amount DECIMAL(10,2));
CREATE TABLE account_log (ts TIMESTAMP DEFAULT CURRENT_TIMESTAMP, old_acct_num INT, old_amount DECIMAL(10,2), new_acct_num INT, new_amount DECIMAL(10,2));

DELIMITER //
CREATE TRIGGER ins_account_log AFTER INSERT ON account FOR EACH ROW
BEGIN
  INSERT INTO account_log SET new_acct_num=NEW.acct_num, new_amount=NEW.amount ;
END//
DELIMITER ;

DELIMITER //
CREATE TRIGGER upd_account_log AFTER UPDATE ON account FOR EACH ROW
BEGIN
  INSERT INTO account_log SET old_acct_num=OLD.acct_num, old_amount=OLD.amount, new_acct_num=NEW.acct_num, new_amount=NEW.amount;
END//
DELIMITER ;

DELIMITER //
CREATE TRIGGER del_account_log AFTER DELETE ON account FOR EACH ROW
BEGIN
  INSERT INTO account_log SET old_acct_num=OLD.acct_num, old_amount=OLD.amount;
END//
DELIMITER ;

INSERT INTO account VALUES(137,14.98),(141,1937.50),(97,-100.00);

UPDATE account SET amount=amount*2  WHERE acct_num=137;
UPDATE account SET amount=amount*3  WHERE acct_num=141;

DELETE  FROM account WHERE acct_num=97;

SELECT * FROM account;
SELECT * FROM account_log;
```

```sql
CREATE TABLE account (acct_num INT, amount DECIMAL(10,2));

CREATE TRIGGER ins_sum BEFORE INSERT ON account FOR EACH ROW SET @sum = @sum + NEW.amount;

SET @sum = 0;
INSERT INTO account VALUES(137,14.98),(141,1937.50),(97,-100.00);
SELECT @sum AS 'Total amount inserted';

DROP TRIGGER test.ins_sum;
```

```sql
DELIMITER //
CREATE TRIGGER upd_check BEFORE UPDATE ON account
FOR EACH ROW
BEGIN
    IF NEW.amount < 0 THEN
    SET NEW.amount = 0;
    ELSEIF NEW.amount > 100 THEN
    SET NEW.amount = 100;
    END IF;
END;//
DELIMITER ;
```

### :books: 參考網站：
- [trigger-syntax](https://dev.mysql.com/doc/refman/5.7/en/trigger-syntax.html)

---

##### InnoDB File-Per-Table Mode
```console
shell> vim /etc/mysql/my.cnf
```
```ini
[mysqld]
innodb_file_per_table
```

```sql
CREATE TABLE customers (a INT, b CHAR (20), INDEX (a)) ENGINE=InnoDB;
```

##### InnoDB Performance Tuning Tips
```ini
[mysqld]
innodb_flush_log_at_trx_commit = 2
innodb_log_file_size
innodb_log_buffer_size
```
----------
##### 疑難排解 (Troubleshooting)

- 出現錯誤訊息
```
[Warning] Using unique option prefix key_buffer instead of key_buffer_size is
 deprecated and will be removed in a future release. Please use the full name instead.
```
解決方法
```console
shell> vim /etc/mysql/my.cnf
```
```ini
#key_buffer		= 16M
key_buffer_size = 16M
```

- 出現錯誤訊息
```
[Warning] TIMESTAMP with implicit DEFAULT value is deprecated. Please use 
--explicit_defaults_for_timestamp server option (see documentation for more details).
```
解決方法
```console
shell> vim /etc/mysql/my.cnf
```
```ini
explicit_defaults_for_timestamp = 1
```

- 出現錯誤訊息
```
[Warning] Using unique option prefix myisam-recover instead of myisam-recover-options is deprecated and will be remo
ved in a future release. Please use the full name instead.
```
解決方法
```console
shell> vim /etc/mysql/my.cnf
```
```ini
#myisam-recover         = BACKUP
myisam-recover-options = BACKUP
```

- 出現錯誤訊息
```
[Warning] IP address '192.168.81.9' could not be resolved: Name or service not known
```

解決方法
```console
shell> vim /etc/mysql/my.cnf
```
```ini
skip-name-resolve
```

---

<a name="insert-on-duplicate"></a>

```sql
INSERT INTO table (a,b,c) VALUES (1,2,3)
  ON DUPLICATE KEY UPDATE c=c+1;

UPDATE table SET c=c+1 WHERE a=1;
```


### :books: 參考網站：
- [insert-on-duplicate](http://dev.mysql.com/doc/refman/5.0/en/insert-on-duplicate.html)

---

<a name="create-view"></a>

```sql
CREATE TABLE t (qty INT, price INT);
INSERT INTO t VALUES(3, 50);
CREATE VIEW v AS SELECT qty, price, qty*price AS value FROM t;
SELECT * FROM v;
```
```
+------+-------+-------+
| qty  | price | value |
+------+-------+-------+
|    3 |    50 |   150 |
+------+-------+-------+
```

### :books: 參考網站：
- [create-view](https://dev.mysql.com/doc/refman/5.0/en/create-view.html)

---

### Configuring MySQL for SSL

```sql
SHOW VARIABLES LIKE 'have_ssl';
```
```
+---------------+------------+
| Variable_name | Value      |
+---------------+------------+
| have_ssl      | DISABLED   |
+---------------+------------+
```

###### Create CA certificate
```console
shell> openssl genrsa -out ca-key.pem 2048
shell> openssl req -sha1 -new -x509 -nodes -days 7305 \
       -key ca-key.pem -out ca-cert.pem \
       -subj "/C=TW/ST=Taiwan/L=TPE/O=Example Company/OU=MYCA/CN=MYCA" 
shell> openssl x509 -in ca-cert.pem -text -noout
```

###### Create server certificate, remove passphrase, and sign it
```console
shell> openssl req -sha1 -newkey rsa:2048 -nodes -days 3653 \
       -keyout mysql-server-key.pem -out mysql-server-req.pem \
       -subj "/C=TW/ST=Taiwan/L=TPE/O=Example Company/OU=MYCA/CN=mysql-server"
shell> openssl x509 -sha1 -req -set_serial 01 -in mysql-server-req.pem \
       -days 3653 -CA ca-cert.pem -CAkey ca-key.pem -out mysql-server-cert.pem
shell> openssl verify -verbose -CAfile ca-cert.pem mysql-server-cert.pem
```
出現錯誤訊息
```
SSL error: Unable to get certificate from '/etc/mysql/mysql-server-key.pem'
[Warning] Failed to setup SSL
[Warning] SSL error: Unable to get certificate
```
解決方法
```console
shell> openssl rsa -in mysql-server-key.pem -out mysql-server-key.pem
```

###### Create client certificate, remove passphrase, and sign it
```console
shell> openssl req -sha1 -newkey rsa:2048 -nodes -days 3653 \
       -keyout mysql-client-key.pem -out mysql-client-req.pem \
       -subj "/C=TW/ST=Taiwan/L=TPE/O=Example Company/OU=MYCA/CN=mysql-client"
shell> openssl x509 -sha1 -req -set_serial 01 -in mysql-client-req.pem \
       -days 3653 -CA ca-cert.pem -CAkey ca-key.pem -out mysql-client-cert.pem
shell> openssl verify -verbose -CAfile ca-cert.pem mysql-client-cert.pem
shell> openssl rsa -in mysql-client-key.pem -out mysql-client-key.pem
```

```console
shell> openssl req -sha1 -newkey rsa:2048 -nodes -days 3653 \
       -keyout jeffrey-key.pem -out jeffrey-req.pem \
       -subj "/C=TW/ST=Taiwan/L=TPE/O=Example Company/OU=MYCA/CN=jeffrey"
shell> openssl x509 -sha1 -req -set_serial 01 -in jeffrey-req.pem \
       -days 3653 -CA ca-cert.pem -CAkey ca-key.pem -out jeffrey-cert.pem
shell> openssl verify -verbose -CAfile ca-cert.pem jeffrey-cert.pem
shell> openssl rsa -in jeffrey-key.pem -out jeffrey-key.pem
```

```console
shell> vim /etc/mysql/my.cnf
```

```ini
ssl-ca=/etc/mysql/ca-cert.pem
ssl-cert=/etc/mysql/mysql-server-cert.pem
ssl-key=/etc/mysql/mysql-server-key.pem
```

```console
shell> service mysql restart
```

```sql
SHOW VARIABLES LIKE 'have_ssl';
+---------------+-------+
| Variable_name | Value |
+---------------+-------+
| have_ssl      | YES   |
+---------------+-------+
```

##### Connecting using SSL Encryption

```console
shell> mysql --ssl-ca=ca-cert.pem \
       --ssl-cert=mysql-client-cert.pem \
       --ssl-key=mysql-client-key.pem -p
```
```sql
SHOW STATUS LIKE 'Ssl_cipher';
```
```
+---------------+--------------------+
| Variable_name | Value              |
+---------------+--------------------+
| Ssl_cipher    | DHE-RSA-AES256-SHA |
+---------------+--------------------+
```

```sql
GRANT ALL ON *.* TO 'jeffrey'@'localhost'
  REQUIRE SUBJECT '/C=TW/ST=Taiwan/L=TPE/O=Example Company/OU=MYCA/CN=jeffrey';
```

```sql
GRANT ALL PRIVILEGES ON *.* TO 'root'@'%' IDENTIFIED BY 'goodsecret' REQUIRE X509;
GRANT ALL ON *.* TO 'root'@'%' REQUIRE SSL WITH GRANT OPTION;
SHOW GRANTS FOR 'root'@'%';
```

```consol0e
shell> vim ~/.my.cnf
```
```ini
[client]
port=3306
ssl-ca=ca-cert.pem
ssl-cert=mysql-client-cert.pem
ssl-key=mysql-client-key.pem
~~~~

![](http://i.imgur.com/kdFs8Bq.jpg)
![](http://i.imgur.com/MLyikpT.jpg)

```php
<?php
$mysqli = mysqli_init();
$mysqli->ssl_set ('mysql-client-key.pem', 'mysql-client-cert.pem',
                  'ca-cert.pem', NULL, NULL);
$link = mysqli_real_connect($mysqli, 'localhost', 'jeffrey',
                 'mypass', 'my_db', 3306, NULL, MYSQLI_CLIENT_SSL);
$query = "SHOW STATUS LIKE 'Ssl_cipher'";

if (!$link) {
  die('Connect Error (' . mysqli_connect_errno() . ') ' . mysqli_connect_error());
} else {
  $result = $mysqli->query($query);
  /* fetch object array */
  while ($row = $result->fetch_row()) {
    printf ("%s (%s)\n", $row[0], $row[1]);
  }

  /* free result set */
  $result->close();
}

/* close connection */
$mysqli->close();
?>
```

```php
<?php
$dsn = 'mysql:dbname=my_db;host=127.0.0.1';
$user = 'jeffrey';
$password = 'mypass';
$dbh = new PDO($dsn, $user, $password, array(
    PDO::MYSQL_ATTR_SSL_KEY => 'mysql-client-key.pem',
    PDO::MYSQL_ATTR_SSL_CERT => 'mysql-client-cert.pem',
    PDO::MYSQL_ATTR_SSL_CA => 'ca-cert.pem'
  )
);

$sql = "SHOW STATUS LIKE 'Ssl_cipher'";

$sth = $dbh->query($sql);
$result = $sth->fetch(PDO::FETCH_ASSOC);
print_r($result);

foreach ($dbh->query($sql) as $row) {
  print $row['Value'] . "\t";
  print $row['Variable_name'] . "\n";
}
?>
```
---

```sql
SELECT USER(), CURRENT_USER();
```
```
+--------------------------+---------------------+
| USER()                   | CURRENT_USER()      |
+--------------------------+---------------------+
| user2@remote.example.com | user2@%.example.com |
+--------------------------+---------------------+
```
---

```sql
SELECT @@innodb_fast_shutdown;
SET GLOBAL innodb_fast_shutdown=0;
```

---
### How to Reset the Root Password

```console
shell> service mysql stop
shell> mysqld_safe --skip-grant-tables &
shell> mysql
```

```sql
UPDATE mysql.user SET Password=PASSWORD('MyNewPass') WHERE User='root';
FLUSH PRIVILEGES;
```

```console
shell> service mysql restart
```

---

```sql
DELETE FROM tbl_name WHERE lastUpdatedTime < 1423706065 
```

```sql
DELETE FROM tbl_name WHERE lastUpdatedTime < 1423706065 ORDER BY uniqueId LIMIT 0,10000
```

---

<a name="partitioning"></a>

###  Partitioning

```sql
SHOW VARIABLES LIKE '%partition%';
```
```
+-------------------+-------+
| Variable_name     | Value |
+-------------------+-------+
| have_partitioning | YES   |
+-------------------+-------+
1 row in set (0.00 sec)
```

```sql
CREATE TABLE members (
    firstname VARCHAR(25) NOT NULL,
    lastname VARCHAR(25) NOT NULL,
    username VARCHAR(16) NOT NULL,
    email VARCHAR(35),
    joined DATE NOT NULL
)
PARTITION BY KEY(joined)
PARTITIONS 6;
```

```sql
CREATE TABLE members (
    firstname VARCHAR(25) NOT NULL,
    lastname VARCHAR(25) NOT NULL,
    username VARCHAR(16) NOT NULL,
    email VARCHAR(35),
    joined DATE NOT NULL
)
PARTITION BY RANGE( YEAR(joined) ) (
    PARTITION p0 VALUES LESS THAN (1960),
    PARTITION p1 VALUES LESS THAN (1970),
    PARTITION p2 VALUES LESS THAN (1980),
    PARTITION p3 VALUES LESS THAN (1990),
    PARTITION p4 VALUES LESS THAN MAXVALUE
);
```

### :books: 參考網站：
- [partitioning](https://dev.mysql.com/doc/refman/5.1/en/partitioning.html)
- [partitioning-types](https://dev.mysql.com/doc/refman/5.1/en/partitioning-types.html)

---

```sql
SHOW PLUGINS;
```
```
+------------+----------+----------------+---------+---------+
| Name       | Status   | Type           | Library | License |
+------------+----------+----------------+---------+---------+
| binlog     | ACTIVE   | STORAGE ENGINE | NULL    | GPL     |
| partition  | ACTIVE   | STORAGE ENGINE | NULL    | GPL     |
| ARCHIVE    | ACTIVE   | STORAGE ENGINE | NULL    | GPL     |
| BLACKHOLE  | ACTIVE   | STORAGE ENGINE | NULL    | GPL     |
| CSV        | ACTIVE   | STORAGE ENGINE | NULL    | GPL     |
| FEDERATED  | DISABLED | STORAGE ENGINE | NULL    | GPL     |
| MEMORY     | ACTIVE   | STORAGE ENGINE | NULL    | GPL     |
| InnoDB     | ACTIVE   | STORAGE ENGINE | NULL    | GPL     |
| MRG_MYISAM | ACTIVE   | STORAGE ENGINE | NULL    | GPL     |
| MyISAM     | ACTIVE   | STORAGE ENGINE | NULL    | GPL     |
| ndbcluster | DISABLED | STORAGE ENGINE | NULL    | GPL     |
+------------+----------+----------------+---------+---------+
11 rows in set (0.00 sec)
```

```sql
SELECT 
    PLUGIN_NAME as Name, 
    PLUGIN_VERSION as Version, 
    PLUGIN_STATUS as Status 
    FROM INFORMATION_SCHEMA.PLUGINS 
    WHERE PLUGIN_TYPE='STORAGE ENGINE';
```

```
+--------------------+---------+--------+
| Name               | Version | Status |
+--------------------+---------+--------+
| binlog             | 1.0     | ACTIVE |
| CSV                | 1.0     | ACTIVE |
| MEMORY             | 1.0     | ACTIVE |
| MRG_MYISAM         | 1.0     | ACTIVE |
| MyISAM             | 1.0     | ACTIVE |
| PERFORMANCE_SCHEMA | 0.1     | ACTIVE |
| BLACKHOLE          | 1.0     | ACTIVE |
| ARCHIVE            | 3.0     | ACTIVE |
| InnoDB             | 5.6     | ACTIVE |
| partition          | 1.0     | ACTIVE |
+--------------------+---------+--------+
10 rows in set (0.00 sec)
```

---

```sql
-- 建立預存程序
DELIMITER //
CREATE PROCEDURE Hello (IN `name` CHAR(20))
BEGIN
  SELECT CONCAT('Hello ', `name`, '!');
END //
DELIMITER ;

-- 執行預存程序
CALL Hello('World');
```
```
Hello World!
```

```sql
-- 建立預存程序
DELIMITER //
CREATE PROCEDURE simpleproc (OUT param1 INT)
BEGIN
  SELECT COUNT(*) INTO param1 FROM t;
END//
DELIMITER ;

-- 執行預存程序
CALL simpleproc(@a);
SELECT @a;
```
```
+------+
| @a   |
+------+
| 3    |
+------+
```

```sql
-- 建立預存程序
DELIMITER //
DROP PROCEDURE IF EXISTS `Hello`//
CREATE PROCEDURE Hello ()
BEGIN
  DECLARE `name` VARCHAR(20);
  SELECT '中文' INTO `name`;
  SELECT `name`;
END//
DELIMITER ;

-- 執行預存程序
CALL Hello(); -- ??
```

```sql
-- 建立預存程序
DELIMITER //
DROP PROCEDURE IF EXISTS `Hello`//
CREATE PROCEDURE Hello ()
BEGIN
  DECLARE `name` VARCHAR(20) CHARACTER SET utf8;
  SELECT '中文' INTO `name`;
  SELECT `name`;
END//
DELIMITER ;

-- 執行預存程序
CALL Hello(); -- 中文
```

```sql
-- 建立預存程序
DELIMITER //
CREATE FUNCTION SimpleCompare(n INT, m INT)
  RETURNS VARCHAR(20)

  BEGIN
    DECLARE s VARCHAR(20);

    IF n > m THEN SET s = '>';
    ELSEIF n = m THEN SET s = '=';
    ELSE SET s = '<';
    END IF;

    SET s = CONCAT(n, ' ', s, ' ', m);

    RETURN s;
  END //
DELIMITER ;
```

### :books: 參考網站：
- [if](https://dev.mysql.com/doc/refman/5.7/en/if.html)

---

```sql
DROP TABLE IF EXISTS tbl;
CREATE TABLE tbl (created_at DATE, id INT, num INT);

INSERT INTO tbl VALUES 
       ('2015-08-01', 1, 50718),
       ('2015-08-01', 2, 82662),
       ('2015-08-01', 3, 12666),
       ('2015-08-02', 1, 19234),
       ('2015-08-02', 2, 44641),
       ('2015-08-02', 3, 29753),
       ('2015-08-03', 1, 82385),
       ('2015-08-03', 2, 72123),
       ('2015-08-03', 3, 47293);
SELECT * FROM tbl;
```

```
created_at      id     num  
----------  ------  --------
2015-08-01       1     50718
2015-08-01       2     82662
2015-08-01       3     12666
2015-08-02       1     19234
2015-08-02       2     44641
2015-08-02       3     29753
2015-08-03       1     82385
2015-08-03       2     72123
2015-08-03       3     47293
```

```sql
SELECT created_at, 
COALESCE(GROUP_CONCAT(IF(id = 1, num, NULL)), 0) AS '1',
COALESCE(GROUP_CONCAT(IF(id = 2, num, NULL)), 0) AS '2',
COALESCE(GROUP_CONCAT(IF(id = 3, num, NULL)), 0) AS '3' 
FROM tbl GROUP BY created_at;
```

```
created_at  1       2       3       
----------  ------  ------  --------
2015-08-01  50718   82662   12666   
2015-08-02  19234   44641   29753   
2015-08-03  82385   72123   47293   
```
---

### :books: 參考網站：
- [create-procedure](https://dev.mysql.com/doc/refman/5.0/en/create-procedure.html)

---

```sql
CREATE TABLE MyTable (
  MyDecimalColumn DECIMAL(5,2) COMMENT '',
  MyNumericColumn NUMERIC(10,5) COMMENT '',
  MyNCharColumn NCHAR(15) COMMENT '',
  MyNVarCharColumn NVARCHAR(20) COMMENT '',
  MyBigIntColumn BIGINT COMMENT '',
  MyIntColumn  INT COMMENT '',
  MySmallIntColumn SMALLINT COMMENT '',
  MyTinyIntColumn TINYINT COMMENT ''
) ENGINE=InnoDB DEFAULT CHARSET=utf8 COMMENT='I''m a table comment!';

INSERT INTO MyTable VALUES (123, 12345.12, N'Test data', N'More test data', 9223372036854775807, 214483647,32767,255);

```

### :books: 參考網站：

- [資料類型](https://msdn.microsoft.com/zh-tw/library/ms187752.aspx)
- [decimal 和 numeric](https://msdn.microsoft.com/zh-tw/library/ms187746.aspx)
- [nchar 和 nvarchar](https://msdn.microsoft.com/zh-tw/library/ms186939.aspx)
- [int、bigint、smallint 和 tinyint](https://msdn.microsoft.com/zh-tw/library/ms187745.aspx)

---

```sql
LOAD DATA INFILE 'data.txt' INTO TABLE db2.my_table;
```

```console
shell> mysql -h remote.example.com \
       -u remoteuser \
       -p password \
       -e "LOAD DATA LOCAL INFILE 'file_name' INTO TABLE tbl_name CHARACTER SET utf8 FIELDS ESCAPED BY '\\\\' TERMINATED BY '\t' LINES TERMINATED BY '\n';"
```

### :books: 參考網站：

- [load-data](https://dev.mysql.com/doc/refman/5.0/en/load-data.html)
- [freebcp](https://dl.dropboxusercontent.com/u/4276183/docs/commands.html#freebcp)
- [bcp](https://dl.dropboxusercontent.com/u/4276183/docs/sqlserver.html#bcp)

---


```sql
CREATE PROCEDURE sp1 (x VARCHAR(5))
BEGIN
  DECLARE xname VARCHAR(5) DEFAULT 'bob';
  DECLARE newname VARCHAR(5);
  DECLARE xid INT;

  SELECT xname, id INTO newname, xid
    FROM table1 WHERE xname = xname;
  SELECT newname;
END;
```

```sql
CREATE PROCEDURE sp2 (x VARCHAR(5))
BEGIN
  DECLARE xname VARCHAR(5) DEFAULT 'bob';
  DECLARE newname VARCHAR(5);
  DECLARE xid INT;
  DECLARE done TINYINT DEFAULT 0;
  DECLARE cur1 CURSOR FOR SELECT xname, id FROM table1;
  DECLARE CONTINUE HANDLER FOR NOT FOUND SET done = 1;

  OPEN cur1;
  read_loop: LOOP
    FETCH FROM cur1 INTO newname, xid;
    IF done THEN LEAVE read_loop; END IF;
    SELECT newname;
  END LOOP;
  CLOSE cur1;
END;
```

### :books: 參考網站：
- [local-variable-scope](http://dev.mysql.com/doc/refman/5.6/en/local-variable-scope.html)

---

![](http://i.imgur.com/CXYPLS5.png)

<!--
![](http://i.imgur.com/lSBPuR6.png)
-->

**`查詢日誌`**
啟用此選項時，由於會記錄大量的查詢紀錄動作，因此可能造成大量的磁碟存取，以至於拖慢系統效率。

```sql
SET GLOBAL log_output = 'FILE';
SET GLOBAL general_log_file = 'host_name.log';
SET GLOBAL general_log = 'ON';
```

```sql
SET GLOBAL general_log = 'OFF';
```

**`慢查詢日誌`**
很多時候，由於不適當的SQL指令往往會造成資料庫效能低下，因為大量的資源都用來處理這些不適當的SQL指令。 
在這種情況下，可利用啟動「慢查詢日誌」記錄功能，來追蹤是否有超出所設定執行時間的SQL指令，藉此找出執行時間過長的SQL指令。 

- log_slow_queries：設定儲存慢查詢日誌的檔案 位置。
- long_query_time：設定執行時間的門檻值，一旦超過此門檻值，就會記錄該SQL指令的資訊，單位為秒。 

```sql
SET @@GLOBAL.long_query_time = 1;
SET @@GLOBAL.slow_query_log_file = 'host_name.log';
SET @@GLOBAL.slow_query_log = 1;

SHOW GLOBAL VARIABLES LIKE 'long_query_time';
SHOW GLOBAL VARIABLES LIKE 'slow_query_log_file';
SHOW GLOBAL VARIABLES LIKE 'slow_query_log';
```

```sql
SET GLOBAL slow_query_log = 'OFF';
```


### :books: 參考網站：

- [server-system-variables](https://dev.mysql.com/doc/refman/5.1/en/server-system-variables.html)
- [sysvar_slow_query_log](http://dev.mysql.com/doc/refman/5.6/en/server-system-variables.html#sysvar_slow_query_log)
- [sysvar_long_query_time](http://dev.mysql.com/doc/refman/5.6/en/server-system-variables.html#sysvar_long_query_time)
- [詳解MySQL四種Log機制 以日誌稽核解析追蹤事件](http://www.netadmin.com.tw/article_content.aspx?sn=1601120005)

---

<a name="mysql-config-editor"></a>

```console
shell> mysql_config_editor set --login-path=client --host=localhost --user=localuser --password 
shell> mysql --login-path=remote
```

.mylogin.cnf

```console
shell> mysql_config_editor print --all
```
```
[client]
user = localuser
password = *****
host = localhost
[remote]
user = remoteuser
password = *****
host = remote.example.com
```

### :books: 參考網站：

- [mysql-config-editor](http://dev.mysql.com/doc/refman/5.6/en/mysql-config-editor.html)

---

```sql
SELECT * FROM performance_schema.events_statements_summary_by_digest;
```

---

0~99999
```sql
(SELECT (t5.i*10000 + t4.i*1000 + t3.i*100 + t2.i*10 + t1.i) mynumber FROM
 (SELECT 0 i UNION SELECT 1 UNION SELECT 2 UNION SELECT 3 UNION SELECT 4 UNION SELECT 5 UNION SELECT 6 UNION SELECT 7 UNION SELECT 8 UNION SELECT 9) t1,
 (SELECT 0 i UNION SELECT 1 UNION SELECT 2 UNION SELECT 3 UNION SELECT 4 UNION SELECT 5 UNION SELECT 6 UNION SELECT 7 UNION SELECT 8 UNION SELECT 9) t2,
 (SELECT 0 i UNION SELECT 1 UNION SELECT 2 UNION SELECT 3 UNION SELECT 4 UNION SELECT 5 UNION SELECT 6 UNION SELECT 7 UNION SELECT 8 UNION SELECT 9) t3,
 (SELECT 0 i UNION SELECT 1 UNION SELECT 2 UNION SELECT 3 UNION SELECT 4 UNION SELECT 5 UNION SELECT 6 UNION SELECT 7 UNION SELECT 8 UNION SELECT 9) t4,
 (SELECT 0 i UNION SELECT 1 UNION SELECT 2 UNION SELECT 3 UNION SELECT 4 UNION SELECT 5 UNION SELECT 6 UNION SELECT 7 UNION SELECT 8 UNION SELECT 9) t5) 
```

```sql
SELECT * FROM (
(SELECT ADDDATE('1970-01-01', t5.i*10000 + t4.i*1000 + t3.i*100 + t2.i*10 + t1.i) `Date` FROM
 (SELECT 0 i UNION SELECT 1 UNION SELECT 2 UNION SELECT 3 UNION SELECT 4 UNION SELECT 5 UNION SELECT 6 UNION SELECT 7 UNION SELECT 8 UNION SELECT 9) t1,
 (SELECT 0 i UNION SELECT 1 UNION SELECT 2 UNION SELECT 3 UNION SELECT 4 UNION SELECT 5 UNION SELECT 6 UNION SELECT 7 UNION SELECT 8 UNION SELECT 9) t2,
 (SELECT 0 i UNION SELECT 1 UNION SELECT 2 UNION SELECT 3 UNION SELECT 4 UNION SELECT 5 UNION SELECT 6 UNION SELECT 7 UNION SELECT 8 UNION SELECT 9) t3,
 (SELECT 0 i UNION SELECT 1 UNION SELECT 2 UNION SELECT 3 UNION SELECT 4 UNION SELECT 5 UNION SELECT 6 UNION SELECT 7 UNION SELECT 8 UNION SELECT 9) t4,
 (SELECT 0 i UNION SELECT 1 UNION SELECT 2 UNION SELECT 3 UNION SELECT 4 UNION SELECT 5 UNION SELECT 6 UNION SELECT 7 UNION SELECT 8 UNION SELECT 9) t5) v )
WHERE `Date` BETWEEN DATE_FORMAT('2015-10-01', '%Y-%m-%d') AND DATE_FORMAT('2015-10-31', '%Y-%m-%d')
```

```sql
DELIMITER //
DROP PROCEDURE IF EXISTS `DateRange`//

CREATE PROCEDURE `DateRange`(IN StartDate CHAR(10),IN EndDate CHAR(10))
BEGIN
  DECLARE v1 INT;
  SELECT DATEDIFF(EndDate, StartDate) INTO v1;

  --Delete the t table if it exists.
  DROP TABLE IF EXISTS t;
  --Create a new table called t.
  CREATE TEMPORARY TABLE IF NOT EXISTS t (d CHAR(10)) ;

  WHILE v1 >= 0 DO
    INSERT INTO t SET d=ADDDATE(StartDate, v1);
    SET v1 = v1 - 1;
  END WHILE;
  SELECT * FROM t ORDER BY d;

END//
DELIMITER ;

CALL DateRange('2015-10-01', '2015-10-31');
```

---
<a name="pvt"></a>

```sql
CREATE TABLE t1 (VendorID INT, Employee VARCHAR(32), Orders INT);

INSERT INTO t1 VALUES (1, 'Emp1', 4);
INSERT INTO t1 VALUES (1, 'Emp2', 3);
INSERT INTO t1 VALUES (1, 'Emp3', 5);
INSERT INTO t1 VALUES (1, 'Emp4', 4);
INSERT INTO t1 VALUES (1, 'Emp5', 4);

INSERT INTO t1 VALUES (2, 'Emp1', 4);
INSERT INTO t1 VALUES (2, 'Emp2', 1);
INSERT INTO t1 VALUES (2, 'Emp3', 5);
INSERT INTO t1 VALUES (2, 'Emp4', 5);
INSERT INTO t1 VALUES (2, 'Emp5', 5);

INSERT INTO t1 VALUES (3, 'Emp1', 4);
INSERT INTO t1 VALUES (3, 'Emp2', 3);
INSERT INTO t1 VALUES (3, 'Emp3', 5);
INSERT INTO t1 VALUES (3, 'Emp4', 4);
INSERT INTO t1 VALUES (3, 'Emp5', 4);

INSERT INTO t1 VALUES (4, 'Emp1', 4);
INSERT INTO t1 VALUES (4, 'Emp2', 2);
INSERT INTO t1 VALUES (4, 'Emp3', 5);
INSERT INTO t1 VALUES (4, 'Emp4', 5);
INSERT INTO t1 VALUES (4, 'Emp5', 4);

INSERT INTO t1 VALUES (5, 'Emp1', 5);
INSERT INTO t1 VALUES (5, 'Emp2', 1);
INSERT INTO t1 VALUES (5, 'Emp3', 5);
INSERT INTO t1 VALUES (5, 'Emp4', 5);
INSERT INTO t1 VALUES (5, 'Emp5', 5);

SELECT * FROM t1;
```

```
VendorID  Employee  Orders  
--------  --------  --------
       1  Emp1             4
       1  Emp2             3
       1  Emp3             5
       1  Emp4             4
       1  Emp5             4
       2  Emp1             4
       2  Emp2             1
       2  Emp3             5
       2  Emp4             5
       2  Emp5             5
       3  Emp1             4
       3  Emp2             3
       3  Emp3             5
       3  Emp4             4
       3  Emp5             4
       4  Emp1             4
       4  Emp2             2
       4  Emp3             5
       4  Emp4             5
       4  Emp5             4
       5  Emp1             5
       5  Emp2             1
       5  Emp3             5
       5  Emp4             5
       5  Emp5             5
       1  Emp1             4
       1  Emp2             3
       1  Emp3             5
       1  Emp4             4
       1  Emp5             4
       2  Emp1             4
       2  Emp2             1
       2  Emp3             5
       2  Emp4             5
       2  Emp5             5
       3  Emp1             4
       3  Emp2             3
       3  Emp3             5
       3  Emp4             4
       3  Emp5             4
       4  Emp1             4
       4  Emp2             2
       4  Emp3             5
       4  Emp4             5
       4  Emp5             4
       5  Emp1             5
       5  Emp2             1
       5  Emp3             5
       5  Emp4             5
       5  Emp5             5
```

```sql
SELECT VendorID, 
COALESCE(GROUP_CONCAT(DISTINCT IF(Employee = 'Emp1', Orders, NULL)), 0) AS 'Emp1',
COALESCE(GROUP_CONCAT(DISTINCT IF(Employee = 'Emp2', Orders, NULL)), 0) AS 'Emp2',
COALESCE(GROUP_CONCAT(DISTINCT IF(Employee = 'Emp3', Orders, NULL)), 0) AS 'Emp3',
COALESCE(GROUP_CONCAT(DISTINCT IF(Employee = 'Emp4', Orders, NULL)), 0) AS 'Emp4',
COALESCE(GROUP_CONCAT(DISTINCT IF(Employee = 'Emp5', Orders, NULL)), 0) AS 'Emp5'
FROM t1 GROUP BY VendorID;

SELECT VendorID, 
MAX(IF(Employee='Emp1',Orders, NULL)) AS 'Emp1',
MAX(IF(Employee='Emp2',Orders, NULL)) AS 'Emp2',
MAX(IF(Employee='Emp3',Orders, NULL)) AS 'Emp3',
MAX(IF(Employee='Emp4',Orders, NULL)) AS 'Emp4',
MAX(IF(Employee='Emp5',Orders, NULL)) AS 'Emp5'
FROM t1 GROUP BY VendorID;
```

```
VendorID    Emp1    Emp2    Emp3    Emp4    Emp5  
--------  ------  ------  ------  ------  --------
       1       4       3       5       4         4
       2       4       1       5       5         5
       3       4       3       5       4         4
       4       4       2       5       5         4
       5       5       1       5       5         5
```

- [使用 PIVOT 和 UNPIVOT](https://technet.microsoft.com/zh-tw/library/ms177410(v=sql.105).aspx)

---

<a name="sql-syntax-prepared-statements"></a>

```sql
PREPARE stmt1 FROM 'SELECT SQRT(POW(?,2) + POW(?,2)) AS hypotenuse';
SET @a = 3;
SET @b = 4;
EXECUTE stmt1 USING @a, @b;
DEALLOCATE PREPARE stmt1;
```

```sql
SET @s = 'SELECT SQRT(POW(?,2) + POW(?,2)) AS hypotenuse';
PREPARE stmt2 FROM @s;
SET @a = 6;
SET @b = 8;
EXECUTE stmt2 USING @a, @b;
DEALLOCATE PREPARE stmt2;
```

```sql
USE test;
CREATE TABLE t1 (a INT NOT NULL);
INSERT INTO t1 VALUES (4), (8), (11), (32), (80);


SET @table = 't1';
SET @s = CONCAT('SELECT * FROM ', @table);

PREPARE stmt3 FROM @s;
EXECUTE stmt3;

DEALLOCATE PREPARE stmt3;
```

### :books: 參考網站：

- [sql-syntax-prepared-statements](http://dev.mysql.com/doc/refman/5.7/en/sql-syntax-prepared-statements.html)

---

<a name="event_scheduler"></a>

```sql
SELECT @@event_scheduler;

SET GLOBAL event_scheduler = ON;
SET @@global.event_scheduler = ON;
SET GLOBAL event_scheduler = 1;
SET @@global.event_scheduler = 1;


SET GLOBAL event_scheduler = OFF;
SET @@global.event_scheduler = OFF;
SET GLOBAL event_scheduler = 0;
SET @@global.event_scheduler = 0;


SHOW PROCESSLIST;

GRANT EVENT ON myschema.* TO jon@ghidora;
GRANT EVENT ON *.* TO jon@ghidora;


CREATE TABLE mytable (dt DATETIME(6));

CREATE EVENT e_store_ts
    ON SCHEDULE
      EVERY 10 SECOND
    DO
      INSERT INTO myschema.mytable VALUES (NOW());

CREATE EVENT e_insert
    ON SCHEDULE
      EVERY 7 SECOND
    DO
      INSERT INTO myschema.mytable;

-- 每天 00:05 執行
DROP EVENT IF EXISTS myevent;

DELIMITER //
CREATE EVENT myevent
    ON SCHEDULE 
      EVERY 1 DAY STARTS DATE_ADD(DATE_ADD(CURDATE(), INTERVAL 1 DAY), INTERVAL 5 MINUTE) 
    ON  COMPLETION  PRESERVE  ENABLE
    COMMENT 'A sample comment.'
    DO
      BEGIN
        CALL MyProc();
      END//
DELIMITER ;
 
-- 每天 00:05 執行
-- EVERY 1 DAY STARTS DATE_ADD(DATE_ADD(CURDATE(), INTERVAL 1 DAY), INTERVAL 5 MINUTE)
-- 每天 03:00 執行 
-- EVERY 1 DAY STARTS DATE_ADD(DATE_ADD(CURDATE(), INTERVAL 1 DAY), INTERVAL 3 HOUR) 



ALTER EVENT myevent ON COMPLETION PRESERVE DISABLE;
ALTER EVENT myevent ON COMPLETION PRESERVE ENABLE;
DROP EVENT [IF EXISTS] myevent;


DELETE FROM mysql.event
    WHERE db = 'myschema'
      AND definer = 'jon@ghidora'
      AND name = 'e_insert';

```

### :books: 參考網站：
- [events-configuration](https://dev.mysql.com/doc/refman/5.7/en/events-configuration.html)
- [events-privileges](https://dev.mysql.com/doc/refman/5.7/en/events-privileges.html)

---

<a name="sql-syntax-transactions"></a>

```sql
START TRANSACTION;
SELECT @A:=SUM(salary) FROM table1 WHERE type=1;
UPDATE table2 SET summary=@A WHERE type=1;
COMMIT;
```

### :books: 參考網站：
- [sql-syntax-transactions](http://dev.mysql.com/doc/refman/5.7/en/sql-syntax-transactions.html)

---
<a name="find_in_set"></a>

### :books: 參考網站：
- [find_in_set](https://mariadb.com/kb/en/mariadb/find_in_set/)

---

### :books: 參考網站：
- [validate-password-plugin](http://dev.mysql.com/doc/refman/5.6/en/validate-password-plugin.html)
- [ha-memcached-install](http://dev.mysql.com/doc/refman/5.7/en/ha-memcached-install.html)

---

<a name="procedure-analyse"></a>

```sql
SELECT ... FROM ... WHERE ... PROCEDURE ANALYSE([max_elements,[max_memory]])
SELECT col1, col2 FROM table1 PROCEDURE ANALYSE(10, 2000);
```

### :books: 參考網站：
- [procedure-analyse](http://dev.mysql.com/doc/refman/5.7/en/procedure-analyse.html)

---

<a name="cursors"></a>

```sql
CREATE PROCEDURE curdemo()
BEGIN
  DECLARE done INT DEFAULT FALSE;
  DECLARE a CHAR(16);
  DECLARE b, c INT;
  DECLARE cur1 CURSOR FOR SELECT id,data FROM test.t1;
  DECLARE cur2 CURSOR FOR SELECT i FROM test.t2;
  DECLARE CONTINUE HANDLER FOR NOT FOUND SET done = TRUE;

  OPEN cur1;
  OPEN cur2;

  read_loop: LOOP
    FETCH cur1 INTO a, b;
    FETCH cur2 INTO c;
    IF done THEN
      LEAVE read_loop;
    END IF;
    IF b < c THEN
      INSERT INTO test.t3 VALUES (a,b);
    ELSE
      INSERT INTO test.t3 VALUES (a,c);
    END IF;
  END LOOP;

  CLOSE cur1;
  CLOSE cur2;
END;
```

### :books: 參考網站：
- [cursors](https://dev.mysql.com/doc/refman/5.7/en/cursors.html)

---

```sql
SHOW  GLOBAL  STATUS LIKE 'Questions';
```

[Queries_per_second](https://en.wikipedia.org/wiki/Queries_per_second)


```sql
SHOW VARIABLES LIKE 'long_query_time';
SET GLOBAL slow_query_log = ON;
```

---

```sql
SELECT REGEXP_SUBSTR('ab12cd','[0-9]+');
-> 12

SELECT REGEXP_SUBSTR(
  'See https://mariadb.org/en/foundation/ for details',
  'https?://[^/]*');
-> https://mariadb.org
SELECT REGEXP_SUBSTR('ABC','b');
-> B

SELECT REGEXP_SUBSTR('ABC' COLLATE utf8_bin,'b');
->

SELECT REGEXP_SUBSTR(BINARY'ABC','b');
->

SELECT REGEXP_SUBSTR('ABC','(?i)b');
-> B

SELECT REGEXP_SUBSTR('ABC' COLLATE utf8_bin,'(?+i)b');
-> B
```

### :books: 參考網站：
- [regexp_substr](https://mariadb.com/kb/en/mariadb/regexp_substr/)

---

---
<a name="mysql-proxy"></a>

mysql-proxy - high availability, load balancing and query modification for mysql

```console
shell> sudo apt-get update
shell> sudo apt-get install mysql-proxy
shell> dpkg -L mysql-proxy
```

/etc/default/mysql-proxy
```
ENABLED="true"
OPTIONS="--defaults-file=/etc/mysql/mysql-proxy.cnf"
```

/etc/mysql/mysql-proxy.cnf
```
[mysql-proxy]
daemon = true
user = mysql
proxy-skip-profiling = true
keepalive = true
max-open-files = 2048
event-threads = 50
pid-file = /var/run/mysql-proxy.pid
log-file = /var/log/mysql-proxy.log
log-level = debug

admin-address = :4041
admin-username = root
admin-password = password
admin-lua-script = /usr/lib/mysql-proxy/lua/admin.lua

proxy-address = :4040
proxy-backend-addresses = 192.168.0.1:3306
proxy-read-only-backend-addresses = 192.168.0.2:3306
proxy-lua-script = /usr/lib/mysql-proxy/lua/proxy/balance.lua

```

```console
shell> sudo chmod 0660 /etc/mysql/mysql-proxy.cnf
shell> sudo service mysql-proxy start 
```

```console
shell> mysql -P4040 -uroot -p 
```

### :books: 參考網站：
- [mysql-proxy-en](http://downloads.mysql.com/docs/mysql-proxy-en.pdf)

---

<a name="mydumper"></a>

mydumper - High-performance MySQL backup tool

```console
shell> sudo apt-get update
shell> sudo apt-get install mydumper
```

```console
shell> mydumper -u root -p mypass -B mysql -o mysql
shell> myloader -u root -p mypass -B mysql -d mysql
```

---
<a name="replication"></a>

my.cnf
```ini
[mysqld]
server-id=1
log-bin=mysql-bin
binlog_format=MIXED
binlog-do-db=database_name
binlog-ignore-db=database_name
innodb_flush_log_at_trx_commit=1
sync_binlog=1
```

```console
shell> service mysql restart
```

```sql
CREATE USER 'repl'@'%.mydomain.com' IDENTIFIED BY 'slavepass';
GRANT REPLICATION SLAVE ON *.* TO 'repl'@'%.mydomain.com';

FLUSH TABLES WITH READ LOCK;
SHOW MASTER STATUS;
```

```console
shell> mysqldump --all-databases --master-data > dbdump.db
```

my.cnf
```ini
[mysqld]
server-id=2
replicate-do-db=db_name
report-host=host_name
replicate-ignore-db=db_name
replicate-do-table=name
replicate-wild-do-table=foo%.bar%
master-connect-retry=60
```

```console
shell> service mysql restart
```

```sql
STOP SLAVE;
RESET SLAVE ALL;
```

```console
shell> mysql < dbdump.db
```

```
CHANGE MASTER TO
     MASTER_HOST='master_host_name',
     MASTER_USER='replication_user_name',
     MASTER_PASSWORD='replication_password',
     MASTER_LOG_FILE='recorded_log_file_name',
     MASTER_LOG_POS=recorded_log_position;
```

```sql
START SLAVE; 
```

```sql
UNLOCK TABLES; 
```

```sql
SET GLOBAL binlog_format = 'STATEMENT';
SET GLOBAL binlog_format = 'ROW';
SET GLOBAL binlog_format = 'MIXED';

SET SESSION binlog_format = 'STATEMENT';
SET SESSION binlog_format = 'ROW';
SET SESSION binlog_format = 'MIXED';
```

```sql
PURGE BINARY LOGS TO 'mariadb-bin.000063';
PURGE BINARY LOGS BEFORE '2013-04-22 09:55:22';
```

- [replication](http://dev.mysql.com/doc/refman/5.7/en/replication.html)
- [using-and-maintaining-the-binary-log](https://mariadb.com/kb/en/mariadb/using-and-maintaining-the-binary-log/)
- [option_mysqld_report-host](http://dev.mysql.com/doc/refman/5.7/en/replication-options-slave.html#option_mysqld_report-host)

---
<a name="mysqlslap"></a>
**mysqlslap - load emulation client**

```console
shell> mysqlslap
shell> mysqlslap --delimiter=";" --create="CREATE TABLE a (b int);INSERT INTO a VALUES (23)" --query="SELECT * FROM a" --concurrency=50 --iterations=200
shell> mysqlslap --concurrency=5 --iterations=5 --query=query.sql --create=create.sql --delimiter=";"
shell> mysqlslap --user=root --password=insecure --auto-generate-sql --verbose --host=localhost
shell> mysqlslap --user=root --password=insecure --auto-generate-sql --concurrency=50 --iterations=200 --verbose --host=localhost 
```

```
Benchmark
        Average number of seconds to run all queries: 0.358 seconds
        Minimum number of seconds to run all queries: 0.230 seconds
        Maximum number of seconds to run all queries: 0.938 seconds
        Number of clients running queries: 50
        Average number of queries per client: 0
```


---

### :books: 參考網站：
- [percona-monitoring-plugins](https://www.percona.com/downloads/percona-monitoring-plugins/LATEST/)
- [installing-templates](https://www.percona.com/doc/percona-monitoring-plugins/1.0/cacti/installing-templates.html)

---

### :books: 參考網站：
- [mysqldumpslow](http://dev.mysql.com/doc/refman/5.7/en/mysqldumpslow.html)

---

「`使用者自訂函數`」 (User-Defined Function, `UDF`)

使用`MySQL`時，只要撰寫程式的內容符合`UDF`架構的規範，即可撰寫自定義的函數來提升`MySQL`的功能。

![](http://i.imgur.com/igMbwjJ.png)

### :books: 參考網站：
- [安裝UDF程式庫 現成MySQL功能輕鬆擴充](http://www.netadmin.com.tw/article_content.aspx?sn=1304290003)

---
> `甲骨文` (`Oracle`)在2010年底發布了`MySQL`的改版，5.5版中有不少重大的更新，例如：將原本預設的資料表儲存引擎由`MyISAM`更改成`InnoDB`、提供更多的分區選項、對多處理器核心系統效能的改進、支援`半同步複製功能` (`Semi-Synchronous Replication`)、加強資料毀壞修復的能力等。

> `MySQL`高可用性架構搭配使用`InnoDB`儲存引擎，更能達到一致性要求。因為`InnoDB`有Crash Safe功能，當主機發生故障時，可保證還在處理的資料能完全寫入，而且具有一致性。

> 5.1版之前，`MyISAM`一直是預設的儲存引擎，雖然它有著快速、簡單的特性，卻不支援`Transaction`（交易）的特性（不可分割、一致、隔離、耐久，簡稱為`ACID`）、`Foreign Key`（`外鍵`）等功能，但`InnoDB`都有，在5.5版中`MySQL`正式將`InnoDB`更改為預設的儲存引擎。

> `InnoDB`支援了`Transaction`的上述4種特性，它的特色是將數個`SQL`指令視為一個整體執行，只要其中一個指令錯誤，就會取消掉所有步驟，舉個例子，假設你正在提款機前操作某項交易，如果在過程中某個步驟發生錯誤，例如停電，則系統會取消掉整筆交易，而不是取消該步驟，這對於交易來說是一個很重要的安全機制；它同時支援`Foreign Key`，可以將數個資料表連結，而這最主要的功能就是確保資料的一致性；`InnoDB`也支援`資料列鎖定`（`Row-level locking`），如果有使用者正在操作一張資料表，那麼`InnoDB`會鎖定對方目前在存取的資料列，而非鎖定整個資料表，如此若別人存取同資料表的其他資料列就不會受影響。

> `MySQL`在5.5版中更進一步加強了`InnoDB`儲存引擎的功能，例如改善資料毀壞修復，過去如果資料庫發生了資料損壞，可能要數小時的修復時間，現在只要幾分鐘就能完成。另外針對資料庫暫存區的改進，現在`MySQL`可以新增多個暫存區（Multiple Buffer Pool Instances）──Buffer Pool是記憶體中的暫存區塊，將資料放在這個暫存區可以增加存取的速度，不過如果同時有多個執行?對暫存區進行存取，就會造成傳輸的瓶頸，而MySQL 5.5版允許使用者可以開啟最多64個暫存區，以改善這個問題，進而增加存取性能，同時管理者也可以自由設定暫存區的大小。

> 一般資料庫若沒有分區功能，又想將資料分散儲存，它可能必須將資料庫或資料表移動分散到不同的磁碟，然後利用連結指向這些位置，以提升系統的速度。而`分區`（`Partition`）則是更進階的作法，它是將資料表中同個屬性的欄或列進行分割，在不同的地方儲存成單獨的資料表，例如：我們可以將某資料表中不常使用到的欄位分配到同一個分區，這樣可以減少搜尋資料表的時間；另外，在搜尋資料時，資料庫系統如果知道要搜尋的資料在那個分區，就可以直接到該分區找，這樣會比搜尋整個資料表快。

> `MySQL`先前就有分區功能，在5.5版又有一些強化，例如：在5.1版中不支援對非整數類型例如Date（日期）分區，必須使用函數進行轉換，在5.5版中則可以對日期直接進行分區，而不需再透過函數，同時也加入了`TRUNCATE PARTITION`指令。

> 以往要刪除分區裡的資料只能用`DROP PARTITION`指令，該指令可以刪除分區的資料但同時也會將分區刪除，如果資料庫系統管理員想刪除分區的某部份資料，但又想保留分區本身就會非常麻煩，現在有了`TRUNCATE PARTITION`指令可以刪除分區資料，同時又保留分區本身，這對於管理員來說相當有幫助。

> 支援半同步複製也是新版才有的機制。在5.5版之前，`MySQL`只支援非同步複製，也就是說`Master`（`主要資料庫`）在使用者送來一個操作請求時，先將該操作處理完畢回覆給使用者，再將該記錄傳送給`Slave`（`備份資料庫`），**缺點是兩套資料庫之間的內容會有時間差，如果主要資料庫發生資料毀損，而備份資料庫的資料還沒更新到與主資料庫資料一致的情形下，那麼就無法靠備用資料庫維持資料一致性**。

> 而在5.5版中，`MySQL`提供了`半同步複製機制`(`Semi-Synchronous Replication`)，這個功能可以保證資料在主從伺服器同時傳入資料的情況下，將結果回傳給使用者，而**所謂的半同步，是指它只保證資料已經傳到備份資料庫上，卻不保證資料在備份資料庫上執行完成，所以還是有可能會發生資料不同步的狀況發生**。

> `MySQL` 5.5版本已經推出且穩定運行了一段時間，而5.6版也即將推出，預計會加入全文檢索及支援`NoSQL `，會是一個重大更新。

> `甲骨文` (`Oracle`) 釋出開放源碼的最新關聯性資料庫版本`MySQL` 5.7.4 `開發者里程碑版` (`Development Milestone Release, DMR`)，強調為了符合現代雲端與嵌入應用的需求，大幅改善了`MySQL`的效能、擴展性與可靠性，在標竿測試中其查詢速度是`MySQL` 5.6的兩倍、`MySQL` 5.5的3倍。

> 在效能與擴展性上，`MySQL` 5.7.4針對`固態硬碟`強化了效能與吞吐量，改善`InnoDB`緩衝區與元資料鎖定，強化其`半同步的複製`效能，其每秒查詢速度是5.6版的2倍，5.5版的3倍。在管理功能上，帶來更精確的成本計算，改善效能架構，並有符合`AES`標準的256bit加密及新的密碼管理選項。

> `甲骨文` (`Oracle`) 發表`MySQL Fabric`，這是一個可用來管理眾多`MySQL`伺服器的開放源碼延伸框架，強調高可得性與擴充能力，為甲骨文`MySQL Utilities` 1.4.3的元件之一。

> `MySQL Fabric`具備自動化的故障偵測、資料切割 (`Sharding`) 能力，也支援`PHP`、`Python`及`Java`連結器(`Connector`)。**它能夠監控主要的資料庫，在發現該資料庫伺服器故障時，可立即遴選其他資料庫當作主資料庫；還能自動把交易傳送到主資料庫，並保持從屬資料庫的查詢負載平衡，可自應用程式清楚檢視資料庫伺服器的拓撲結構及狀態**。

> 把資料庫切割成分片（`shards`）並放置到不同伺服器的用意在於疏解單一伺服器的負載，並改善效能。其自動化的資料切割與重新切割能力允許表格的讀寫可橫向擴展；可選擇所要切割的表格及指定切割欄位；或是把既有已切割的分片移到新的伺服器或再拆分這些分片。

> `MySQL` 5.5是在2010年12月發表，`MySQL` 5.6則於2013年2月釋出。

> Web2.0概念的成熟發展促成了`NoSQL`資料庫的興起。過去幾年使用者網路行為的改變，挑戰了`關聯式資料庫`的效能和彈性，因應爆量讀寫頻繁的需求，`NoSQL`的概念重新被提出，`NoSQL`資料庫的特色是不使用`SQL`當作查詢語言、動態列儲存及分散式架構等。

> `關聯式資料庫`的操作具有`ACID`的特性，第一、`不可分割性` (`Atomicity`)，在一次的`交易` (`Transaction`)，操作必須全部成功，一旦發生錯誤，所有資料更動將回復到交易之前，不容許有中間狀態，第二、`一致性` (`Consistency`)，所有的`交易`，都必須遵守資料庫設定規則，第三、`獨立性`  (`Isolation`) 資料交易進行中，不受其他交易影響，第四、`持久性` (`Durability`)，交易成功後，所做的任何變更都會被永久保存。這些特性在金融交易很重要，可以確保其過程安全及結果的可靠性，而過去的靜態網頁的資料庫操作，讀取比例遠高於寫入，在關聯式資料庫也是沒有問題的。

> 但近年盛行的網路服務，如社群網站、社群遊戲甚至是網路遊戲，龐大的使用者規模以及頻繁互動的操作模式，`關聯式資料庫`的可靠性無用武之地，反而成為效能瓶頸。

> `NoSQL`資料庫因其`分散式架構`，容量容易擴充，但資料更新可能會有不同步的狀況，對此`NoSQL`資料庫採用`資料遲早會一致` (`Eventually Consistency`) 的做法，不同資料庫伺服器，或許資料會因時間差而不同，但終究會同步。

> `關聯式資料庫`必須遵守`ACID`的特性，`NoSQL`資料庫應用上更具彈性，**兩類型資料庫系統沒有優劣之分，只有需求考量不同**。

---

> 資料庫的設計是採取主從 (Master/Slave) 架構，並沒有考量到高可用性。這種架構的好處是，讀取與寫入分別由不同主機負責，因此，當使用者端的資料寫入`Master`主機後，會進一步複寫到`Slave`主機，等到使用者端需要讀取資料時，就可直接由`Slave`主機回應，藉此達到降低`Master`主機負載的目標。

> 然而，這種架構的設計，因為只有一臺`Master`主機，沒有考量到高可用性，只要`Master`主機發生故障，就會影響到網站服務。

> `MySQL`使用`memcached`分散式快取系統相容的`API`作為`NoSQL`，透過該程式介面可以直接驅動`InnoDB`儲存引擎，大幅提昇讀取速度。另外，`memcached`的資料都是儲存在記憶體之中，因此執行效率遠高於一般放置於硬碟的`SQL`資料庫。

---

### :books: 參考網站：

- [MariaDB 10新版大躍進](http://www.ithome.com.tw/news/86622)
- [A Quick Guide to Using the MySQL APT Repository](http://dev.mysql.com/doc/mysql-apt-repo-quick-guide/en/)
- [甲骨文發表MySQL 5.7：效能比5.6版快三倍](http://www.ithome.com.tw/news/99416)
- [percona-xtrabackup](https://www.percona.com/software/mysql-database/percona-xtrabackup)
- [percona-xtradb-cluster] (https://www.percona.com/software/mysql-database/percona-xtradb-cluster)
- [提高MySQL效能及壓縮率  以TokuDB優化Log資料庫](http://www.netadmin.com.tw/article_content.aspx?sn=1507020002)
- [資料庫管理系統｜MySQL 5.5 Community Edition 新增半同步複製機制](http://www.ithome.com.tw/node/69364)
- [威脅資料存取的SQL Injection](http://www.ithome.com.tw/node/66384)
- [甲骨文新版 MySQL帶來兩倍查詢速度](http://www.ithome.com.tw/news/86373)
- [Google棄甲骨文MySQL，將大規模導入MariaDB](http://www.ithome.com.tw/node/82854)
- [甲骨文發表可強化資料庫延展性的MySQL Fabric](http://www.ithome.com.tw/news/88179)
- [痞客邦導入MySQL 檢索1億張照片也沒問題](http://www.ithome.com.tw/tech/87416)
- [Oracle釋出MySQL 5.6　增加添NoSQL功能](http://www.ithome.com.tw/node/67003)
- [ALTER TABLE Partition Operations](http://docs.oracle.com/cd/E17952_01/refman-5.5-en/alter-table-partition-operations.html)
- [MySQL](https://help.ubuntu.com/12.04/serverguide/mysql.html)
- [Transportable Tablespace Examples](https://dev.mysql.com/doc/refman/5.7/en/innodb-transportable-tablespace-examples.html)
- [Assigning Account Passwords](http://dev.mysql.com/doc/refman/5.0/en/assigning-passwords.html)
- [Setting Up SSL Certificates and Keys for MySQL](http://dev.mysql.com/doc/refman/5.0/en/creating-ssl-certs.html)
- [http://dev.mysql.com/doc/refman/5.1/en/using-ssl-connections.html](http://dev.mysql.com/doc/refman/5.1/en/using-ssl-connections.html)
- [MySQL Documentation: Other MySQL Documentation](http://dev.mysql.com/doc/index-other.html)
- [innodb_flush_log_at_trx_commit](http://dev.mysql.com/doc/refman/5.1/en/innodb-parameters.html#sysvar_innodb_flush_log_at_trx_commit)
- [http://dev.mysql.com/doc/refman/5.1/en/innodb-tuning.html](http://dev.mysql.com/doc/refman/5.1/en/innodb-tuning.html)
- [http://dev.mysql.com/doc/refman/5.6/en/optimizing-innodb.html](http://dev.mysql.com/doc/refman/5.6/en/optimizing-innodb.html)
- [Setup MySQL Master-Slave Replication on Debian/Ubuntu](https://www.vultr.com/docs/setup-mysql-master-slave-replication-on-debian-ubuntu)
- [Reset MySQL Root Password on Debian/Ubuntu](https://www.vultr.com/docs/reset-mysql-root-password-on-debian-ubuntu)
- [DELETE Syntax](http://dev.mysql.com/doc/refman/5.0/en/delete.html)
