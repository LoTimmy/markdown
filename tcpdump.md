
最後更新： 2015-11-04        

---

```console
# 
shell> tcpdump -i eth0 -w tcpdump.out -s 1520 port 80
shell> tcptrace tcpdump.out
shell> tcptrace -l -o1 tcpdump.out
shell> tcptrace -r -l -o1 tcpdump.out

shell> tcpdump -nn -i ethX host ip-addr
shell> tcpdump -nn port 25
shell> tcpdump -nn -X 'port 21' 
```




