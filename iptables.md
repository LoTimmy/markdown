
![](http://i.imgur.com/3gzXLPj.png)

---

```console
shell> iptables
```

```console
# Circumvent MTU issues
shell> iptables -t mangle -A FORWARD -p tcp --tcp-flags SYN,RST SYN -j TCPMSS --clamp-mss-to-pmtu

# Masquerade everything out ppp0.
shell> iptables -t nat -A POSTROUTING -o ppp0 -j MASQUERADE
```

```console
shell> iptables -L
shell> iptables -L -v
shell> iptables -nvL --line-numbers

shell> iptables -nvL INPUT --line-numbers  
```

```console
shell> iptables -F
```

```console
shell> iptables -Z
```

```console
shell> iptables-save
shell> iptables-restore
```

```console
shell> iptables -P INPUT DROP
shell> iptables -P FORWARD DROP
shell> iptables -P OUTPUT ACCEPT
```

```console
shell> iptables -A INPUT -m conntrack --ctstate ESTABLISHED,RELATED -j ACCEPT
shell> iptables -A INPUT -m state --state ESTABLISHED,RELATED -j ACCEPT    
```

```
-A INPUT -m state --state NEW -m tcp -p tcp --dport 53 -j ACCEPT
-A INPUT -m state --state NEW -m udp -p udp --dport 69 -j ACCEPT
```

```console
shell> iptables -A INPUT -p tcp --dport ssh -j ACCEPT
shell> iptables -A INPUT -p tcp --dport 80 -j DROP
```

```
INPUT|OUTPUT|FORWARD
ACCEPT|DROP|REJECT 
INVALID|ESTABLISHED|NEW|RELATED|SNAT|DNAT
PREROUTING|POSTROUTING
mangle|nat 
```

```sh
iptables -P INPUT ACCEPT
iptables -P FORWARD ACCEPT
iptables -P OUTPUT ACCEPT

iptables -F -t nat
iptables -F -t mangle
iptables -F

iptables -X -t nat 
iptables -X -t mangle 
iptables -X

iptables -Z

iptables -A INPUT -m conntrack --ctstate ESTABLISHED,RELATED -j ACCEPT

iptables -A INPUT -i lo -j ACCEPT

#iptables -A INPUT -p icmp -j ACCEPT 
iptables -A INPUT -p icmp --icmp-type 0 -j ACCEPT
iptables -A INPUT -p icmp --icmp-type 3 -j ACCEPT
iptables -A INPUT -p icmp --icmp-type 11 -j ACCEPT
iptables -A INPUT -p icmp --icmp-type 8 -m limit --limit 1/second -j ACCEPT

iptables -A INPUT --protocol tcp --tcp-flags ALL SYN,ACK -j DROP

iptables -A INPUT -m conntrack --ctstate NEW -p udp --dport 5353 -j ACCEPT

iptables -A INPUT -m conntrack --ctstate NEW -p tcp --dport 22 -j ACCEPT
iptables -A INPUT -m conntrack --ctstate NEW -p tcp --dport 80 -j ACCEPT
iptables -A INPUT -m conntrack --ctstate NEW -p tcp --dport 443 -j ACCEPT
iptables -A INPUT -m conntrack --ctstate NEW -p tcp --dport 1723 -j ACCEPT

iptables -A INPUT -p udp -m conntrack --ctstate NEW -m udp --dport 5353 -j ACCEPT

iptables -A INPUT -j REJECT --reject-with icmp-host-prohibited
iptables -A FORWARD -j REJECT --reject-with icmp-host-prohibited
```

```sh
#! /bin/bash

# Private interface
IF_PRV=eth0
IP_PRV=192.168.1.1
NET_PRV=192.168.1.0/24

# Public interface
IF_PUB=eth1
IP_PUB=10.0.0.1
NET_PUB=10.0.0.0/24

# Others
ANYWHERE=0.0.0.0/0


SetDefaultPolicy() {
	# Drop everything
	iptables -P INPUT DROP
	iptables -P OUTPUT DROP
	iptables -P FORWARD DROP
}

FlushTables() {
	iptables -F -t nat
	iptables -F -t mangle
	iptables -F -t filter
	iptables -X
}

SetForwardingRules() {
	iptables -A FORWARD -i $IF_PUB -o $IF_PRV -m state --state ESTABLISHED,RELATED -j ACCEPT
	iptables -A FORWARD -i $IF_PRV -o $IF_PUB -j ACCEPT
}

SetLoopbackRules() {
	# Allow everything
	iptables -A INPUT -i lo -j ACCEPT
	iptables -A OUTPUT -o lo -j ACCEPT
}

SetPrivateInterfaceRules() {
	# Allow everything
	iptables -A INPUT -i $IF_PRV -s $NET_PRV -j ACCEPT
	iptables -A OUTPUT -o $IF_PRV -d $NET_PRV -j ACCEPT
}

SetPublicInterfaceRules() {
	iptables -A INPUT -i $IF_PUB -m state --state ESTABLISHED,RELATED -j ACCEPT
	iptables -A OUTPUT -o $IF_PUB -j ACCEPT
}

EnableSourceNAT() {
	# Then source NAT everything else
	iptables -t nat -A POSTROUTING -s $NET_PRV -o $IF_PUB -j SNAT --to $IP_PUB
}

SetICMP_Open() {
	iptables -A INPUT -p icmp --icmp-type 0 -j ACCEPT
	iptables -A INPUT -p icmp --icmp-type 3 -j ACCEPT
	iptables -A INPUT -p icmp --icmp-type 11 -j ACCEPT
	iptables -A INPUT -p icmp --icmp-type 8 -m limit --limit 1/second -j ACCEPT
}

SetSSH_Open() {
	iptables -A INPUT -i $IF_PUB -p tcp -d $IP_PUB --dport 2202 -j ACCEPT
}

SetSMTP_DNAT() {
	iptables -t nat -A PREROUTING -i $IF_PUB -d $IP_PUB -p tcp --dport smtp -j DNAT --to 192.168.1.254
	iptables -A FORWARD -m state --state NEW,ESTABLISHED,RELATED -i $IF_PUB -p tcp --dport smtp -j ACCEPT
}

SetPOP3_DNAT() {
	iptables -t nat -A PREROUTING -i $IF_PUB -d $IP_PUB -p tcp --dport pop3 -j DNAT --to 192.168.10.254
	iptables -A FORWARD -m state --state NEW,ESTABLISHED,RELATED -i $IF_PUB -p tcp --dport pop3 -j ACCEPT
}

SetHTTP_DNAT() {
	iptables -t nat -A PREROUTING -i $IF_PUB -d $IP_PUB -p tcp --dport http -j DNAT --to 192.168.10.253
	iptables -A FORWARD -m state --state NEW,ESTABLISHED,RELATED -i $IF_PUB -p tcp --dport http -j ACCEPT
}

SetBlockedHosts() {
	iptables -A INPUT -i $IF_PUB -s 10.220.231.236 -j REJECT --reject-with icmp-host-prohibited
	iptables -A FORWARD -i $IF_PUB -s 10.220.231.236 -j REJECT --reject-with icmp-host-prohibited
}

SetBlockedNetworks() {
	iptables -A INPUT -i $IF_PUB -s 10.220.232.0/24 -j REJECT --reject-with icmp-net-prohibited
	iptables -A FORWARD -i $IF_PUB -d $IP_PUB -s 10.220.232.0/24 -j REJECT --reject-with icmp-net-prohibited
}



```

### :books: 參考網站：
- [Simple Firewall Configuration Using NetFilter/iptables](https://www.novell.com/coolsolutions/feature/18139.html)
- [Linux 下网络性能优化方法简析](https://www.ibm.com/developerworks/cn/linux/l-cn-network-pt/)

```
iptables -P INPUT ACCEPT
iptables -P FORWARD ACCEPT
iptables -P OUTPUT ACCEPT

iptables -F -t nat
iptables -F -t mangle
iptables -F

iptables -X -t nat 
iptables -X -t mangle 
iptables -X

iptables -Z

iptables -A INPUT -m conntrack --ctstate ESTABLISHED,RELATED -j ACCEPT

iptables -A INPUT -i lo -j ACCEPT
iptables -A INPUT -i ppp+ -j ACCEPT

#iptables -A INPUT -p icmp -j ACCEPT
iptables -A INPUT -p icmp --icmp-type 0 -j ACCEPT
iptables -A INPUT -p icmp --icmp-type 3 -j ACCEPT
iptables -A INPUT -p icmp --icmp-type 11 -j ACCEPT
iptables -A INPUT -p icmp --icmp-type 8 -m limit --limit 1/second -j ACCEPT


iptables -A INPUT -m conntrack --ctstate NEW -p tcp --dport 22 -j ACCEPT
iptables -A INPUT -m conntrack --ctstate NEW -p tcp --dport 1723 -j ACCEPT

iptables -A FORWARD -i eth0 -j ACCEPT
iptables -A FORWARD -o eth0 -j ACCEPT

iptables -t nat -I POSTROUTING -o eth0 -j MASQUERADE
iptables -I FORWARD -p tcp --tcp-flags SYN,RST SYN -j TCPMSS --clamp-mss-to-pmtu

iptables -A INPUT -j REJECT --reject-with icmp-host-prohibited
iptables -A FORWARD -j REJECT --reject-with icmp-host-prohibited
```

```console
shell> modprobe nf_conntrack_ftp
shell> modprobe nf_conntrack_pptp
shell> modprobe nf_nat_pptp
```

/etc/modules
```
nf_conntrack_ftp
nf_conntrack_pptp
nf_nat_pptp
```

```console
shell> ip6tables -L
shell> ip6tables -L -v
shell> ip6tables -nvL --line-numbers

shell> ip6tables -nvL INPUT --line-numbers

shell> ip6tables -A INPUT -i eth0 -p tcp -s 3ffe:ffff:100::1/128 --dport 22 -j ACCEPT
  
```

netstat-nat

- [](https://access.redhat.com/documentation/en-US/Red_Hat_Enterprise_Linux/4/html/Security_Guide/s1-firewall-ipt-fwd.html)
- [packet-filtering-HOWTO](http://www.netfilter.org/documentation/HOWTO/packet-filtering-HOWTO-5.html)
- [NAT-HOWTO](http://www.netfilter.org/documentation/HOWTO/NAT-HOWTO-4.html)
- [NAT-HOWTO](http://www.netfilter.org/documentation/HOWTO/NAT-HOWTO-6.html)

---
```console
shell> sudo apt-get install iptables-persistent
```

```console
shell> service iptables-persistent save
```


---

```console
shell> sudo apt-get install ipset
shell> ipset help
shell> ipset list
```

```
Name: foo
Type: hash:net
Revision: 6
Header: family inet hashsize 1024 maxelem 65536
Size in memory: 448
References: 0
Members:
192.168.0.0/24
```


```console
shell> ipset create test hash:net family inet hashsize 131072 maxelem 236294
shell> ipset create test hash:net
shell> ipset add test 192.168.0.0/24
shell> ipset add test 10.1.0.0/16
shell> ipset add test 192.168.0/24

shell> ipset test test 192.168.0/24

shell> iptables -A INPUT -m set --match-set foo src -j DROP
shell> iptables -A INPUT -m set --match-set foo src -p tcp --dport 80 -j DROP
```

```console
shell> ipset create test hash:ip timeout 300
shell> ipset add test 192.168.0.1 timeout 60
shell> ipset -exist add test 192.168.0.1 timeout 600
```

```console
shell> ipset create foo hash:mac
shell> ipset add foo 01:02:03:04:05:06
shell> ipset test foo 01:02:03:04:05:06
```

```console
shell> ipset create foo hash:ip,port
shell> ipset add foo 192.168.1.0/24,80-82
shell> ipset add foo 192.168.1.1,udp:53
shell> ipset add foo 192.168.1.1,vrrp:0
shell> ipset test foo 192.168.1.1,80
```

```console
shell> sudo ipset save foo -f /etc/ipset.conf 
shell> sudo ipset save -f /etc/ipset.conf

shell> sudo ipset restore -f /etc/ipset.conf
```

```console
shell> ipset flush foo 
shell> ipset flush
```

```console
shell> ipset destroy foo 
shell> ipset destroy
```

```
ipset v6.29: Timeout cannot be used: set was created without timeout support
ipset v6.29: Set cannot be created: set with the same name already exists
ipset v6.20.1: Set cannot be destroyed: it is in use by a kernel component
```

```console
shell> apt install python-pip
shell> pip install --upgrade pip
shell> pip install iblocklist2ipset

shell> iblocklist2ipset generate --ipset=foo "http://list.iblocklist.com/?list=ydxerpxkpcfqjaybcssw&fileformat=p2p&archiveformat=" > foo.txt
shell> sudo ipset restore -f foo.txt
```

```
http://list.iblocklist.com/?list=ydxerpxkpcfqjaybcssw&fileformat=p2p&archiveformat=gz
```


### :books: 參考網站：
- [ipset](http://ipset.netfilter.org/)
- [ipset](http://ipset.netfilter.org/ipset.man.html)
- [ipset](http://manpages.ubuntu.com/manpages/xenial/man8/ipset.8.html)
- [ChangeLog](http://ipset.netfilter.org/changelog.html)
- [iptables](http://ipset.netfilter.org/iptables.man.html)
- [iptables-extensions](http://ipset.netfilter.org/iptables-extensions.man.html)
- [iblocklist](https://www.iblocklist.com/)

---

**mturoute**
```console
shell> mturoute host
```

 
### :books: 參考網站：
- [mturoute.exe](http://www.elifulkerson.com/projects/downloads/mturoute_2_5/mturoute.exe)

---
```console
shell> apt install iputils-tracepath
shell> tracepath host
```


---

`TSO` (`TCP Segmentation Offload`) **是一种利用网卡分割大数据包，减小 CPU 负荷的一种技术**，也被叫做 `LSO` (`Large segment offload`) ，如果数据包的类型只能是 TCP，则被称之为 TSO，如果硬件支持 TSO 功能的话，也需要同时支持硬件的 TCP 校验计算和分散 - 聚集 (Scatter Gather) 功能。

`GSO` (`Generic Segmentation Offload`)

`TSO` 是使得网络协议栈能够将大块 buffer 推送至网卡，然后网卡执行分片工作，这样减轻了 CPU 的负荷，但 `TSO` 需要硬件来实现分片功能；而性能上的提高，主要是因为延缓分片而减轻了 CPU 的负载，因此，可以考虑将 `TSO` 技术一般化，因为其本质实际是延缓分片，这种技术，在 Linux 中被叫做 `GSO`(`Generic Segmentation Offload`)，它比 `TSO` 更通用，原因在于它不需要硬件的支持分片就可使用，对于支持 TSO 功能的硬件，则先经过 `GSO` 功能，然后使用网卡的硬件分片能力执行分片；而对于不支持 `TSO` 功能的网卡，将分片的执行，放在了将数据推送的网卡的前一刻，也就是在调用驱动的 xmit 函数前。

### :books: 參考網站：
- https://www.ibm.com/developerworks/cn/linux/l-cn-network-pt/

---

![](https://i.imgur.com/qqG1RsI.png)
![](https://i.imgur.com/ijCrsH6.png)
