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

---

```
#!/bin/dash
/bin/sleep 10
/usr/bin/killall iperf3
/bin/sleep 0.1
/usr/bin/killall -9 iperf3
/bin/sleep 0.1
if [ `ps -C iperf3 | wc -l` = "1" ]
then
  /usr/bin/sudo -u nobody /usr/bin/iperf3 -s -p 5200 -D >/dev/null 2>&1
  /usr/bin/sudo -u nobody /usr/bin/iperf3 -s -p 5201 -D >/dev/null 2>&1
  /usr/bin/sudo -u nobody /usr/bin/iperf3 -s -p 5202 -D >/dev/null 2>&1
  /usr/bin/sudo -u nobody /usr/bin/iperf3 -s -p 5203 -D >/dev/null 2>&1
  /usr/bin/sudo -u nobody /usr/bin/iperf3 -s -p 5204 -D >/dev/null 2>&1
  /usr/bin/sudo -u nobody /usr/bin/iperf3 -s -p 5205 -D >/dev/null 2>&1
  /usr/bin/sudo -u nobody /usr/bin/iperf3 -s -p 5206 -D >/dev/null 2>&1
  /usr/bin/sudo -u nobody /usr/bin/iperf3 -s -p 5207 -D >/dev/null 2>&1
  /usr/bin/sudo -u nobody /usr/bin/iperf3 -s -p 5208 -D >/dev/null 2>&1
  /usr/bin/sudo -u nobody /usr/bin/iperf3 -s -p 5209 -D >/dev/null 2>&1
fi
```
```
# Start iPerf3
/sbin/iptables -A INPUT -p udp --dport 5200:5209 -j DROP
/sbin/ip6tables -A INPUT -p udp --dport 5200:5209 -j DROP
/home/scripts/restart_iperf.sh
```
```
# Example of job definition:
# .---------------- minute (0 - 59)
# |  .------------- hour (0 - 23)
# |  |  .---------- day of month (1 - 31)
# |  |  |  .------- month (1 - 12) OR jan,feb,mar,apr ...
# |  |  |  |  .---- day of week (0 - 6) (Sunday=0 or 7) OR sun,mon,tue,wed,thu,fri,sat
# |  |  |  |  |
# *  *  *  *  * user-name  command to be executed
# Restart iPerf3 every hour
  59 *  *  *  * /home/scripts/restart_iperf.sh >/dev/null 2>&1
```



### :books: 參考網站：

- [iperf-servers](https://iperf.fr/iperf-servers.php)
- [iperf.he.net](http://www.ip-tracker.org/locator/ip-lookup.php?ip=iperf.he.net)
- [iperf.biznetnetworks.com](http://www.ip-tracker.org/locator/ip-lookup.php?ip=iperf.biznetnetworks.com)
