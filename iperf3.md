最後更新： 2016-11-04 

```console
shell> iperf3 -s
shell> iperf3 -c 192.168.11.2
```

```
Connecting to host 192.168.11.2, port 5201
[  4] local 192.168.11.10 port 52466 connected to 192.168.11.2 port 5201
[ ID] Interval           Transfer     Bandwidth       Retr  Cwnd
[  4]   0.00-1.00   sec  11.3 MBytes  94.6 Mbits/sec    0   39.6 KBytes
[  4]   1.00-2.00   sec  11.2 MBytes  94.3 Mbits/sec    0   43.8 KBytes
[  4]   2.00-3.00   sec  11.2 MBytes  94.0 Mbits/sec    0   43.8 KBytes
[  4]   3.00-4.00   sec  11.2 MBytes  94.3 Mbits/sec    0   43.8 KBytes
[  4]   4.00-5.00   sec  11.2 MBytes  94.1 Mbits/sec    0   43.8 KBytes
[  4]   5.00-6.00   sec  11.3 MBytes  94.5 Mbits/sec    0   69.3 KBytes
[  4]   6.00-7.00   sec  11.2 MBytes  93.9 Mbits/sec    0   69.3 KBytes
[  4]   7.00-8.00   sec  11.2 MBytes  94.3 Mbits/sec    0   69.3 KBytes
[  4]   8.00-9.00   sec  11.2 MBytes  94.2 Mbits/sec    0   69.3 KBytes
[  4]   9.00-10.00  sec  11.2 MBytes  93.9 Mbits/sec    0   69.3 KBytes
- - - - - - - - - - - - - - - - - - - - - - - - -
[ ID] Interval           Transfer     Bandwidth       Retr
[  4]   0.00-10.00  sec   112 MBytes  94.2 Mbits/sec    0             sender
[  4]   0.00-10.00  sec   112 MBytes  94.2 Mbits/sec                  receiver

iperf Done.
```
```console
shell> iperf3 -c 192.168.11.2 -t -i
```

```
-b, --bandwidth n[KM]
```

```console
shell> iperf3 -c iperf.biznetnetworks.com -t -i
shell> iperf3 -c iperf.he.net -t -i -b 1M
```




### :books: 參考網站：

- [iperf-servers](https://iperf.fr/iperf-servers.php)
- [iperf.he.net](http://www.ip-tracker.org/locator/ip-lookup.php?ip=iperf.he.net)
- [iperf.biznetnetworks.com](http://www.ip-tracker.org/locator/ip-lookup.php?ip=iperf.biznetnetworks.com)
