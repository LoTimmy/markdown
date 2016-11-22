![](https://raw.githubusercontent.com/docker-library/docs/master/httpd/logo.png)

最後更新： 2016-10-14                   

### 在 `Ubuntu` 14.04 LTS 上建置 `Apache`

安裝作業系統及`Apache`相關套件。
因本文主要介紹`Apache`如何安裝及設定，作業系統方面就不再詳述。

```console
shell> lsb_release -a
```
```
No LSB modules are available.
Distributor ID:	Ubuntu
Description:	Ubuntu 14.04 LTS
Release:	14.04
Codename:	trusty
```

### 安裝 Apache 

```console
shell> apt-get install libapache2-mod-php5 php5 php5-gd php5-gd php5-mysql php5-curl php-apc php-mdb2 php-mail php-date php-pear apache2
```

```console
shell> cp /etc/apache2/sites-available/default /etc/apache2/sites-available/mynewsite
shell> a2ensite mynewsite
shell> service apache2 restart
shell> a2dissite mynewsite
shell> service apache2 restart
```

```console
shell> vim /etc/apache2/conf.d/security
```

```apacheconf
ServerSignature Off
ServerTokens Prod
```

```console
shell> a2enmod ssl
shell> a2ensite default-ssl
shell> service apache2 restart
```

```console
shell> chgrp -R webmasters /var/www
shell> find /var/www -type d -exec chmod g=rwxs "{}" \;
shell> find /var/www -type f -exec chmod g=rws  "{}" \;
```

```console
shell> httpd -M
shell> apachectl -M

Loaded Modules:
 core_module (static)
 so_module (static)
 http_module (static)
 access_compat_module (shared)
 actions_module (shared)
 alias_module (shared)
 allowmethods_module (shared)
 ...
 proxy_fcgi_module (shared)
 proxy_fdpass_module (shared)
 proxy_ftp_module (shared)
 proxy_http_module (shared)
 proxy_scgi_module (shared)
 proxy_wstunnel_module (shared)
 systemd_module (shared)
 cgi_module (shared)
 php5_module (shared)
```

### Disabling SSLv3 on Apache
```console
shell> vim /etc/apache2/mods-available/ssl.conf
```
```apacheconf
SSLProtocol all -SSLv3 -SSLv2
```

### Enabling Strict Transport Security

```apacheconf
LoadModule headers_module libexec/apache2/mod_headers.so

<VirtualHost 114.35.124.22:443>
  Header always set Strict-Transport-Security "max-age=31536000; includeSubDomains; preload";
</VirtualHost>

<VirtualHost *:80>
  # ...
  ServerName example.com
  Redirect permanent / https://example.com/
</VirtualHost>

<VirtualHost *:80>
  # ...
  <IfModule mod_rewrite.c>
    RewriteEngine On
    RewriteCond %{HTTPS} off
    RewriteRule (.*) https://%{HTTP_HOST}%{REQUEST_URI}
  </IfModule>
</VirtualHost>
```


### 在 `CentOS-5` 上建置 `Apache`

```console
shell> yum install httpd

shell> chkconfig --list
shell> chkconfig httpd on

shell> service httpd start
```

```console
shell> sestatus
```
```
SELinux status:                 enabled
SELinuxfs mount:                /selinux
Current mode:                   enforcing
Mode from config file:          enforcing
Policy version:                 24
Policy from config file:        targeted
```
```console
shell> vim /etc/selinux/config
```
```
# This file controls the state of SELinux on the system.
# SELINUX= can take one of these three values:
#       enforcing - SELinux security policy is enforced.
#       permissive - SELinux prints warnings instead of enforcing.
#       disabled - No SELinux policy is loaded.
SELINUX=disabled
# SELINUXTYPE= can take one of these two values:
#       targeted - Targeted processes are protected,
#       mls - Multi Level Security protection.
SELINUXTYPE=targeted
```

```console
shell> getenforce
Disabled
```
---

`SPDY` (讀音為`SPeeDY`) 為一網路內容傳輸的應用程式層協定，該協定著重於開發更多可降低延遲的功能，諸如多工串流、判斷要求的優先等級，以及HTTP標頭的壓縮等。
`SPDY`是`Google`針對HTTP傳輸協定缺點所提出的改良版，具有加密、傳輸較快等優點。

```console
shell> uname -m

shell> wget https://dl-ssl.google.com/dl/linux/direct/mod-spdy-beta_current_i386.deb
shell> wget https://dl-ssl.google.com/dl/linux/direct/mod-spdy-beta_current_amd64.deb

shell> dpkg -i mod-spdy-*.deb
shell> apt-get -f install

shell> vim /etc/apache2/mods-available/spdy.conf
``` 

```apacheconf
Turning ON mod_spdy
SpdyEnabled on
```

---

`mod_pagespeed`可以自動為`Apache`網站上的網頁及資源使用做最佳化，以加快網站的速度。

---

` `是一種網頁防火牆軟體，可與網站伺服器結合（依照官方網站的說明，`ModSecurity`可安裝在`Apache`或`IIS`等知名的網站伺服器），提供針對Web攻擊如`資料庫注入攻擊` (`SQL injection Attacks`)、`跨網站Script攻擊` (`Cross-site Scripting`)、`目錄路徑外洩` (`Path Traversal Attacks`)等等相關攻擊的防衛能力。

```
libapache2-mod-security2 - Tighten web applications security for Apache
libapache2-modsecurity - Dummy transitional package
modsecurity-crs - modsecurity's Core Rule Set
```

```console
shell> apt-get install libapache2-mod-security2
shell> dpkg -L libapache2-mod-security2
shell> /etc/modsecurity/modsecurity.conf
```

**413 Payload Too Large**

```apacheconf
SecRequestBodyAccess On
```

```console
shell> a2dismod security2
shell> service apache2 restart
```

```
spring.http.multipart.max-file-size=128KB
spring.http.multipart.max-request-size=128KB
```

- [uploading-files](https://spring.io/guides/gs/uploading-files/)
- [413 Payload Too Large](https://tools.ietf.org/html/rfc7231#section-6.5.11)

---

```console
shell> apt-get install libapache2-mod-rpaf
shell> vim /etc/apache2/mods-available/rpaf.conf
```
```apacheconf
RPAFproxy_ips 192.168.42.102
```

---

`Apache`在全球網站伺服器的領導地位早已著毋庸議，而其內建的`Apache Bench`也是相當值得參考的效能指標。
進行網站伺服器的效能測試，同步連線數設為10，對伺服器發出10000次request

```console
http://192.168.42.104
shell> ab -n 10000 -c 10 http://192.168.42.104/
shell> ab -c 500 -n 20000 http://192.168.42.104/
shell> ab -c 500 -n 20000 -H "Accept-Encoding: gzip" http://192.168.42.104/
```
---

```console
shell> apache2ctl -M

Loaded Modules:
 core_module (static)
 log_config_module (static)
 logio_module (static)
 version_module (static)
 mpm_worker_module (static)
 http_module (static)
 so_module (static)
 alias_module (shared)
 auth_basic_module (shared)
 authn_file_module (shared)
 authz_default_module (shared)
 authz_groupfile_module (shared)
 authz_host_module (shared)
 authz_user_module (shared)
 autoindex_module (shared)
 cgid_module (shared)
 deflate_module (shared)
 dir_module (shared)
 env_module (shared)
 mime_module (shared)
 security2_module (shared)
 negotiation_module (shared)
 pagespeed_module (shared)
 proxy_module (shared)
 proxy_balancer_module (shared)
 proxy_http_module (shared)
 reqtimeout_module (shared)
 setenvif_module (shared)
 spdy_module (shared)
 status_module (shared)
 unique_id_module (shared)
Syntax OK
```

---

```console
shell> apt-get install liblwp-online-perl
shell> HEAD http://127.0.0.1/
shell> GET -Used http://127.0.0.1/
```

---
##### 疑難排解 (Troubleshooting)

出現錯誤訊息

```
apache2: Could not reliably determine the server's fully qualified domain name, using 192.168.42.102 for ServerName
```

```console
shell> vim /etc/hosts
```
```
192.168.42.102       ip-192-168-42-102.myserver.com ip-192-168-42-102
```

---

```apacheconf
# Ensure that Apache listens on port 80
Listen 80

# Listen for virtual host requests on all IP addresses
NameVirtualHost *:80

# etc ...
# ...
```

```
Complete!
```

###  參考網站：

- [letsencrypt](https://github.com/letsencrypt/letsencrypt)

- [httpd.conf](http://www.opensource.apple.com/source/apache/apache-769/httpd.conf)
- [Apache Core Features](http://httpd.apache.org/docs/2.2/mod/core.html)
- [开源 Apache 服务器安全防护技术精要及实战](http://www.ibm.com/developerworks/cn/linux/l-cn-apache-secure/index.html)
- [HTTPD - Apache2 Web Server](https://help.ubuntu.com/12.04/serverguide/httpd.html)
- [Certificates](https://help.ubuntu.com/12.04/serverguide/certificates-and-security.html)
- [Enabling and Disabling SELinux](https://access.redhat.com/documentation/en-US/Red_Hat_Enterprise_Linux/6/html/Security-Enhanced_Linux/sect-Security-Enhanced_Linux-Working_with_SELinux-Enabling_and_Disabling_SELinux.html)
- [http://zh.wikipedia.org/wiki/SPDY](http://zh.wikipedia.org/wiki/SPDY)
- [Apache釋出HTTP伺服器2.4版](http://www.ithome.com.tw/node/72287)
- [IETF規劃下一代HTTP標準　將採SPDY協定](http://www.ithome.com.tw/node/76619)
- [Google揭露SPDY計畫　要讓網路瀏覽速度加倍](http://www.ithome.com.tw/node/58126)
- [Google釋出正式版Apache自動優化模組　加快網站速度](http://www.ithome.com.tw/node/76796)
- [How to Install Apache, MySQL, and PHP on Ubuntu](https://www.vultr.com/docs/how-to-install-apache-mysql-and-php-on-ubuntu)
- [Disabling SSLv3](https://www.vultr.com/docs/disabling-sslv3)
- [以ModSecurity監控上傳檔案 結合開源ClamAV防毒](http://www.netadmin.com.tw/article_content.aspx?sn=1412020006)
- [spdy](https://developers.google.com/speed/spdy/)
- [spdy](https://developers.google.com/speed/spdy/mod_spdy/)
- [Apache內建基本驗證機制 快速啟用mod_auth網頁認證](http://www.netadmin.com.tw/article_content.aspx?sn=1107080004&ns=1107190008)
- [用MySQL資料庫 提供Apache控管帳號權限](http://www.netadmin.com.tw/article_content.aspx?sn=1107150002)
- [ab - Apache HTTP server benchmarking tool](http://httpd.apache.org/docs/2.2/programs/ab.html)
- [htpasswd](http://httpd.apache.org/docs/2.2/programs/htpasswd.html)
