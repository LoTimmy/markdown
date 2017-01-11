
```
Port 22960 
LoginGraceTime 30 
MaxAuthTries 3 
Protocol 2 
PermitRootLogin no
```

- 把 SSH 的标准端口改为不常用的值并增强 SSH 配置，从而挡住最简单的攻击。
- LoginGraceTime 允许一次登录花费 30 秒；如果用户花费的时间超过 30 秒，就不允许他访问，必须重新登录。
- MaxAuthTries 把错误尝试的次数限制为 3 次，3 次之后拒绝登录尝试。
- 上面的 Protocol 2 行禁止使用比较弱的协议。
- 最后一行不允许任何人作为根用户登录，这会让黑客攻击更困难。

**OpenSSH Server**


/etc/ssh/sshd_config
```
UseDNS no

Compression yes

GSSAPIAuthentication no
GSSAPICleanupCredentials yes

#Banner /etc/issue.net

```

```console
shell> man sshd_config
shell> sudo cp /etc/ssh/sshd_config /etc/ssh/sshd_config.original
shell> sudo chmod a-w /etc/ssh/sshd_config.original
shell> sudo service ssh restart
```

---

> `SSH` 会自动加密和解密所有 `SSH` 客户端与服务端之间的网络数据。
> `SSH` 还同时提供了一个非常有用的功能，这就是端口转发。
> 它能够将其他 `TCP` 端口的网络数据通过 `SSH` 链接来转发，并且自动提供了相应的加密及解密服务。这一过程有时也被叫做“隧道”（tunneling），这是因为 `SSH` 为其他 `TCP` 链接提供了一个安全的通道来进行传输而得名。
> 加密 SSH Client 端至 SSH Server 端之间的通讯数据。
> 突破防火墙的限制完成一些之前无法建立的 TCP 连接。

**本地端口转发**
```
Host remotehost
    User matt
    LocalForward 0.0.0.0:9999 localhost:3306 
```

```console
shell> ssh -NC matt@remotehost -L 9999:localhost:3306
```

**远程端口转发**
```
Host remotehost
    User matt
    RemoteForward 0.0.0.0:12429 127.0.0.1:22 
```

```console
shell> ssh -NfR 12429:127.0.0.1:22 matt@remotehost
```

**动态端口转发**
```
Host remotehost
    User matt
    DynamicForward 0.0.0.0:1080
```

```console
shell> ssh -N -D 0.0.0.0:1080 matt@remotehost
shell> ssh -f -N -D 0.0.0.0:1080 matt@remotehost
```

---

~/.ssh/config
```
Host *
    ControlMaster auto
    ControlPath ~/.ssh/master-%r@%h:%p
    Compression yes
    TCPKeepAlive yes
    ServerAliveInterval 20
    ServerAliveCountMax 5
    VisualHostKey yes 

Host 192.168.42.*
    User root
    StrictHostKeyChecking no
    UserKnownHostsFile /dev/null
    LogLevel QUIET

Host 60.248.90.170
    HostName 60.248.90.170
    Port 22
    User apple
    IdentityFile "~/.ssh/s85ThUdubruv.pem"

Host mail
    HostName 192.168.2.93
    Port 22
    User apple
    ProxyCommand ssh 60.248.90.170 -W %h:%p

```

```console
shell> ssh -p 12345 username@remotehost
shell> ssh -o "User=username" -o "Port=12345" -o "HostName=remotehost"
```

---

**Generating an SSH Key on Linux**
```console
shell> ssh-keygen -t rsa
shell> chmod 600 ~/.ssh/[private_key_file]
shell> ssh-add ~/.ssh/[private_key_file]

shell> ssh-copy-id username@remotehost
shell> chmod 600 .ssh/authorized_keys
```


```console
$ ssh-keygen
Generating public/private rsa key pair.
Enter file in which to save the key (/home/user/.ssh/id_rsa):
Enter passphrase (empty for no passphrase):
Enter same passphrase again:
Your identification has been saved in /home/user/.ssh/id_rsa.
Your public key has been saved in /home/user/.ssh/id_rsa.pub.
The key fingerprint is:
df:c4:49:e9:fe:8e:7b:eb:28:d5:1f:72:82:fb:f2:69
The key's randomart image is:
+--[ RSA 2048]----+
|                 |
|             .   |
|            o    |
|           + .   |
|        S   *.   |
|         . =.o.o |
|          ..+ +..|
|          .o Eo .|
|           .OO=. |
+-----------------+
 
```

```console
$ ssh-keygen -y
```

**Example SSH Public Key**

```
ssh-rsa AAAAB3NzaC1yc2EAAAABIwAAAQEA6bUsFjDSFcPC/BZbIAv8cAR5syJMB
GiEqzFOIEHbm0fPkkQ0U6KppzuXvVlc2u7w0mgPMhnkEfV6j0YBITu0Rs8rNHZFJs
CYXpdoPxMMgmCf/FaOiKrb7+1xk21q2VwZyj13GPUsCxQhRW7dNidaaYTf14sbd9A
qMUH4UOUjs27MhO37q8/WjV3wVWpFqexm3f4HPyMLAAEeExT7UziHyoMLJBHDKMN7
1Ok2kV24wwn+t9P/Va/6OR6LyCmyCrFyiNbbCDtQ9JvCj5RVBla5q4uEkFRl0t6m9
XZg+qT67sDDoystq3XEfNUmDYDL4kq1xPM66KFk3OS5qeIN2kcSnQ==
```

- [generate_ssh_key](http://docs.aws.amazon.com/cloudhsm/latest/userguide/generate_ssh_key.html)

---

**sshpass - Non-interactive ssh password authentication**

```console
shell> apt-get install sshpass

shell> sshpass -p 12345 ssh -l username remotehost
shell> sshpass -p 12345 sftp username@remotehost
```

```console
shell> set +o history
shell> sshpass -p 12345 ssh -l username remotehost
shell> set -o history
```

---

### 安裝 Google Authenticator (`兩步驟驗證`)

```console
shell> apt-get install libpam-google-authenticator
shell> google-authenticator
```

**~/.google_authenticator**
```
RG2YMNCEBZRKAG5H
" RATE_LIMIT 3 30 1453447203 1453447204 1453447204
" DISALLOW_REUSE
" TOTP_AUTH
41002789
33636205
58145958
96084925
37756905
```

```console
shell> vi /etc/pam.d/sshd
```
```
auth required /lib/security/pam_google_authenticator.so

# Standard Un*x authentication.
# @include common-auth
```

```
auth sufficient /lib/security/pam_google_authenticator.so
```

```console
shell> vi /etc/ssh/sshd_config
```
```
ChallengeResponseAuthentication yes
```

---

```console
shell> ssh-keygen -f "/root/.ssh/known_hosts" -R 192.168.42.19
```

---

```console
shell> apt-get install autossh
shell> autossh -M 20000 -t remotehost 'screen -raAd sessionname'
shell> ssh -t remotehost screen -xRR
```

autossh


###  參考網站：
- [serverguide](https://help.ubuntu.com/lts/serverguide/)
- [openssh-server](https://help.ubuntu.com/lts/serverguide/openssh-server.html)
- [保护 SSH 的三把锁](https://www.ibm.com/developerworks/cn/aix/library/au-sshlocks/)
- http://www.ibm.com/support/knowledgecenter/SSWT7D_1.0.0/com.ibm.commercecloud.administering.doc/tasks/tad_connect_jumphosts_cyg.htm
- [实战 SSH 端口转发](https://www.ibm.com/developerworks/cn/linux/l-cn-sshforward/)
