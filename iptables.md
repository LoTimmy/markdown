最後更新： 2016-09-12

---

```console
shell> iptables
```

```console
#Circumvent MTU issues
shell> iptables -t mangle -A FORWARD -p tcp --tcp-flags SYN,RST SYN -j TCPMSS --clamp-mss-to-pmtu

## Masquerade everything out ppp0.
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

```
# Private interface
IF_PRV=eth0
IP_PRV=192.168.1.1
NET_PRV=192.168.1.0/24

# Public interface 1
IF_PUB=eth1
IP_PUB=10.0.0.1
NET_PUB=10.0.0.0/24

# Others
ANYWHERE=0.0.0.0/0
```

[](https://www.novell.com/coolsolutions/feature/18139.html)

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

```console
shell> ipset create test hash:ip 

shell> ipset create foo hash:net
shell> ipset add foo 192.168.0.0/24
shell> ipset add foo 10.1.0.0/16
shell> ipset add foo 192.168.0/24

shell> iptables -A INPUT -m set --match-set foo src -j DROP
shell> iptables -A INPUT -m set --match-set foo src -p tcp --dport 80 -j DROP
```

```console
shell> sudo ipset save foo -f /etc/ipset.conf 
shell> sudo ipset save -f /etc/ipset.conf

shell> sudo ipset restore -f /etc/ipset.conf
```

```console
shell> ipset destroy foo 
shell> ipset destroy
```

```
ipset v6.20.1: Set cannot be destroyed: it is in use by a kernel component
```

```console
shell> pip install iblocklist2ipset
```


### :books: 參考網站：
- [ipset](http://ipset.netfilter.org/)
- [ipset](http://ipset.netfilter.org/ipset.man.html)
- [iptables](http://ipset.netfilter.org/iptables.man.html)
- [iptables-extensions](http://ipset.netfilter.org/iptables-extensions.man.html)

---

**mturoute**
```console
shell> mturoute host
```

 
### :books: 參考網站：
- [mturoute.exe](http://www.elifulkerson.com/projects/downloads/mturoute_2_5/mturoute.exe)

---
```console
shell> aptitude install iputils-tracepath
shell> tracepath host
```

---

![](https://i.imgur.com/qqG1RsI.png)
![](https://i.imgur.com/ijCrsH6.png)
