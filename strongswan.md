![](https://www.strongswan.org/images/strongswan.png)


`strongswan - IPsec VPN solution metapackage`
`strongswan-plugin-xauth-generic - strongSwan plugin for the generic XAuth backend`

```console
shell> sudo apt-get install strongswan strongswan-plugin-xauth-generic
```

/etc/sysctl.conf

```
net.ipv4.ip_forward=1
```

```console
shell> sysctl -w net.ipv4.ip_forward=1
```

/etc/ipsec.secrets
```
PSK "OGqW45V4iAk="
```

```
version 2.0
config setup
    nat_traversal=yes
    virtual_private=%v4:10.0.0.0/8,%v4:192.168.0.0/16,%v4:172.16.0.0/12
    oe=off
    protostack=netkey
    listen=192.168.1.35
    #plutodebug=all
    #plutostderrlog=/var/log/pluto.log

conn L2TP-PSK-NAT
    rightsubnet=vhost:%priv
    also=L2TP-PSK-noNAT

conn L2TP-PSK-noNAT
#    authby=secret
    authby=xauthpsk

    pfs=no
    auto=add
    keyingtries=3
    rekey=yes
    ikelifetime=8h
    keylife=1h
    type=transport
    left=%defaultroute
#    left=192.168.1.35
    leftprotoport=17/1701
    right=%any
    rightprotoport=17/%any
    forceencaps=no
    sha2_truncbug=no
    dpddelay=10
    dpdtimeout=90
    dpdaction=clear
```

```console
shell> service strongswan start
shell> update-rc.d strongswan enable
shell> ipsec status
shell> ipsec statusall
```

```
/usr/share/doc/strongswan
```

`options.xl2tpd`
```
require-mschap-v2
refuse-mschap
refuse-chap
refuse-pap


name l2tpd
ms-dns 8.8.8.8

mtu 1400
mru 1400
connect-delay 5000
noccp
auth
crtscts
lock
debug
proxyarp

plugin /var/packages/VPNCenter/target/lib/pppd/radius.so
plugin /var/packages/VPNCenter/target/lib/pppd/radattr.so

unit 301
```

`xl2tpd.conf`

```
[global]
force userspace=no
listen-addr=192.168.1.35
[lns default]
length bit=yes
ip range=10.2.0.1-20
ppp debug=no
require authentication=yes
local ip=10.2.0.0
pppoptfile=/usr/syno/etc/packages/VPNCenter/l2tp/options.xl2tpd
```

---

### :books: 參考網站：
- [strongswan](https://www.strongswan.org/)
- [ipsec.conf](http://manpages.ubuntu.com/manpages/wily/man5/ipsec.conf.5.html)
- [ipsec.secrets](http://manpages.ubuntu.com/manpages/xenial/man5/ipsec.secrets.5.html)
- http://www.cisco.com/cisco/web/support/CN/113/1133/1133929_117258-config-l2l.html

