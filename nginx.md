![](https://raw.githubusercontent.com/docker-library/docs/master/nginx/logo.png)

![](https://d33np9n32j53g7.cloudfront.net/assets/stacks/nginxstack/img/nginxstack-stack-110x117-5c92eb04fa128dcd0e9259e63b1dba01.png)

最後更新： 2016-10-11                    

### 在 `Raspbian` 8.0 上建置 `nginx`

安裝作業系統及`nginx`相關套件。
因本文主要介紹`nginx`如何安裝及設定，作業系統方面就不再詳述。

```console 
shell> lsb_release -a
No LSB modules are available.
Distributor ID:	Raspbian
Description:	Raspbian GNU/Linux 8.0 (jessie)
Release:	8.0
Codename:	jessie
```

### 安裝 nginx 

```
nginx - small, powerful, scalable web/proxy server
nginx-extras - nginx web/proxy server (extended version)
nginx-full - nginx web/proxy server (standard version)
nginx-light - nginx web/proxy server (basic version)
```

```console
shell> curl -sSL http://nginx.org/keys/nginx_signing.key | sudo apt-key add - 
shell> echo deb http://nginx.org/packages/ubuntu/ "$(lsb_release -sc)" nginx | sudo tee /etc/apt/sources.list.d/nginx.list
shell> echo deb-src http://nginx.org/packages/ubuntu/ "$(lsb_release -sc)" nginx | sudo tee -a /etc/apt/sources.list.d/nginx.list
shell> sudo apt-get update
shell> sudo apt-get install nginx
```

```console
shell> nginx -v
nginx version: nginx/1.6.2
nginx version: nginx/1.10.2
```

```console
shell> nginx -t
nginx: the configuration file /etc/nginx/nginx.conf syntax is ok
nginx: configuration file /etc/nginx/nginx.conf test is successful
```

```console
shell> nginx -V
nginx version: nginx/1.6.2
TLS SNI support enabled
configure arguments: --with-cc-opt='-g -O2 -fstack-protector-strong -Wformat -Werror=format-security -D_FORTIFY_SOURCE=2' --with-ld-opt=-Wl,-z,relro --prefix=/usr/share/nginx --conf-path=/etc/nginx/nginx.conf --http-log-path=/var/log/nginx/access.log --error-log-path=/var/log/nginx/error.log --lock-path=/var/lock/nginx.lock --pid-path=/run/nginx.pid --http-client-body-temp-path=/var/lib/nginx/body --http-fastcgi-temp-path=/var/lib/nginx/fastcgi --http-proxy-temp-path=/var/lib/nginx/proxy --http-scgi-temp-path=/var/lib/nginx/scgi --http-uwsgi-temp-path=/var/lib/nginx/uwsgi --with-debug --with-pcre-jit --with-ipv6 --with-http_ssl_module --with-http_stub_status_module --with-http_realip_module --with-http_auth_request_module --with-http_addition_module --with-http_dav_module --with-http_geoip_module --with-http_gzip_static_module --with-http_image_filter_module --with-http_spdy_module --with-http_sub_module --with-http_xslt_module --with-mail --with-mail_ssl_module --add-module=/build/nginx-Kaumns/nginx-1.6.2/debian/modules/nginx-auth-pam --add-module=/build/nginx-Kaumns/nginx-1.6.2/debian/modules/nginx-dav-ext-module --add-module=/build/nginx-Kaumns/nginx-1.6.2/debian/modules/nginx-echo --add-module=/build/nginx-Kaumns/nginx-1.6.2/debian/modules/nginx-upstream-fair --add-module=/build/nginx-Kaumns/nginx-1.6.2/debian/modules/ngx_http_substitutions_filter_module
```

```console
shell> hostname -I
```

```console
shell> service nginx restart
```
```console
shell> systemctl status nginx.service
```
---

**反向 Proxy**
![](http://i.imgur.com/9QNvICY.gif)

```console
shell> cd /etc/nginx
shell> sudo vim sites-enabled/default 
```

```
upstream backend {
  server backend1.example.com:12345;
  server backend2.example.com:12345;
  server backend3.example.com:12345;
  keepalive 32;
}

server {
  listen 80 default_server;

  location / {
    add_header Alternate-Protocol: 443:npn-spdy/2;
    proxy_pass http://backend;
    proxy_buffering off;
    proxy_set_header Host $host;
    proxy_set_header X-Real-IP $remote_addr;
    proxy_set_header X-Forwarded-For $proxy_add_x_forwarded_for;
}

```

### :books: 參考網站：
- [reverse-proxy](https://www.nginx.com/resources/admin-guide/reverse-proxy/)
- [load-balancer](https://www.nginx.com/resources/admin-guide/load-balancer/)
- [Alternate-Protocol](https://www.chromium.org/spdy/spdy-protocol/spdy-protocol-draft2#TOC-Server-Advertisement-of-SPDY-through-the-HTTP-Alternate-Protocol-header)

---

###### 建立憑證要求 (Generates a CSR)

```console
shell> openssl req -newkey rsa:2048 -sha256 -nodes -keyout www_yourdomain_com.key -out server-req.pem -subj "/C=TW/ST=Taiwan/L=TPE/O=MyCompany Ltd/OU=IT/CN=server"

shell> openssl pkcs12 -export -in server.crt -inkey server.key -out server.pfx
shell> openssl pkcs12 -export -in server.crt -inkey server.key -out server.pfx -certfile CACert.crt
```

### :books: 參考網站：
- [easy-csr](https://www.digicert.com/easy-csr/openssl.htm)
- [Converting a PFX file to PEM, SPC, and PVK files](https://support.comodo.com/index.php?/Default/Knowledgebase/Article/View/548/7/converting-a-pfx-file-to-pem-spc-and-pvk-files)
- [How do I export, as a pfx file, my Certificate and Private Key from Apache?](https://support.comodo.com/index.php?/Default/Knowledgebase/Article/View/297/17/how-do-i-export-as-a-pfx-file-my-certificate-and-private-key-from-apache)
- [Convert a Certificate File to PKCS#12 Format](https://pubs.vmware.com/view-51/index.jsp?topic=%2Fcom.vmware.view.certificates.doc%2FGUID-17AD1631-E6D6-4853-8D9B-8E481BE2CC68.html)
- [Various Types of SSL Commands and Keytool](https://cheapsslsecurity.com/blog/various-types-ssl-commands-keytool/)

######  提交憑證要求


server-req.pem
www_yourdomain_com.key

###### 安裝憑證，並設定 SSL 的網站

```console
shell> cat www_yourdomain_com.crt COMODORSADomainValidationSecureServerCA.crt COMODORSAAddTrustCA.crt > ssl-bundle.crt

shell> cat COMODORSADomainValidationSecureServerCA.crt COMODORSAAddTrustCA.crt AddTrustExternalCARoot.crt > full_chain.pem  

shell> cp ssl-bundle.crt /etc/ssl/certs
shell> cp www_yourdomain_com.key /etc/ssl/private/mysite.key
shell> cp full_chain.pem /etc/nginx/ssl

```

```console
shell> openssl dhparam -out dhparam.pem 2048
```

```console
shell> cd /etc/nginx
shell> sudo vim sites-enabled/default 
```

```
server {
    listen       80;
    server_name  _;
    return       301 https://$host$request_uri;
}

server {
	listen 443 ssl default_server spdy;
    listen 443 ssl http2;

    server_tokens off;


        ssl on;
        ssl_certificate /etc/ssl/certs/ssl-bundle.crt;
        ssl_certificate_key /etc/ssl/private/mysite.key;
         
        ssl_dhparam /etc/ssl/private/dhparam.pem;

        #enables all versions of TLS, but not SSLv2 or 3 which are weak and now deprecated.
        ssl_protocols TLSv1 TLSv1.1 TLSv1.2;

        #Disables all weak ciphers
        ssl_ciphers "ECDHE-RSA-AES256-GCM-SHA384:ECDHE-RSA-AES128-GCM-SHA256:DHE-RSA-AES256-GCM-SHA384:DHE-RSA-AES128-GCM-SHA256:ECDHE-RSA-AES256-SHA384:ECDHE-RSA-AES128-SHA256:ECDHE-RSA-AES256-SHA:ECDHE-RSA-AES128-SHA:DHE-RSA-AES256-SHA256:DHE-RSA-AES128-SHA256:DHE-RSA
-AES256-SHA:DHE-RSA-AES128-SHA:ECDHE-RSA-DES-CBC3-SHA:EDH-RSA-DES-CBC3-SHA:AES256-GCM-SHA384:AES128-GCM-SHA256:AES256-SHA256:AES128-SHA256:AES256-SHA:AES128-SHA:DES-CBC3-SHA:HIGH:!aNULL:!eNULL:!EXPORT:!DES:!MD5:!PSK:!RC4";

        ssl_prefer_server_ciphers on;

        resolver 8.8.8.8;
        ssl_stapling on;
        ssl_stapling_verify on;
        ssl_trusted_certificate /etc/nginx/ssl/full_chain.pem;
        
        #Enabling Strict Transport Security
        add_header Strict-Transport-Security "max-age=31536000; includeSubDomains; preload";
        add_header X-Frame-Options SAMEORIGIN;
        add_header Alternate-Protocol: 443:npn-spdy/3;

}
```

```console
shell> openssl s_client -connect www.godaddy.com:443
```

### :books: 參考網站：
- [enable-ocsp-stapling-on-nginx](https://support.comodo.com/index.php?/Default/Knowledgebase/Article/View/1015/38/enable-ocsp-stapling-on-nginx)
- [ngx_http_v2_module](http://nginx.org/en/docs/http/ngx_http_v2_module.html)
- [enable-ocsp-stapling-on-nginx](https://support.comodo.com/index.php?/Default/Knowledgebase/Article/View/1015/0/enable-ocsp-stapling-on-nginx)
- [X-Frame-Options](https://developer.mozilla.org/en-US/docs/Web/HTTP/X-Frame-Options)
- [linux_packages](http://nginx.org/en/linux_packages.html)
- [ngx_http_headers_module](http://nginx.org/en/docs/http/ngx_http_headers_module.html)
- [csr-generation-using-openssl-apache-wmod_ssl-nginx-os-x](https://support.comodo.com/index.php?/Default/Knowledgebase/Article/View/1/0/csr-generation-using-openssl-apache-wmod_ssl-nginx-os-x)
- [certificate-installation-nginx](https://support.comodo.com/index.php?/Default/Knowledgebase/Article/View/789/37/certificate-installation-nginx)
- [HTTP_strict_transport_security](https://developer.mozilla.org/en-US/docs/Web/Security/HTTP_strict_transport_security)
- [最佳化效能](https://developers.google.com/web/fundamentals/performance/?hl=zh-tw)
- [configuring_https_servers](http://nginx.org/en/docs/http/configuring_https_servers.html)
- [sslanalyzer](https://sslanalyzer.comodoca.com/)

- [root-comodo-rsa-certification-authority-sha-2](https://support.comodo.com/index.php?/Knowledgebase/Article/View/969/0/root-comodo-rsa-certification-authority-sha-2)
- [intermediate-2-sha-2-comodo-rsa-domain-validation-secure-server-ca](https://support.comodo.com/index.php?/Knowledgebase/Article/View/970/0/intermediate-2-sha-2-comodo-rsa-domain-validation-secure-server-ca)

<!--
https://gist.github.com/bradmontgomery/6487319
-->

---
```console
shell> nginx -V
```

```
--with-http_spdy_module
```

```
listen 443 ssl default_server spdy;
```

### :books: 參考網站：
- [ngx_http_spdy_module](http://nginx.org/en/docs/http/ngx_http_spdy_module.html)

---
### 安裝 PHP

```console
shell> sudo apt-get install php5-fpm
```

```console
shell> cd /etc/nginx
shell> sudo vim sites-enabled/default 
```

```
index index.html index.htm;
```

```
index index.php index.html index.htm;
```

---

**/etc/nginx/sites-enabled/default**
```
server {
        listen 80 default_server;
        listen [::]:80 default_server;
        root /var/www/html;
        index index.html index.htm index.nginx-debian.html;
        server_name _;
}
```

---

**/etc/nginx/sites-enabled/default**
```
location / {
       # First attempt to serve request as file, then
       # as directory, then fall back to displaying a 404.
       try_files $uri $uri/ =404;
}
```
---

**/etc/nginx/nginx.conf**

```
worker_processes auto;

http {
        server_tokens off;
        ssl_session_cache   shared:SSL:10m;
        ssl_session_timeout 10m;
        
        ssl_stapling on;
        resolver 192.0.2.1;
        ssl_trusted_certificate file;

}

events {
        worker_connections 768;
        use epoll; 
        multi_accept on;
}

http {
        gzip on;
        gzip_disable "msie6";
        gzip_types text/plain text/css application/json application/javascript text/xml application/xml application/xml+rss text/javascript;


}

- [configuring_https_servers](http://nginx.org/en/docs/http/configuring_https_servers.html)
- [ngx_http_ssl_module](http://nginx.org/en/docs/http/ngx_http_ssl_module.html)

```

### :books: 參考網站：
- [worker_processes](http://nginx.org/en/docs/ngx_core_module.html#worker_processes)
- [use](http://nginx.org/en/docs/ngx_core_module.html#use)
- [ngx_http_gzip_module](http://nginx.org/en/docs/http/ngx_http_gzip_module.html)

---

```
net.ipv4.ip_local_port_range = 1024	65000
net.ipv4.tcp_fin_timeout = 15

```

-  [Changing Network Kernel Settings](https://access.redhat.com/documentation/en-US/Red_Hat_Enterprise_Linux/5/html/Tuning_and_Optimizing_Red_Hat_Enterprise_Linux_for_Oracle_9i_and_10g_Databases/sect-Oracle_9i_and_10g_Tuning_Guide-Adjusting_Network_Settings-Changing_Network_Kernel_Settings.html)

---

```console
shell> sudo apt-get install nginx-extras
```

```
# set the Server output header
more_set_headers    "Server: my_server";

more_clear_headers 'Server';
more_clear_headers 'X-Powered-By';

expires    24h;
add_header Cache-Control private;

```

### :books: 參考網站：
- [headers-more-nginx-module](https://github.com/openresty/headers-more-nginx-module#more_set_headers)
- [ngx_http_headers_module](http://nginx.org/en/docs/http/ngx_http_headers_module.html#add_header)

---

How to test Logjam via command line?

```console
shell> openssl s_client -connect www.example.com:443 -cipher 'EXP'
shell> nmap --script ssl-enum-ciphers -p 443 www.example.com
```

---

```
if ($http_user_agent ~* "Baiduspider") {
        return 403;
}
```


**robots.txt**
```
User-agent: Googlebot-Image
User-agent: Googlebot
User-agent: Baiduspider
Disallow: /
```

### :books: 參考網站：
- [建立 robots.txt 檔案](https://support.google.com/webmasters/answer/6062596?hl=zh-Hant)
- [robots.txt](https://support.google.com/webmasters/answer/6062608?hl=zh-Hant)
- [透過 robots.txt 測試工具來測試 robots.txt](https://support.google.com/webmasters/answer/6062598)


---

### :books: 參考網站：
- [ngx_http_log_module](http://nginx.org/en/docs/http/ngx_http_log_module.html)
- [ssl_checker](https://www.geocerts.com/ssl_checker)
- [SSL Certificate Checker](https://www.digicert.com/help/)
- [csr-creation](https://www.digicert.com/csr-creation.htm)
- [easy-csr](https://www.digicert.com/easy-csr/openssl.htm)
- [checker](https://cryptoreport.websecurity.symantec.com/checker/)
- [ssltest](https://www.ssllabs.com/ssltest/index.html)
- [SSL/TLS Capabilities of Your Browser](https://www.ssllabs.com/ssltest/viewMyClient.html)

- [nginx](https://www.raspberrypi.org/documentation/remote-access/web-server/nginx.md)
- [Install Nginx + PHP FPM + Caching + MySQL on Ubuntu 12.04](https://www.vultr.com/docs/install-nginx-php-fpm-caching-mysql-on-ubuntu-12-04)
- [Disabling SSLv3](https://www.vultr.com/docs/disabling-sslv3)
- [Setup Nginx as Reverse Proxy Over Apache on Debian/Ubuntu](https://www.vultr.com/docs/setup-nginx-as-reverse-proxy-over-apache-on-debian-ubuntu)


MacGyver
馬蓋先

<!--
http://168gg.net/?p=71
-->
