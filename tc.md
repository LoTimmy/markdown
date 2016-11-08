上次更新日期： 2016-11-08 

---

```console
shell> tc qdisc del dev eth0 root

# Add +40ms latency
shell> tc qdisc add dev eth0 root netem delay 40ms

shell> tc qdisc add dev eth0 root netem rate 5kbit 20 100 5
```

```console
shell> tc qdisc sh dev eth0
```

```console
shell> modprobe ifb
shell> modprobe sch_htb
shell> ip link show 
shell> ip link set dev ifb0 up
```

```console
shell> tc qdisc del dev eth0 ingress
shell> tc qdisc add dev eth0 ingress
shell> tc filter add dev eth0 parent ffff: protocol ip u32 match u32 0 0 flowid 1:1 action mirred egress redirect dev ifb0
```

```console
shell> tc qdisc del dev eth0 root
shell> tc qdisc add dev eth0 root handle 1: htb default 10
shell> tc class add dev eth0 parent 1: classid 1:1 htb rate 6mbit
shell> tc qdisc add dev eth0 parent 1:1 handle 10: netem delay 100ms

```

```console
shell> tc qdisc del dev ifb0 root
shell> tc qdisc add dev ifb0 root handle 1: htb default 10
shell> tc class add dev ifb0 parent 1: classid 1:1 htb rate 6mbit
shell> tc qdisc add dev ifb0 parent 1:1 handle 10: netem delay 100ms
```

```console
shell> tc qdisc add dev eth0 root netem delay 100ms rate 1mbit
shell> tc qdisc add dev ifb0 root netem delay 100ms rate 1mbit

shell> tc qdisc del dev eth0 root
shell> tc qdisc del dev ifb0 root
shell> tc qdisc add dev eth0 root netem rate 1mbps
shell> tc qdisc add dev ifb0 root netem delay 100ms rate 1mbps
```

---

### :books: 參考網站：
- [tc](http://manpages.ubuntu.com/manpages/trusty/man8/tc.8.html)
- [tc-netem](http://manpages.ubuntu.com/manpages/trusty/man8/tc-netem.8.html)
- [ip](http://manpages.ubuntu.com/manpages/trusty/man8/ip.8.html)
- [Linux 高级流控](http://www.ibm.com/developerworks/cn/linux/1412_xiehy_tc/)
- [在多租戶雲環境中細粒度調整IBM AIX 7.1 和Linux 上的網絡服務質量](http://www.ibm.com/developerworks/cn/aix/library/au-fine-grain-network/)
- [](https://docs.oracle.com/cd/E24628_01/doc.121/e56523/gre.htm#g1013049)
- [Facebook將可模擬各種網路連線狀況的ATC技術貢獻給開放源碼社群](http://www.ithome.com.tw/news/94765)
