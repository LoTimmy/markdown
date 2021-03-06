### 在 `Ubuntu` 14.04 LTS 上建置 `fail2ban`

安裝作業系統及`fail2ban`相關套件。
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

### 安裝 fail2ban 

```console
shell> aptitude install fail2ban
```

---

```console
shell> fail2ban-client status
Status
|- Number of jail:	1
`- Jail list:		ssh
```

```console
shell> fail2ban-client status ssh
Status for the jail: ssh
|- filter
|  |- File list:	/var/log/auth.log 
|  |- Currently failed:	3
|  `- Total failed:	130
`- action
   |- Currently banned:	0
   |  `- IP list:	
   `- Total banned:	4
```

```console
shell> iptables -n -L INPUT
```

```console
shell> fail2ban-regex /var/log/auth.log /etc/fail2ban/filter.d/sshd.conf
shell> fail2ban-regex /var/log/auth.log /etc/fail2ban/filter.d/sshd-ddos.conf
```

```console
shell> fail2ban-client set ssh unbanip <IP> 
shell> fail2ban-client set postfix-sasl unbanip <IP> 
```

```console
shell> fail2ban-client -i
fail2ban> status postfix-sasl
fail2ban> status set postfix-sasl unbanip <IP>
```





/etc/fail2ban/jail.conf

```
[DEFAULT]
ignoreip = 127.0.0.1/8
bantime  = 600
```


```
[ssh]

enabled  = true
port     = ssh
filter   = sshd
logpath  = /var/log/auth.log
maxretry = 6

[sshd-ddos]

enabled  = true
port     = ssh
filter   = sshd-ddos
logpath  = /var/log/auth.log
maxretry = 6
```

```console
shell> tar xvfj fail2ban-0.9.4.tar.bz2
shell> cd fail2ban-0.9.4
shell> python setup.py install
shell> cp files/debian-initd /etc/init.d/fail2ban
```