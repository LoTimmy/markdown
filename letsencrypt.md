
上次更新日期： 2016-11-08                                                     

---

![](https://letsencrypt.org/images/letsencrypt-logo-horizontal.svg)


letsencrypt

```console
mkdir /opt/letsencrypt

shell> wget https://dl.eff.org/certbot-auto
shell> chmod a+x ./certbot-auto
shell> ./certbot-auto --help
shell> ./certbot-auto
shell> ./certbot-auto certonly --standalone --standalone-supported-challenges tls-sni-01 --register-unsafely-without-email --agree-tos -d example.com -d www.example.com -d other.example.net

shell> ./certbot-auto renew
```

```console
shell> ./certbot-auto --apache -d example.com -d www.example.com -d other.example.net
shell> ./certbot-auto certonly --standalone --agree-tos --email admin@example.com -d example.com -d www.example.com -d other.example.net
```

```console
shell> git clone https://github.com/certbot/certbot
shell> cd certbot
shell> ./certbot-auto --help
```

```console
shell> certbot renew --dry-run
```

![Imgur](http://i.imgur.com/7hNAFJa.png)
![Imgur](http://i.imgur.com/3w8fptF.png)
![Imgur](http://i.imgur.com/szPIxbh.png)

---

```
server {
	listen 443 ssl default_server spdy;
    listen 443 ssl http2;

	server_tokens off;


	ssl on;
	ssl_certificate /etc/letsencrypt/live/www.example.com/fullchain.pem;
	ssl_certificate_key /etc/letsencrypt/live/www.example.com/privkey.pem;
         
	ssl_dhparam /etc/ssl/private/dhparam.pem;

	#enables all versions of TLS, but not SSLv2 or 3 which are weak and now deprecated.
	ssl_protocols TLSv1 TLSv1.1 TLSv1.2;

	#Disables all weak ciphers
	ssl_ciphers "ECDHE-RSA-AES256-GCM-SHA384:ECDHE-RSA-AES128-GCM-SHA256:DHE-RSA-AES256-GCM-SHA384:DHE-RSA-AES128-GCM-SHA256:ECDHE-RSA-AES256-SHA384:ECDHE-RSA-AES128-SHA256:ECDHE-RSA-AES256-SHA:ECDHE-RSA-AES128-SHA:DHE-RSA-AES256-SHA256:DHE-RSA-AES128-SHA256:DHE-RSA-AES256-SHA:DHE-RSA-AES128-SHA:ECDHE-RSA-DES-CBC3-SHA:EDH-RSA-DES-CBC3-SHA:AES256-GCM-SHA384:AES128-GCM-SHA256:AES256-SHA256:AES128-SHA256:AES256-SHA:AES128-SHA:DES-CBC3-SHA:HIGH:!aNULL:!eNULL:!EXPORT:!DES:!MD5:!PSK:!RC4";

	ssl_prefer_server_ciphers on;

	resolver 8.8.8.8;
	ssl_stapling on;
	ssl_stapling_verify on;
        
	#Enabling Strict Transport Security
	add_header Strict-Transport-Security "max-age=31536000; includeSubDomains; preload";
	add_header X-Frame-Options SAMEORIGIN;
	add_header Alternate-Protocol: 443:npn-spdy/3;
}
```




----------
### :books: 參考網站：

- [letsencrypt](https://letsencrypt.org/)
- [certbot](https://github.com/certbot/certbot)
- [certbot](https://certbot.eff.org/docs/contributing.html)


`㊙`

