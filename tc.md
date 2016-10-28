上次更新日期： 2016-10-26

---

```console
shell> tc qdisc del dev eth0 root
shell> tc qdisc add dev eth0 root netem delay 100ms
shell> tc qdisc add dev eth0 root netem rate 5kbit 20 100 5
```

```console
shell> tc qdisc sh dev eth0
```

```console
shell> modprobe ifb
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
