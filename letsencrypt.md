
上次更新日期： 5/23/2016 11:06:48 AM                                                    

---

![](https://letsencrypt.org/images/letsencrypt-logo-horizontal.svg)


letsencrypt

```console
shell> wget https://dl.eff.org/certbot-auto
shell> chmod a+x ./certbot-auto
shell> ./certbot-auto --help
```

```console
shell> git clone https://github.com/certbot/certbot
shell> cd certbot
shell> ./certbot-auto --help
```

```console
shell> certbot renew --dry-run
```

```
Usage: certbot-auto [OPTIONS]
A self-updating wrapper script for the Certbot ACME client. When run, updates
to both this script and certbot will be downloaded and installed. After
ensuring you have the latest versions installed, certbot will be invoked with
all arguments you have provided.

Help for certbot itself cannot be provided until it is installed.

  --debug                                   attempt experimental installation
  -h, --help                                print this help
  -n, --non-interactive, --noninteractive   run without asking for user input
  --no-self-upgrade                         do not download updates
  --os-packages-only                        install OS dependencies and exit
  -v, --verbose                             provide more output

All arguments are accepted and forwarded to the Certbot client when run.
```

```console
shell> ./certbot-auto --apache -d example.com -d www.example.com -d other.example.net
shell> ./certbot-auto certonly --standalone --agree-tos --email admin@example.com -d example.com -d www.example.com -d other.example.net
```


----------
### :books: 參考網站：

- [letsencrypt](https://letsencrypt.org/)
- [certbot](https://github.com/certbot/certbot)
- [certbot](https://certbot.eff.org/docs/contributing.html)


`㊙`

